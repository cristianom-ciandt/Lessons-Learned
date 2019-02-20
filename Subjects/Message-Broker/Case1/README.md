# Resolvendo problemas de concorrência em filas de mensagens

## Palavras chave
* Concorrência
* Concurrency
* Condição de corrida
* Race condition
* Mensageria
* Messaging
* Fila
* Queue
* Message broker

## Autor
Claudinei Oliveira

## Case
Nos sistemas do Goal, alguns objetos são processados através de filas de mensagens.

No início não houve problemas, uma vez que as regras de negócio começaram simples e havia somente um consumidor por fila.

Com o tempo, o processamento de cada objeto ficou maior, tanto em relação ao tempo quanto à quantidade de regras envolvidas.
Aliado a isso, o aumento do uso do Goal gerou a necessidade de escalar os consumidores das filas.

Algum tempo depois, identificamos que certos problemas de processamento foram causados pela concorrência entre os consumidores das filas.

Após estudar o problema, concluímos que a solução seria utilizar *partitioned channels*, um recurso implementado pela maioria dos message brokers, embora em cada implementação tenha um nome diferente (no ActiveMQ, por exemplo, o termo utilizado é *message group*).

Um *partitioned channel* funciona da seguinte maneira: ao produzir uma mensagem, especifica-se uma *partition key*. O message broker utiliza esta chave para destinar esta mensagem para um único consumidor. Desta forma, mensagens da mesma *partition* são processadas pelo mesmo consumidor e na ordem correta. O message broker também se encarrega de gerenciar e reatribuir os consumidores se, por exemplo, alguma instância cair ou uma nova subir.

## Principais desafios e dores
No Goal, a primeira tentativa falhou. Utilizamos uma *partition key* que, pela forma como nossas mensagens eram produzidas, deixava sempre um consumidor ocupado e os demais ociosos. Conseguimos resolver o problema da concorrência, porém deixamos de usufruir dos benefícios que ela traz. Então, revimos nosso plano de *partitions* e sucedemos na segunda tentativa.

Outro detalhe importante foi entender como o message broker realiza o *tracking* das *partitions* e lida com o consumo de memória.  No caso do ActiveMQ, esta estratégia pode ser definida por configuração: é possível, por exemplo, criar e gerenciar um número ilimitado de *partitions*, porém sem limitar o consumo de memória; por outro lado, pode-se manter o consumo de memória sob controle ao definir um número máximo de *partitions* gerenciadas, sendo que as *partitions* utilizadas há mais tempo deixam de ser gerenciadas para dar lugar às mais recentes, funcionando de forma semelhante a um cache.

Em resumo, foram 2 pontos importantes:
1. Definir a *partition key* mais apropriada.
2. Entender a relação entre *partitions* x consumo de memória específica do message broker utilizado.

## Contatos importantes podem compartilhar mais informações
**Cristiano**<br/>
cristianom@ciandt.com

**Salvador**<br/>
fsalvador@ciandt.com

**Claudinei**<br/>
claudineij@ciandt.com