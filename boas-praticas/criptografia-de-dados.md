# Criptografia de Dados

Esta boa prática foi implementada no projeto como parte da [PoC 2](../provas-de-conceito/poc-2-autenticacao-e-comunicacao.md). Para mais detalhes sobre uma aplicação dessa prática em um sistema e suas especificações, visite a prova de conceito em questão.

Esta prática concentra-se na utilização de práticas de criptografia de dados por meio do _**BCrypt**_, uma biblioteca _Python_ criada com o objetivo de geração de _hashs_ para senhas.

### Benefícios em Arquitetura de Microsserviços

* **Algoritmo Lento**: Por se tratar de um algoritmo lento de hash para senhas, o BCrypt reduz o número de senhas por segundo que um atacante poderia tentar com um ataque de força bruta;
* **Utilização do Salt por Padrão:** O BCrypt utiliza o valor denominado de _salt_ precedendo o _hash_ de uma senha, permitindo que duas senhas iguais tenham _hashs_ diferentes, e evitando, dessa forma, técnicas como a de _**Rainbow Table**_, determinda por tabelas pré-calculadas de _hashes_.
* **Armazenamento Seguro:** Com dados criptografados e armazenados em um banco de dados, é dificultada a realização bem sucedida de ataques e visualização de seus valores.
* **Múltiplos Pontos de Acesso:** A implementação de um banco de dados para cada microsserviço, com seus dados criptografados com diferentes _hashs_, dificulta as tentativas maliciosas de invasores de obter todos os dados.

Para começar, acesse a documentação do _BCrypt_ e utilize suas funções em seu projeto.
