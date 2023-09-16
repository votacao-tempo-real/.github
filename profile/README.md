# 🗳 Sistema de Votação em Tempo Real

📚 Trabalho prático da Pós-Graduação em Arquitetura de Software Distribuído da PUC Minas, da matéria Arquitetura de Backend mestrada pelo professor, Lucas Porto.
Este é um sistema de votação de enquetes em tempo real, implementado com uma arquitetura orientada a serviços (SOA). O sistema é composto por vários componentes interconectados que proporcionam uma experiência de votação eficiente e em tempo real.


## Integrantes:

- Luiz Gabriel Santos Fernandes
- Raife Ferreira Paiva
- Renan Carlos Silva Braz Tafner

## Introdução

## 🎯 Objetivos 

- Objetivo Geral: Criar um aplicação de votação de enquetes em tempo real.
- Objetivo Específico: Fornecer um exemplo de implementação utilizando comunicação em 3 camadas de tecnologias diferentes (AWS Lambda, GraphQL e WebSockets).

## 🗃 Repositórios principais

### [GraphQL (Middleware)](https://github.com/RenanTafner/Trabalho5ArquiteturaBackend-MiddlewareGraphQL)
#### Resposável por orquestrar operações no banco de dados usando GraphQL.

O middleware atua como uma camada intermediária que gerencia as solicitações e as respostas entre o frontend e os serviços de backend. Ele é construído com GraphQL, facilitando a consulta de dados específicos e a atualização em tempo real das enquetes em exibição.

