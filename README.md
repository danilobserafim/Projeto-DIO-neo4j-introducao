# Modelo de grafo

- Grafo referente ao exercício da DIO sobre "Modelagem de Dados em Grafos de um Serviço de Streaming"
- Um modelo de grafo com as seguintes entidades e relacionamentos:</br>
Entidades (nós): User, Movie, Series, Genre, Actor, Director.</br>
Relacionamentos (conexões): WATCHED (com propriedade rating), ACTED_IN, DIRECTED, IN_GENRE.

![Alt text](./graph.png "Optional Title")
<br/>

### Modelo de inserção de dados ao NEO4J
````cypher
CREATE (`Stranger things`:Serie)<-[:WATCHED {rating: 4.2}]-(`João`:User)-[:WATCHED {rating: 5}]->(`Ai - Artificial Inteligence`:Movie)<-[:DIRECTED]-(:Director),
(:Actor)-[:ACTED_IN]->(`Ai - Artificial Inteligence`)<-[:ACTED_IN]-(:Actor),
(:Actor)-[:ACTED_IN]->(`Ai - Artificial Inteligence`)<-[:WATCHED {rating: 4.9}]-(Pedro:User)-[:WATCHED {rating: 3}]->(`The Matrix`:Movie)<-[:DIRECTED]-(:Director),
(:Director)-[:DIRECTED]->(`Stranger things`)<-[:WATCHED {rating: 5}]-(Maria:User)-[:Watched {rating: 5}]->(`The Matrix`)<-[:DIRECTED]-(:Director),
(:Actor)-[:ACTED_IN]->(`The Matrix`)<-[:ACTED_IN]-(:Actor),
(:Actor)-[:ACTED_IN]->(`The Matrix`)<-[:WATCHED {rating: 3.1}]-(`João`)-[:WATCHED {rating: 5}]->(`House Of Dragons`:Serie),
(:Actor)-[:ACTED_IN]->(`Stranger things`)<-[:ACTED_IN]-(:Actor),
(:Actor)-[:ACTED_IN]->(`Stranger things`)<-[:DIRECTED]-(:Director),
(`House Of Dragons`)<-[:WATCHED {rating: 4.2}]-(Pedro)-[:WATCHED {rating: 5}]->(`Avatar: Fire and Ash`:Movie)<-[:DIRECTED]-(:Director),
(:Actor)-[:ACTED_IN]->(`Avatar: Fire and Ash`)<-[:ACTED_IN]-(:Actor),
(:Actor)-[:ACTED_IN]->(`Avatar: Fire and Ash`)<-[:WATCHED {rating: 4.2}]-(Maria),
(:Director)-[:DIRECTED]->(`House Of Dragons`)<-[:ACTED_IN]-(:Actor),
(:Actor)-[:ACTED_IN]->(`House Of Dragons`)<-[:ACTED_IN]-(:Actor),
(`João`)-[:WATCHED {rating: 5}]->(`Avatar: Fire and Ash`)
````
