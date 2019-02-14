# Reduzindo o leadtime da construção de experimentos

## Palavras chave:
* Startup
* Experimentos
* Feature Toggle
* Processo de desenvolvimento
* Leadtime
* Velocidade

## Autor
* Cristiano Manoel

## Case

No contexto do projeto do Goal operávamos no formato de startup, utilizando o famoso ciclo: **build, measure & learn** definido pelo *Eric Ries*.

Num determinado momento do nosso projeto, identificamos que o processo de desenvolvimento tradicional de projetos de software não estava entregando para nós a agilidade que precisávamos para rodar experimentos de forma rápida, medir resultados e gerar aprendizados para tomar decisão de persistir ou pivotar o desenvolvimento de uma determinada feature.

Neste contexto, ficamos incomodados e provocados para estudar e buscar uma estratégia que trouxesse a agilidade necessária para uma startup conseguir gerar aprendizados rápidos e investir recursos(*tempo, dinheiro, talentos, etc...*) somente no que realmente fosse um problema ou job to be done dos nossos clientes.

## Solução ou Detalhamento da experiência vivenciada

Então, após bastante estudo e reflexões, decidimos modificar nosso processo de desenvolvimento de experimentos da seguinte maneira:

**1. Modificação de mind set:**

A principal mudança de mind set, consistiu-se em ***não buscar a perfeição no primeiro momento***, pois, se tratando de experimentos, nos não tinhamos a certeza que iriam ter sucesso ou falha, com isto, decidimos fazer um mínimo possível.

**2.  Linha rápida:**

O mínimo mencionado no item anterior, foi definido da seguinte maneira:
* Menor quantidade de código possível;
* Menor número de teste automatizado possível para entregar;
* Flexibilização do nosso quality gate de código;
* Utilização de fake features, apenas para coletar feedback e metricas via analytics
* Utilização do Google Optimize para segmentação de audiências.

**3.  Audiência específicas:**

Em alguns casos adotamos a estratégia de liberar features somente para  audiência de early adopters, por meio de mecanismo de feature toggle. Estes usuários já tinham ciência que estavam recebendo features que não eram versão final, desta forma, fizemos a gestão de expectativa dos mesmos para evitar frustação e para conseguir motivar eles a darem feedbacks.

**4.  Linha de refinamento:**

Uma vez que nossos experimentos comprovavam sucesso, o código entrava em uma linha de lapidação e refinamento, onde:

* A refatoração acontecia visando qualidade e mantenabilidade de código;
* Em alguns casos faziamos até rescrita completa;
* Nesta etapa, faziamos também, a cobertura de código com testes automatizados, visando agora garantir a conformidade de requisitos e a confiabilidade da suite de testes;
* Refinamentos de design também eram aplicados caso fosse necessário.

Desta forma, uma vez que a uma feature passasse por todos refinamentos necessários, ela passava a incorporar o produto final e era liberada para todos usuários.

## Principais desafios e Dores

Os principais desafios e dores que enfrentamos, foram:

* Quebrar o paradigma de entregar inicialmente, tudo com qualidade total.
* Conseguir entender que essa flexibilização e desburocratização do nosso processo de desenvolvimento era necessário para alcançar a velocidade que precisávamos. 
* No primeiro momento, pensou se que estávamos abrindo a mão da qualidade. Mas na verdade não, nós estávamos apenas deixando para aplicar qualidade no total somente ao que iríamos incorporar no produto final e com isto economizamos tempo e dinheiro.
* Entender o que era o mínimo do ponto de vista de desenvolvimento, pois, sempre tinha aquele desejo de deixar o melhor possível ou já adiantar algo para a fase de refinamento.

## Resultados obtidos

Após a implantação deste novo processo de desenvolvimento, nosso leadtime de experimentos foi otimizado de maneira expressiva, diminuindo de 30 para 5 dias úteis.

## Contatos importantes que podem compartilhar mais informação ou experiências sobre o tema.

**Cristiano**

**Email**: cristianom@ciandt.com
**Fone:**

**Salvador**

**Email**: fsalvador@ciandt.com
**Fone:**

## Referências relevantes para consulta

