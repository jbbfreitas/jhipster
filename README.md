# JHipster - Gerando Código para o Backend e para o FrontEnd

JHipster é uma plataforma de desenvolvimento para gerar, desenvolver e fazer o  deploy de aplicações Web usando `Spring Boot` + `Angular/React`.  Pode-se usá-la também para criar microserviços Spring . 


## Iniciando com o JHipster

1. Crie uma pasta em `Grupo de Estudo/jhipster`. Essa pasta será utilizada para criar a nossa aplicação:

2. Vá para a pasta recém criada :

```java
cd jhipster/
```

3. Gere a sua primeira aplicação, simplesmente digitando:

```java
jhipster
```

4. Diversas questões deverão ser respondidas para criar a nossa aplicação. Vamos a elas então:

:one:-```Qual o tipo de aplicação você deseja criar```


::: :pushpin: Importante :::

> Os tipos de aplicações possíveis são as seguintes:

  - Monolithic application (recommended for simple projects) 
  - Microservice application 
  - Microservice gateway 
  - JHipster UAA server (for microservice OAuth2 authentication) 


> A primeira opção cria aplicações monolíticas, ou seja, sem utilização de microserviços. As demais são relacionadas para microserviços.  A opção  que será utilizada neste projeto é a primeira.


> Para saber um pouco mais sobre microserviço acesse https://www.jhipster.tech/microservices-architecture/

:two:-` Qual o nome base para a sua aplicação? (jhipster)` 

::: :pushpin: Importante :::

> o nome base será utilizado como sufixo do pacote principal. Vamos informar `ec`

:three:-` Qual o pacote java? (br.com.abim)` 

::: :pushpin: Importante :::

> Vamos informar `br.com.abim`

:four:-`Qual o pacote java? (br.com.abim)` 

::: :pushpin: Importante :::

> Vamos informar `br.com.abim`

:five:-Qual o tipo de autenticação você gostaria de usar?

::: :pushpin: Importante :::

> Os tipos de autenticações disponíveis são as seguintes:

- JWT authentication (stateless, with a token) 
- OAuth 2.0 / OIDC Authentication (stateful, works with Keycloak and Okta) 
- HTTP Session Authentication (stateful, default Spring Security mechanism) 

Vamos explicar cada uma delas

**Autenticação de Sessão HTTP** 

Este é o mecanismo de autenticação "clássico" do Spring Security, que foi melhorado pela equipe do JHipster. Ele usa a Sessão HTTP, portanto, é um mecanismo com estado: se você planeja dimensionar seu aplicativo em vários servidores, é necessário ter um balanceador de carga com sessões fixas para que cada usuário permaneça no mesmo servidor. E esse, ao meu ver é o grande incoveniente.

**Autenticação do OAuth2**

OAuth2 é um mecanismo de segurança sem estado, portanto, você pode preferir se quiser escalonar seu aplicativo em várias máquinas. O Spring Security fornece uma implementação do OAuth2, que é configurado pelo jhipster para você.

O maior problema com o OAuth2 é que ele requer várias tabelas de banco de dados para armazenar seus tokens de segurança. 

Essa solução usa uma chave secreta, que deve ser configurada no arquivo application.yml, como a propriedade "authentication.oauth.secret".

**Autenticação JWT**

A autenticação JSON Web Token (JWT), assim como o OAuth2, é um mecanismo de segurança sem estado, portanto, é outra boa opção se você quiser escalonar vários servidores diferentes.

Esse mecanismo de autenticação não existe por padrão com o Spring Security, é uma integração específica do JHipster do projeto Java JWT. É mais fácil de usar e implementar do que o OAuth2, já que não requer um mecanismo de persistência, portanto funciona em todas as opções SQL e NoSQL.

Essa solução usa um token seguro que contém o nome de login e as autoridades do usuário. Como o token é assinado, ele não pode ser alterado por um usuário.

A chave secreta deve ser configurada no arquivo application.yml, como a propriedade jhipster.security.authentication.jwt.secret.


> Iremos usar JWT-Java Web Token. Para mais informações sobre JWT acesse esse link: https://medium.com/tableless/entendendo-tokens-jwt-json-web-token-413c6d1397f6