#### 📋 Tecnologias utilizadas:
- [Javascript](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript)
- [Apollo Server](https://www.apollographql.com/)
- [GraphQL](https://graphql.org/)

### [AWS Lambda (Backend)](https://github.com/RenanTafner/Trabalho5ArquiteturaBackend-BackendAWSLambdaServerless)
#### Responsável por processar as solicitações do [GraphQL (Middleware)](https://github.com/RenanTafner/Trabalho5ArquiteturaBackend-MiddlewareGraphQL) e deter a lógica de negócios vinculadas a diferentes endpoints.

Os serviços de backend são hospedados na Amazon Web Services (AWS) usando o AWS Lambda. Esses serviços fornecem as funcionalidades essenciais do sistema. A escalabilidade automática da AWS Lambda garante que o sistema possa lidar com cargas de tráfego variáveis.

#### 📋 Tecnologias utilizadas:
- [Javascript](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript)
- [Express](https://expressjs.com/pt-br/)
- [Serverless](https://www.serverless.com/)
- [API DynamoDB](https://docs.aws.amazon.com/pt_br/sdk-for-javascript/v2/developer-guide/dynamodb-examples.html)


### [Websockets (Frontend)](https://github.com/RenanTafner/Trabalho5ArquiteturaBackend-FrontendWebSockets)
#### Responsável pela interface visual e lógica para utilização do Middleware usando WebSockets.

O frontend do sistema é uma interface de usuário estática e responsiva que utiliza a tecnologia WebSocket para proporcionar uma experiência de votação em tempo real aos usuários. Ele exibe enquetes ativas e permite que os usuários enviem seus votos instantaneamente, sem a necessidade de atualizações manuais da página.

#### 📋 Tecnologias utilizadas:
- [Javascript](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript)
- [Express](https://expressjs.com/pt-br/)
- [Socket.IO](https://socket.io/)

## Diagrama

![Diagrama de componente](https://github.com/votacao-tempo-real/.github/blob/main/profile/assets/diagrama.jpg)

## Boas práticas

### 🔐 Segurança

Esse tópico é uma preocupação fundamental para garantir a integridade e a confidencialidade dos dados no sistema de votação em tempo real proposto. Algumas práticas e tecnologias relevantes que pensamos em adicionar caso o sistema fosse implementado:


- Autenticação e Autorização: Implementar um sistema de autenticação robusto para garantir que apenas usuários autorizados possam votar. Além disso, estabelecer regras de autorização para controlar o acesso a recursos e funcionalidades específicos. Poderiam ser utilizados sistemas de autenticação como JWT e OAuth 2.0 vinculados. Alguns serviços de documentação como o [Swagger](https://2knh0oc42g.execute-api.us-east-1.amazonaws.com/api-docs/), devem ser privados com sistema de login e boas práticas de segurança.

- Proteção contra Injeção de SQL: Utilizar consultas parametrizadas para evitar ataques de injeção de SQL no banco de dados e também utilizar níveis de autorização no banco de dados.

- Criptografia: Proteger dados sensíveis, como senhas, utilizando técnicas de criptografia adequadas.

- Monitoramento de Segurança: Implementar ferramentas de monitoramento de segurança para identificar e responder a atividades suspeitas ou tentativas de violação.

### 🧗‍♂️ Escalabilidade

A escalabilidade é crucial para garantir que o sistema possa lidar com aumentos de tráfego e carga de trabalho caso seja implementado.

O ponto principal do tópico escalabilidade, é entender escalabilidade vertical e horizontal: Projetar componentes que possam ser escalados verticalmente (aumento de recursos em um servidor) e horizontalmente (adicionar mais servidores) para lidar com diferentes tipos de carga. Alguns pontos levantados foram:

- Arquitetura Serverless: O uso de serviços Serverless, já é uma boa prática ao pensar em escalabilidade, pois permite que o sistema se adapte automaticamente ao tráfego, escalando horizontalmente conforme necessário.

- Balanceamento de Carga: Implementar um balanceamento de carga eficiente para distribuir as solicitações entre os serviços backend e evitar sobrecarga em um único servidor. Aqui poderiamos por exemplo utilizar um [PM2](https://pm2.keymetrics.io/) para subir o nosso middleware, ou também até utilizar um sistema de conteiners como o [Kubernets](https://kubernetes.io/pt-br/). Para o Frontend, entendemos que uma máquina bem calculada seria o suficiente, utilizar Kubernets para essa parte seria um gasto desnecessário.

- Cache nas consultas do banco: Utilizar caches para armazenar resultados de consultas frequentes e reduzir a carga de processamento no banco de dados. 

### 📊 Monitoramento

O monitoramento é essencial para acompanhar o desempenho do sistema e identificar problemas em tempo real. Algumas práticas de monitoramento incluem:

- Logs e Rastreamento: Gerar logs detalhados de todas as operações e implementar rastreamento para seguir o fluxo das solicitações através dos componentes. O AWS Lambda já tem um serviço de logging, os outros componentes necesstariam de um serviço externo ou o do próprio ambiente que fosse implementado.

- Métricas e Alertas: Definir métricas-chave de desempenho e configurar alertas para notificar a equipe de operações sobre eventos críticos ou quedas de desempenho.

- Monitoramento de Infraestrutura: Monitorar o status dos servidores, recursos da nuvem e a integridade dos serviços em tempo real.

- Análise de Desempenho: Utilizar ferramentas de análise de desempenho para identificar gargalos e otimizar o sistema.

### 👨‍💻 Escrita de código

A escrita de código de alta qualidade é essencial para manter o sistema eficiente e fácil de manter.

- Padrões de Codificação: Adotar padrões de codificação consistentes para garantir que o código seja legível e compreensível por toda a equipe.

- Testes Automatizados: Escrever testes automatizados abrangentes para garantir que as alterações no código não quebrem funcionalidades existentes.

- Teste Unitário: Implementar testes unitários para verificar a funcionalidade de unidades individuais de código, garantindo que cada parte do sistema funcione conforme o esperado.

- Revisões de Código: Realizar revisões de código regularmente para identificar e corrigir problemas de código, bem como para promover boas práticas.

- Documentação: Manter documentação atualizada, incluindo comentários no código e documentação de API para facilitar o entendimento e uso do sistema.

- Refatoração: Identificar áreas do código que podem ser melhoradas e aplicar refatorações para reduzir a complexidade e melhorar a legibilidade.

### 📚 Padrões Arquiteturais

Utilizar um padrão do tipo Clean Architecture influenciaria em vários aspectos do desenvolvimento, incluindo segurança, escalabilidade, monitoramento, escrita de código e testes unitários. Claro que precisamos ter bastante cuidado ao escolher um padrão arquitetural, visto a complexidade de manutenção em certos casos, mas é importante levantar que a escolha de padrões arquiteturais são de extrema valia para os tópicos acima.
