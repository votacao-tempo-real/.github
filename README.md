# 🗳 Sistema de Votação em Tempo Real

Este é um sistema de votação de enquetes em tempo real, implementado com uma arquitetura orientada a serviços (SOA). O sistema é composto por vários componentes interconectados que proporcionam uma experiência de votação eficiente e em tempo real.

## Componentes

A arquitetura do sistema é composta pelos seguintes componentes:
<br>

### Frontend com WebSocket: 
O frontend do sistema é uma interface de usuário estática e responsiva que utiliza a tecnologia WebSocket para proporcionar uma experiência de votação em tempo real aos usuários. Ele exibe enquetes ativas e permite que os usuários enviem seus votos instantaneamente, sem a necessidade de atualizações manuais da página.
<br><br>

### Middleware com GraphQL:
O middleware atua como uma camada intermediária que gerencia as solicitações e as respostas entre o frontend e os serviços de backend. Ele é construído com GraphQL, facilitando a consulta de dados específicos e a atualização em tempo real das enquetes em exibição.

### Serviço Lambda na AWS
Os serviços de backend são hospedados na Amazon Web Services (AWS) usando o AWS Lambda. Esses serviços fornecem as funcionalidades essenciais do sistema. A escalabilidade automática da AWS Lambda garante que o sistema possa lidar com cargas de tráfego variáveis.
<br><br>

## Diagrama
![Diagrama de componente](https://github.com/votacao-tempo-real/.github/blob/main/profile/assets/diagrama.jpg)
<br><br>

## Mais informações

Para obter acesso aos repositorios de cada serviço mencionado acima, acesse [aqui](https://github.com/votacao-tempo-real/.github/blob/main/profile/README.md)
