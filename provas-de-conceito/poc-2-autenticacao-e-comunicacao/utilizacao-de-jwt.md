---
icon: user-vneck
---

# Utilização de JWT

Na versão inicial, a aplicação não implementava mecanismos de autenticação e au-\
torização nos endpoints. Com isso, qualquer requisição contendo os parâmetros cor-\
retos era processada, independentemente da identidade ou das permissões do solici-\
tante. Além disso, não havia validação ou restrição de acesso baseada em políticas\
de autorização, o que expunha os serviços a potenciais acessos indevidos.

Para adotar mecanismos de autenticação e autorização, que são conceitos funda-\
mentais quando se trata de Segurança, foram utilizados mecanismos como JWT e\
OAuth2.&#x20;

A imagem a seguir representa o fluxo realizado para autenticação e autorização nos serviços da aplicação, onde o serviço de usuário é o responsável pela autenticação e geração de token de acesso, enquanto os outros serviços, ao receberem o token, apenas validam a role e verificar se o token foi assinado pelo sistema, utilizando de uma mesma secret:&#x20;

<figure><img src="../../.gitbook/assets/image (6).png" alt="" width="563"><figcaption></figcaption></figure>



Para a criação da secret foi executado o seguinte comando:

```
openssl rand -hex 32
```

Essa chave, juntamente com o tempo de expiração da chave e o algoritmo de cripto-\
grafia utilizado, foram armazenados nas variáveis de ambiente de todos os serviços\
da aplicação. Essa chave atua como uma chave privada, em que a aplicação assina\
os tokens que estão sendo criados. Sendo assim, é utilizada para encriptar e des-\
criptar os tokens JWT.

O serviço tcc-customer ficou como o responsável por realizar a autenticação do\
usuário no sistema e geração do token.

Endpoiont de login para o sistema:&#x20;

{% code title="app/api/router/customer.py" %}
```python
@router.post("/login/", response_model = Token)
async def login_for_access_token(
    session: SessionDep,
    form_data: Annotated[OAuth2PasswordRequestForm, Depends()],
) -> Token:
    
    user = auth.authenticate_user(session, form_data)
    access_token_expires = timedelta(days=settings.ACCESS_TOKEN_EXPIRE_DAYS)

    access_token = auth.create_access_token(
        data={"sub": str(user.id), "name": user.name, "role": user.role}, 
        expires_delta=access_token_expires
    )
    
    return Token(access_token=access_token, token_type="bearer")
        
```
{% endcode %}

Adicionalmente, foram criadas funções para geração do token de acesso e autenticação de usuário, que valida se o hash da senha informada condiz com o hash da senha armazenada. Caso não, o usuário recebe resposta de usuário não autorizado, com credenciais incorretas. Caso sim, o token de acesso é gerado para o usuário.&#x20;

Seguem funções:&#x20;

{% code title="app/auth.py" lineNumbers="true" %}
```python
def create_access_token(data: dict, expires_delta: timedelta | None = None):
    to_encode = data.copy()
    if expires_delta:
        expire = datetime.now(timezone.utc) + expires_delta
    else:
        expire = datetime.now(timezone.utc) + timedelta(minutes=15)
    to_encode.update({"exp": expire})
    encoded_jwt = jwt.encode(to_encode, settings.SECRET_KEY, algorithm=settings.ALGORITHM)
    return encoded_jwt
            
def authenticate_user(session: Session, login_request: LoginRequest): 
    customer = customer_service.get_customer_by_email(session, login_request.username)
    if not customer: 
        raise UserNotFoundException
    stored_password_hash = customer.password
    provided_password_hash = login_request.password
        
    if (not stored_password_hash) or not check_password(stored_password_hash, provided_password_hash): 
        raise InvalidPasswordException
    return customer
```
{% endcode %}
