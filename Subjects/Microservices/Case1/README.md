# Comunicação entre processos de microserviços - Desafios & Estratégias

## Palavras chave:
* Microserviços
* Comunicação
* Comunicação entre Microserviços

## Autor
* Felipe Salvador

## Case

Uma das principais vantagens que a arquitetura de microserviços trás é o isolamento dos serviços. Uma vez que um Microserviço está enfrentando um problema de sobrecarga, lentidão ou indisponibilidade, nenhum outro Microserviço deveria ser afetado. 

Para que tenha um isolamento, os serviços precisam se comunicar. Um dos aspectos mais importantes de uma arquitetura de Microserviços é a comunicação entre serviços. 

No ecossistema de microserviços do Goal, tínhamos uma cenário onde  alguns microserviços se comunicavam para:  
* Replicar dados;
* Compor dados para visualização em reports ou telas do sistema;
* Obter informações para validações;

A estratégia de comunicação inicial adotada, foi via requisições HTTP e na medida que o sistema escalou(quantidade de usuários, quantidade de projetos, operações de sincronização, etc...) passamos a ter as dores e os desafios detalhados na próxima sessão.

No Goal não tinhamos esse isolamento de todos os serviços e havia uma sobrecarga muito grande em um serviço especifico. Sempre que esse serviço enfrentava lentidões ou indisponibilidade, todos os outros que dependiam dele, eram afetados.

## Solução ou Detalhamento da experiência vivenciada

Existem algumas soluções para realizar a comunicação entre os Microserviços.

**Synchronous protocol**
Era o que usavamos no Goal, o Microserviço X faz um request para o Microserviço Y via Http e aguarda a resposta para completar o request. Essa abordagem tem o problema da dependencia entre eles.

O recomendado é que se analise bem o uso dessa abordagem e se caso seja a melhor abordagem, não crie uma chain of requests.

**Asynchronous protocol**
Protocolo como AMQP que usa mensagem assincrona. O Microserviço X se comunica com o Microserviço Y via mensageria. Esse abordagem tem o beneficio de caso o Microserviço Y esteja enfrentando problemas de lentidão ou até esteja indisponível, assim que tudo voltar ao normal ele volta a consumir as mensagens da fila.

## Contatos importantes que podem compartilhar mais informação ou experiências sobre o tema.

**Cristiano**

**Email**: cristianom@ciandt.com

**Salvador**

**Email**: fsalvador@ciandt.com

**Claudinei**

**Email**: claudineij@ciandt.com

## Referências relevantes para consulta
