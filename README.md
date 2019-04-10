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




Once the application is generated, you can launch it using Maven (./mvnw on Linux/MacOS/Windows PowerShell, mvnw on Windows Cmd) or Gradle (./gradlew on Linux/MacOS/Windows PowerShell, gradlew on Windows Cmd).

The application will be available on http://localhost:8080

Important if you want to have “live reload” of your JavaScript/TypeScript code, you will need run npm start or yarn start. You can go to the Using JHipster in development page for more information.

