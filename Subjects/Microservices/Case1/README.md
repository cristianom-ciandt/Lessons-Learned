# Comunicação entre processos de microserviços - Desafios & Estratégias

## Palavras chave:
* Microserviços
* Comunicação
* Comunicação entre Microserviços

## Autor
* Felipe Salvador

## Case

Uma das principais vantagens que a arquitetura de microserviços trás é o isolamento dos serviços. Uma vez que um Microserviço está enfrentando um problema de sobrecarga, lentidão ou indisponibilidade, nenhum outro Microserviço deveria ser afetado. 

Em um sistema distribuído, devido aos múltiplos processos independentes, os serviços precisam se comunicar. Neste contexto, a comunicação é um aspecto muito importante de uma arquitetura de Microserviços.

No ecossistema de microserviços do Goal, tínhamos um cenário onde alguns microserviços se comunicavam para:  
* Replicar dados(CQRS);
* Compor dados para visualização em reports ou telas do sistema;
* Obter informações para validações;

A estratégia de comunicação inicial adotada, foi via requisições HTTP e na medida que o sistema escalou(quantidade de usuários, quantidade de projetos, operações de sincronização, etc...) passamos a ter as dores e os desafios detalhados na próxima sessão.

## Solução ou Detalhamento da experiência vivenciada

Existem algumas soluções para realizar a comunicação entre os Microserviços:

* **Synchronous protocol:**
Para arquitetura de microserviços, o padrão tem sido protocolo HTTP. O Microserviço X faz um request para o Microserviço Y via HTTP e aguarda a resposta para completar o request. Essa abordagem tem o problema da dependência entre eles.

* **Asynchronous protocol:**
    Protocolo que usa mensagens assíncronas, como o AMPQ. O Microserviço X se comunica com o Microserviço Y via mensageria. Esta abordagem tem o benefício de ser fault tolerant: caso o Microserviço Y esteja enfrentando problemas de lentidão ou até esteja indisponível, assim que tudo voltar ao normal o consumo das mensagens da fila é restabelecido. 
    
    Uma comunicação de mensagem assíncrona pode ser implementada de duas formas:

    * **One-to-one(queue):** 
    Cada mensagem deve ser processada apenas por um serviço.

    * **Publish/Subscribe(topic):** 
    Cada mensagem pode ser processada por zero ou múltiplos serviços.

No Goal, a maior parte da comunicação era síncrona, através de chamadas HTTP, sendo que havia uma pequena parte do sistema que utilizava comunicação assíncrona via AMPQ.
Como era razoavelmente comum acontecer instabilidades temporárias nos serviços, a comunicação síncrona se mostrou um gargalo, expondo a alta dependência existente entre os serviços. O time de arquitetura concluiu que, para resolver o problema, era necessário refatorar o sistema para utilizar somente o modelo de comunicação assíncrona.

## Principais desafios e Dores

Os principais desafios e dores que enfrentamos, foram:

* Quando necessário escalar um microserviço, todos os outros serviços de sua dependência também precisavam ser escalados;
* A cadeia de request causava muitas vezes problemas de performance e lentidão no sistema;
* A requisição falhava quando acontecia um erro ou instabilidade num dos serviços da cadeia. Como não havia implementação de circuit breaker, em alguns casos estas falhas se multiplicavam.

## Contatos importantes que podem compartilhar mais informação ou experiências sobre o tema.

**Cristiano**

**Email**: cristianom@ciandt.com

**Salvador**

**Email**: fsalvador@ciandt.com

**Claudinei**

**Email**: claudineij@ciandt.com

## Referências relevantes para consulta

[Microsoft .Net Guide](https://docs.microsoft.com/en-us/dotnet/standard/microservices-architecture/architect-microservice-container-applications/communication-in-microservice-architecture)