> Para saber um pouco mais sobre OAuth 2.0 acesse este link: https://imasters.com.br/desenvolvimento/como-funciona-o-protocolo-oauth-2-0

:six:-Que tipo de banco de dados gostaria de usar?

::: :pushpin: Importante :::

> Os tipos de banco disponíveis são os seguintes:

- SQL (H2, MySQL, MariaDB, PostgreSQL, Oracle, MSSQL) 
-  MongoDB 
-  Couchbase 
-  Cassandra


O **MongoDB** e **Couchbase** armazenam dados em documentos flexíveis semelhantes a JSON, o que significa que os campos podem variar de documento para documento e a estrutura de dados pode ser alterada ao longo do tempo. **MongoDB** é um software livre, enquanto que  **Couchbase** necessita de uma subscrição. Ambos fazem parte de um conjunto de banco de dados denominados `NoSQL`. O termo NoSQL surgiu para diferenciar os novos banco de dados dos tradicionais bancos relacionais dos novos modelos de armazenamento. Essa sigla significa “not only SQL”. Como pode-se perceber a idéia não é substituir os bancos relacionais mas adicionar outras formas de armazenamento.

O **CassandraDB** foi criado originalmente pelo Facebook, sua arquitetura foi inspirada pelo DynamoDB da Amazon e seu modelo de dados foi baseado no BigTable do Google — como open source desde 2008. Atualmente ele é mantido pela fundação Apache.
O Cassandra é altamente escalável e sua arquitetura foi projetada para ser o mais resiliente possível. É extremamente eficiente para escrita e leitura desde que esteja bem modelado: os dados precisam estar desnormalizados! 

> Para este estudo de caso, iremos usar um banco SQL.

:seven:-Que banco de dados deseja usar em ambiente de produção?

::: :pushpin: Importante :::

> Os tipos de banco disponíveis são os seguintes:

-  MySQL 
-  MariaDB 
-  PostgreSQL 
-  Oracle  
-  Microsoft SQL Server 

> Para este estudo de caso, iremos usar o banco PostgreSQL.

:eight:-Que banco de dados deseja usar em ambiente de desenvolvimenyo?

::: :pushpin: Importante :::

> Os tipos de banco disponíveis são os seguintes:

-  H2 with disk-based persistence 
-  H2 with in-memory persistence 
-  PostgreSQL 

> Para este estudo de caso, iremos usar o banco PostgreSQL.


:nine:-Você quer usar a abstração do cache Spring? 

::: :pushpin: Importante :::

> As opções disponíveis são as seguintes:

- Sim, com a implementação do Ehcache (cache local, para um único nó)
- Sim, com a implementação do Hazelcast (cache distribuído, para vários nós)
- [BETA] Sim, com a implementação do Infinispan (cache híbrido, para vários nós)
- Sim, com Memcached (cache distribuído) - Aviso, ao usar um banco de dados SQL, isso desabilitará
       e Hibernate cache de segundo nível!
- Não - Atenção, ao usar um banco de dados SQL, isso desabilitará o cache do segundo nível do Hibernate!

> Para este estudo de caso, iremos usar a primeira opção.

:ten:- Você deseja usar o cahce de segundo nível do hibernate? (Y/n)

> Para este estudo de caso, iremos usar `Y`.

:one::one:-Voce deseja usar o `Maven` ou `Gradle` para a construção do *backend*?

> Para este estudo de caso, iremos usar `Maven`.


:one::two:-Quais outras tecnologias você gostaria de usar?

- ◯ Mecanismo de pesquisa usando o Elasticsearch

- ◯ WebSockets usando Spring Websocket

- ◯ Mensagens assíncronas usando o Apache Kafka

- ◯ API first usando o gerador OpenAPI

O modelo de documento é mapeado para os objetos no código do aplicativo, facilitando o trabalho com os dados


Once the application is generated, you can launch it using Maven (./mvnw on Linux/MacOS/Windows PowerShell, mvnw on Windows Cmd) or Gradle (./gradlew on Linux/MacOS/Windows PowerShell, gradlew on Windows Cmd).

The application will be available on http://localhost:8080

Important if you want to have “live reload” of your JavaScript/TypeScript code, you will need run npm start or yarn start. You can go to the Using JHipster in development page for more information.

