# Criptografia de Dados

Esta boa prática foi implementada no projeto como parte da [PoC 2](../provas-de-conceito/poc-2-autenticacao-e-comunicacao.md). Para mais detalhes sobre uma aplicação dessa prática em um sistema, visite a prova de conceito em questão.

Esta prática concentra-se na utilização de práticas de criptografia de dados por meio do BCrypt, uma biblioteca Python criada com o objetivo de geração de hashs para senhas.

### Benefícios em Arquitetura de Microsserviços

* **Algoritmo Lento**: Por se tratar de um algoritmo lento de hash para senhas, o BCrypt reduz o número de senhas por segundo que um atacante poderia tentar com um ataque de força bruta;
* **Utilização do Salt por padrão:** O BCrypt utiliza o valor denominado de salt precedendo o hash de uma senha, permitindo que duas senhas iguais tenham hashs diferentes, e evitando, dessa forma, a técnica de Rainbow Table, determinda por tabelas pré-calculadas de hashes.
* **Armazenamento seguro:** Com dados criptografados e armazenados em um banco de dados, é dificultada a realização de ataques e visualização de seus valores.
* **Múltiplos Pontos de Acesso:** A implementação de um banco de dados para cada microsserviço, com seus dados criptografados com diferentes hashs, dificulta as tentativas maliciosas de invasores.

Para começar, acesse a documentação do BCrypt e utilize suas funções em seu projeto.
