# Modelo de grafo

- Grafo referente ao exercício da DIO sobre "Modelagem de Dados em Grafos de um Serviço de Streaming"
- Um modelo de grafo com as seguintes entidades e relacionamentos:</br>Entidades (nós): User, Movie, Series, Genre, Actor, Director.</br>Relacionamentos (conexões): WATCHED (com propriedade rating), ACTED_IN, DIRECTED, IN_GENRE.

```cypher
CREATE (:User {name: "João"});
CREATE (:User {name: "Marina"});

CREATE (:Movie {title: "Inception"});
CREATE (:Movie {title: "The Matrix"});

CREATE (:Series {title: "Breaking Bad"});
CREATE (:Series {title: "Dark"});

CREATE (:Genre {name: "Sci-Fi"});
CREATE (:Genre {name: "Thriller"});
CREATE (:Genre {name: "Crime"});
CREATE (:Genre {name: "Drama"});

CREATE (:Actor {name: "Leonardo DiCaprio"});
CREATE (:Actor {name: "Keanu Reeves"});
CREATE (:Actor {name: "Bryan Cranston"});
CREATE (:Actor {name: "Louis Hofmann"});

CREATE (:Director {name: "Christopher Nolan"});
CREATE (:Director {name: "Wachowskis"});
CREATE (:Director {name: "Vince Gilligan"});
CREATE (:Director {name: "Baran Odar"});

MATCH (u:User {name: "João"}), (m:Movie {title: "Inception"}) CREATE (u)-[:WATCHED {rating: 5}]->(m);
MATCH (u:User {name: "João"}), (m:Movie {title: "The Matrix"}) CREATE (u)-[:WATCHED {rating: 4}]->(m);

MATCH (u:User {name: "João"}), (s:Series {title: "Breaking Bad"}) CREATE (u)-[:WATCHED {rating: 5}]->(s);

MATCH (u:User {name: "Marina"}), (s:Series {title: "Dark"}) CREATE (u)-[:WATCHED {rating: 5}]->(s);
MATCH (u:User {name: "Marina"}), (m:Movie {title: "Inception"}) CREATE (u)-[:WATCHED {rating: 4}]->(m);

MATCH (a:Actor {name: "Leonardo DiCaprio"}), (m:Movie {title: "Inception"}) CREATE (a)-[:ACTED_IN]->(m);
MATCH (a:Actor {name: "Keanu Reeves"}), (m:Movie {title: "The Matrix"}) CREATE (a)-[:ACTED_IN]->(m);

MATCH (a:Actor {name: "Bryan Cranston"}), (s:Series {title: "Breaking Bad"}) CREATE (a)-[:ACTED_IN]->(s);
MATCH (a:Actor {name: "Louis Hofmann"}), (s:Series {title: "Dark"}) CREATE (a)-[:ACTED_IN]->(s);

MATCH (d:Director {name: "Christopher Nolan"}), (m:Movie {title: "Inception"}) CREATE (d)-[:DIRECTED]->(m);
MATCH (d:Director {name: "Wachowskis"}), (m:Movie {title: "The Matrix"}) CREATE (d)-[:DIRECTED]->(m);

MATCH (d:Director {name: "Vince Gilligan"}), (s:Series {title: "Breaking Bad"}) CREATE (d)-[:DIRECTED]->(s);
MATCH (d:Director {name: "Baran Odar"}), (s:Series {title: "Dark"}) CREATE (d)-[:DIRECTED]->(s);

MATCH (m:Movie {title: "Inception"}), (g:Genre {name: "Sci-Fi"}) CREATE (m)-[:IN_GENRE]->(g);
MATCH (m:Movie {title: "Inception"}), (g:Genre {name: "Thriller"}) CREATE (m)-[:IN_GENRE]->(g);

MATCH (m:Movie {title: "The Matrix"}), (g:Genre {name: "Sci-Fi"}) CREATE (m)-[:IN_GENRE]->(g);

MATCH (s:Series {title: "Breaking Bad"}), (g:Genre {name: "Crime"}) CREATE (s)-[:IN_GENRE]->(g);
MATCH (s:Series {title: "Breaking Bad"}), (g:Genre {name: "Drama"}) CREATE (s)-[:IN_GENRE]->(g);

MATCH (s:Series {title: "Dark"}), (g:Genre {name: "Sci-Fi"}) CREATE (s)-[:IN_GENRE]->(g);
MATCH (s:Series {title: "Dark"}), (g:Genre {name: "Thriller"}) CREATE (s)-[:IN_GENRE]->(g);
```
