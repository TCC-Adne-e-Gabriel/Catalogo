---
icon: arrow-right-arrow-left
---

# ORM e validação de dados de entrada e saída

Na fase inicial do desenvolvimento do sistema, os serviços de Back-End foram implementados sem validações explícitas dos dados de entrada e saída, utilizando consultas SQL escritas manualmente.&#x20;

Essa abordagem permitiu agilidade na prototipação da lógica principal porém apresentou limitações em termos de segurança e manutenção, incluindo riscos como injeção de SQL e maior acoplamento entre regras de negócio e acesso ao banco de dados.&#x20;

Exemplo de endpoint com Query SQL usando de concatenação de query SQL  a partir do informações do request:&#x20;

```python
@router.post("/", status_code=201)
async def create_customer(body: Request, conn=Depends(get_db_conn)) -> Any:
    body = await body.json()
    cursor = conn.cursor()
    customer_id = uuid4()
    date_now = datetime.now()
    query = (
        "INSERT INTO CUSTOMER (id, name, email, password, phone, created_at, updated_at) VALUES ('"
        + str(customer_id) + "', '"
        + body["name"] + "', '"
        + body["email"] + "', '"
        + encrypt_data(body["password"]) + "', '"
        + body["phone"] + "', '"
        + date_now + "', '"
        + date_now + "')"
    )
    cursor.execute(query)
    conn.commit()
    cursor.close()
    body["id"] = customer_id
    body["updated_at"] = date_now
    body["created_at"] = date_now
    return body
```

Esse trecho é vulnerável à SQL Injection porque ele concatena diretamente a variável ID na query SQL como string, o que permite que um atacante injete comandos maliciosos no banco de dados

A boa prática em questão tem como objetivo deixar o sistema mais robusto e minimizar as potenciais brechas de segurança no sistema, como SQL Injection, Command\
Injection e Cross-Site-Scripting. Para isso, os autores optaram pela utilização da biblioteca Pydantic do Python para validação de dados e SQLAlchemy, um ORM.&#x20;

Endpoint após aplicação da prática:&#x20;

{% code title="app/api/router/customer.py" %}
```python
@router.post("/", response_model=CustomerResponse, status_code=201)
def create_customer(
    session: SessionDep, 
    customer: CustomerRequest
): 
    customer_email = customer_service.get_customer_by_email(session=session, email=customer.email)
    if(customer_email): 
        raise HTTPException(
            status_code=400, 
            detail="User with this email already exists"
        )
    customer = customer_service.create_customer(session=session, customer=customer)
    return customer


```
{% endcode %}



Para isso, caminho app/schemas/customer.py, define o tipo de\
dado que será recebido no corpo da requisição. A classe criada herda da\
classe BaseModel, fornecida pelo Pydantic, que serve como base para a criação de\
modelos de dados com validação automática e tipagem explícita.

{% code title="app/schemas/customer.py" %}
```python
class CustomerRequest(BaseModel):
    name: str
    email: str
    password: str
    phone: str
```
{% endcode %}

Também foi criado um arquivo na pasta de services, repsonsável por empacotar a regra de negócio para criação de usuário:&#x20;

{% code title="app/services/customer.py" %}
```python
class CustomerService():
    def create_customer(self, session: Session, customer: CustomerRequest) -> CustomerResponse:
        customer.password = encrypt_data(customer.password)
        customer_data = customer.model_dump()
        db_customer = Customer(**customer_data)
        session.add(db_customer)
        session.commit()
        session.refresh(db_customer)
        return db_customer
```
{% endcode %}

Todos os serviços do lado do servidor desenvolvidos seguiram a mesma base estru-\
tural, utilizando o Pydantic para a definição e a validação dos dados de entrada\
e saída, e o SQLModel (que utiliza SQLAlchemy como base) como ferramenta de\
mapeamento objeto-relacional (ORM) para interação com o banco de dados. Essa\
padronização contribuiu para a consistência, a reutilização de código, e a facilidade\
na manutenção da aplicação como um todo.
