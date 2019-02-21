# Pattners para Comunicação entre Microserviços

## Palavras chave:
* Microserviços
* Comunicação
* Comunicação entre Microserviços

## Autor
* Felipe Salvador

## Case

Um dos aspectos mais importantes de uma arquitetura de Microserviços é a comunicação entre serviços. 

No cenário do Goal os dados de card do Jira eram replicados entre os Microserviços para que cada um pudesse executar sua logica, montar seus dados e prover as informações via API. Tinhamos também o caso em que para atender uma requisição, o Microserviço buscava informações em outros microserviços para compor o resultado.

Uma das principais vantagens que a arquitetura de microserviços trás é o isolamento. Uma vez que um Microserviço está enfrentando um problema de sobrecarga, lentidão ou indisponibilidade, nenhum outro Microserviço deveria ser afetado.

No caso do Goal não tinhamos esse isolamento total e havia uma sobrecarga muito grande em um Microserviço especifico. Toda vez que esse Microserviço enfrentava lentidões ou indisponibilidade, todos os outros eram afetados e o que deveria ser apenas uma parte do sistema, ele como todo enfrentava lentidão.

## Solução ou Detalhamento da experiência vivenciada

Existem algumas soluções para realizar a comunicação entre os Microserviços.

**Synchronous protocol**
Era o que usavamos no Goal, o Microserviço X faz um request para o Microserviço Y via Http e aguarda a resposta para completar o request. Essa abordagem tem o problema da dependencia entre eles.

O recomendado é que se analise bem o uso dessa abordagem e se caso seja a melhor abordagem, não crie uma chain of requests.

**Asynchronous protocol**
Protocolo como AMQP que usa mensagem assincrona. O Microserviço X se comunica com o Microserviço Y via menssageria. Esse abordagem tem o beneficio de caso o Microserviço Y esteja enfrentando problemas de lentidão ou até esteja indisponível, assim que tudo voltar ao normal ele volta a consumir as mensagens da fila.

## Contatos importantes que podem compartilhar mais informação ou experiências sobre o tema.

**Cristiano**

**Email**: cristianom@ciandt.com

**Salvador**

**Email**: fsalvador@ciandt.com

**Claudinei**

**Email**: claudineij@ciandt.com
