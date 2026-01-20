# Modelo de grafo

- Grafo referente ao exercício da DIO sobre "Modelagem de Dados em Grafos de um Serviço de Streaming"
- Um modelo de grafo com as seguintes entidades e relacionamentos:</br>
Entidades (nós): User, Movie, Series, Genre, Actor, Director.</br>
Relacionamentos (conexões): WATCHED (com propriedade rating), ACTED_IN, DIRECTED, IN_GENRE.

![Alt text](./graph.png "Optional Title")
<br/>

### Modelo de inserção de dados ao NEO4J
````cypher
CREATE (n22:`Stranger things`)<-[:WATCHED {rating: 4.2}]-(n0:`João`)-[:WATCHED {rating: 5}]->(n1:`Ai - Artificial Inteligence`)<-[:DIRECTED]-(:`Steeven spilberg`),
(:`Haley Joel Osment`)-[:ACTED_IN]->(n1)<-[:ACTED_IN]-(:`Jude Law`),
(:`Brendan Gleeson`)-[:ACTED_IN]->(n1)<-[:WATCHED {rating: 4.9}]-(n28:Pedro)-[:WATCHED {rating: 3}]->(n17:`The Matrix`)<-[:DIRECTED]-(:` Lilly Wachowski`),
(:`Ross Duffer`)-[:DIRECTED]->(n22)<-[:WATCHED {rating: 5}]-(n16:Maria)-[:Watched {rating: 5}]->(n17)<-[:DIRECTED]-(:` Lana Wachowski`),
(:`Carrie-Anne Moss`)-[:ACTED_IN]->(n17)<-[:ACTED_IN]-(:`Laurence Fishburne`),
(:`Keanu Reeves`)-[:ACTED_IN]->(n17)<-[:WATCHED {rating: 3.1}]-(n0)-[:WATCHED {rating: 5}]->(n34:`Hou Of Dragons`),
(:`Finn Wolfhard`)-[:ACTED_IN]->(n22)<-[:ACTED_IN]-(:`Noah Schnapp`),
(:`Millie Bobby Brown`)-[:ACTED_IN]->(n22)<-[:DIRECTED]-(:`Matt Duffer`),
(n34)<-[:WATCHED {rating: 4.2}]-(n28)-[:WATCHED {rating: 5}]->(n29:`Avatar: Fire and Ash`)<-[:DIRECTED]-(:`James Cameron`),
(:`Sam Worthington`)-[:ACTED_IN]->(n29)<-[:ACTED_IN]-(:`Zoë Saldaña`),
(:`Sigourney Weaver`)-[:ACTED_IN]->(n29)<-[:WATCHED {rating: 4.2}]-(n16),
(:`Ryan Condal `)-[:DIRECTED]->(n34)<-[:ACTED_IN]-(:`Matt Smith `),
(:`Emma D'Arcy`)-[:ACTED_IN]->(n34)<-[:ACTED_IN]-(:`Paddy Considine`),
(n0)-[:WATCHED {rating: 5}]->(n29)
````
