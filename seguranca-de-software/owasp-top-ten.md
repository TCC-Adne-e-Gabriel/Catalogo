# OWASP Top Ten

A OWASP (sigla em inglês para _Open Web Application Security Project_, ou Projeto Aberto de Segurança em Aplicações _Web_), é uma organização sem fins lucrativos que visa disseminar e promover boas práticas de segurança no desenvolvimento _web_, oferecendo gratuitamente diversas ferramentas, documentos e pesquisas relacionadas à segurança de software.

A comunidade OWASP publica diversos estudos e pesquisas sobre segurança, sendo reconhecida por produzir a lista "_OWASP Top Ten_" (originalmente _The Ten Most Critical Web Application Security Vulnerabilities_) (OWASP, 2021).

Publicado inicialmente em 2003, o _OWASP Top Ten_ apresenta as dez vulnerabilidades e ameaças mais críticas que poderiam ser encontradas na etapa de desenvolvimento _Web_, e essencialmente aborda as vulnerabilidades mais frequentemente exploradas por agentes mal-intencionados que possam realizar a tentativa de invasão ou alteração de _software_. Além de descrever como essas vulnerabilidades funcionam, a OWASP também oferece orientações para suas mitigação, ajudando desenvolvedores a adotar devidas práticas que reduzam os riscos associados.

A lista OWASP Top 10 de 2021 (OWASP, 2021), apresenta as seguintes vulnerabilidades:



1. #### Quebra de Controle de Acesso (A01:2021 – _Broken Access Control_)

Políticas de controle de acesso devem garantir que um usuário não pode agir fora do que está dentro de suas permissões. Violações na política de acesso podem permitir a modificação, visualização ou destruição de dados ou acesso de funcionalidades de negócio indesejadas (OWASP, 2021).&#x20;Segundo OWASP (2021), dentre as vulnerabilidades de controle de acesso que podem ser exploradas, é comum a violação do princípio do menor privilégio.



2. **Falhas de Criptografia (A02:2021 –&#x20;**_**Cryptographic Failures**_**)**

As vulnerabilidades de falhas de criptografia auxiliam em como determinar as proteções necessárias para dados sensíveis ao serem trafegados ou simplesmente armazenados no sistema. Esses dados podem envolver número de cartão, senhas, informações pessoais, sendo a privacidade e a segurança desses dados, normalmente, prevista por lei e regulações. Nesse sentido, é de fundamental importância o cuidado e preocupação com esses dados (OWASP, 2021)



3. **Injeção (A03:2021 –&#x20;**_**Injection**_**)**

Segundo OWASP (2021), normalmente, as aplicações estão sujeitas aos ataques desse tipo, quando não validam os dados fornecidos pelos usuários; existem consultas dinâmicas e chamadas não parametrizadas, e dados são usados diretamente ou concatenados. Dentre recomendações para prevenir esse tipo de vulnerabilidade, é importante enfatizar a definição de limites em comandos SQL para evitar comandos em massa; utilização de validação de entrada pelo lado do servidor; utilização de ferramentas de mapeamento relacional de dados, dentre outros.



4. **Design Inseguro (A04:2021 –&#x20;**_**Insecure Design**_**)**

Já um _design_ inseguro não pode ser corrigido por uma implementação de código perfeita, pois o sistema foi construído sem os controles de segurança necessários. Um dos fatores para a construção de um _design_ inseguro compreende a própria falha em determinar o nível de _design_ de segurança que é\
necessário para a aplicação em si (OWASP, 2021).



5. **Configuração Incorreta de Segurança (A05:2021 –&#x20;**_**Security Misconfiguration**_**)**

Segundo Myf5 (2022), vulnerabilidades de falha de configuração são fragilidades que podem existir em componentes de _software_ e subsistemas ou em administração de usuários. A OWASP menciona que 90% das aplicações são testadas para alguma forma de erro de configuração, com média de incidente de 4%.



6. **Componentes Vulneráveis e Ultrapassados (A06:2021 –&#x20;**_**Vulnerable and Outdated Components**_**)**

Esse tipo de vulnerabilidade acontece quando um componente não é&#x20;suportado, está ultrapassado, ou ainda vulnerável, representando uma ameaça para a aplicação (MYF5, 2022).



7. **Falhas de Identificação e Autenticação (A07:2021 –&#x20;**_**Identification and Authentication Failures**_**)**

Segundo OWASP (2021), autenticação, gerenciamento de sessão e confirmação da identidade de usuário são pontos críticos para proteção contra ataques relacionados à autenticação. Podem ser consideradas vulnerabilidades de autenticação quando se permite usar senhas padrão, senhas fracas ou muito conhecidas, ou quando não se tem autenticação multi-fatores de forma efetiva, ou ainda quando não se invalida tokens de sessão, dentre outros.



8. **Falhas de Integridade de Dados e de Software (A08:2021 –&#x20;**_**Software and Data Integrity Failures**_**)**

Relacionada com atualização de software, dados críticos e/ou _pipelines_ de _CI/CD_ sem verificar a integridade (OWASP, 2021).



9. **Falhas de Registro e Monitoramento de Segurança (A09:2021 –&#x20;**_**Security Logging and Monitoring Failures**_**)**

Essa categoria existe para auxiliar na detecção, escalada e resposta às falhas de segurança. Registros e monitoramento podem ser difíceis de testar, normalmente dependendo da detecção de ataques durante testes de penetração. Entretanto, é muito impactante para visibilidade, alerta de incidentes de segurança, e análises e rastreabilidade dos incidentes (OWASP, 2021).



10. #### Falsificação de Request do Lado do Servidor (A10:2021 – _Server-Side Request Forgery (SSRF)_)

Vulnerabilidades dessa categoria acontecem quando uma aplicação _Web_ está requisitando um recurso remoto do lado do servidor sem validar a _URL_ fornecida pelo usuário. Nesse cenário, é possível que o atacante mande uma requisição criada para um destino não esperado (OWASP, 2021).&#x20;

### Referências

OWASP. OWASP Top 10: 2021. 2021. Acessado em: 07 jan. 2025.

MYF5. Security misconfiguration (A5) | Secure against the OWASP Top 10 for 2021. 2022. Acessado em: 07 jan. 2025. Disponível em: \<https://my.f5.com/manage/s/article/ K49812250>
