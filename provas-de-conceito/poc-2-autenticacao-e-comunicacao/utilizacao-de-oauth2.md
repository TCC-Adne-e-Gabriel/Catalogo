---
icon: person-circle-question
---

# Utilização de OAuth2

O OAuth2 foi implementado para autorização utilizando apenas access tokens no\
formato JWT. Cada token é gerado com um tempo de expiração curto, e os clientes\
precisam reautenticar quando ele expira. Como não foram utilizados refresh tokens,\
evitou-se a complexidade extra de gerenciamento e armazenamento seguro desses\
tokens, mantendo o fluxo mais simples e adequado ao caso de uso.

Para acesso dos endpoints da aplicação, o usuário deve passar o token de acesso\
por meio de um Bearer Token, que é o tipo predominante de acesso no protocolo\
OAuth2 (OAUTH2.O, 2025).

{% code title="app/auth.py" overflow="wrap" lineNumbers="true" %}
```python
    oauth2_scheme = OAuth2PasswordBearer(tokenUrl="token")
    settings = Settings()
            
    async def get_current_customer_data(token: str = Depends(oauth2_scheme)) -> TokenData:
        try:
            payload = jwt.decode(token, settings.SECRET_KEY, algorithms=[settings.ALGORITHM])
            customer_id = payload.get("sub")
            role = payload.get("role")
            if customer_id is None:
                raise InvalidTokenError
            if role is None: 
                raise InvalidTokenError
            token_data = TokenData(id=customer_id, role=role)
        except InvalidTokenError:
            raise InvalidPasswordException
        return token_data
        
    def role_required(roles: List[str]): async def checker(decoded_token: TokenData = Depends(get_current_customer_data)):
            if not decoded_token.role in roles:
                raise UnauthorizedException
            return decoded_token
        return checker
```
{% endcode %}

Para limitação de acesso para determinados roles, foi adicionado o seguinte trecho de código nos endpoints:&#x20;

`dependencies=[Depends(auth.role_required(["admin"]))`

{% code title="app/api/router/customer.py" %}
```python
@router.delete("/{id}/", dependencies=[Depends(auth.role_required(["admin"]))])
def delete_user(
    session: SessionDep, 
    id: UUID
) -> Message:
    address_service.delete_addresses(session, id)
    customer_service.delete_customer(session, id)
    return Message(message="User deleted successfully")
```
{% endcode %}

Obs.: As funções de decodificar token e verificar se usuário tem a role desejada foram aplicadas em todos os serviços, de forma que todos passaram a implementar os mecanismos de autorização. Caso o usuário não possua a role desejada, uma exceção de usuário não autorizado é lançada.&#x20;

### Referências

OAUTH2.O. OAuth 2.0 Bearer Token Usage. 2025. Disponível em: \<https:\
//oauth.net/2/bearer-tokens/>
