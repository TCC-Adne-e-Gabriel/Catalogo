---
icon: hashtag
---

# Utilização de práticas de Criptografia

Para utilização de um serviço de criptografia segura, os autores optaram por utilizar\
a biblioteca Bcrypt. Segundo Arias (2021), o BCrypt foi desenvolvido por Niels\
Provos e David Mazières (1999) com o propósito de gerar hashs para senhas. Trata-\
se de um algoritmo lento, o que é bom, pois reduz o número de senhas por segundo\
que um atacante pode tentar em um ataque de força bruta.

A alteração visou aumentar a segurança dos\
dados sensíveis, além de seguir as boas práticas atuais de segurança da informação.

```python
import bcrypt

def encrypt_data(password): 
    encoded_password = password.encode('utf-8')
    salt = bcrypt.gensalt()
    return bcrypt.hashpw(encoded_password, salt).decode('utf-8')

def check_password(hash, input_password): 
    user_bytes = input_password.encode('utf-8')
    hash_bytes = hash.encode('utf-8')
    return bcrypt.checkpw(user_bytes, hash_bytes)
```
