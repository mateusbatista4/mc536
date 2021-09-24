# Modelo para Apresentação do Lab05 - Marcadores e Taxonomia em Cypher

# Aluno
* `241599`: `Mateus Siqueira Batista`

## Tarefa de Cypher sobre Marcadores e Taxonomia

## Tarefa 1

Escreva em Cypher uma consulta que retorne os marcadores da categoria `Serviços`, sem considerar as categorias subordinadas.

~~~cypher
MATCH (node:Categoria {id:"Serviços"}) <- [:Pertence]-(n)
RETURN n
~~~

## Tarefa 2

Escreva em Cypher uma consulta que retorne os marcadores da categoria `Serviços`, considerando as categorias subordinadas.

~~~cypher
MATCH (m:Marcador)
MATCH (c1:Categoria)
MATCH (c2:Categoria)
WHERE ((m)-[:Pertence]->(c1 {id: "Serviços"})) OR
    ((m)-[:Pertence]->(c1) AND (c1)-[:Superior*1..3]->(c2 {id: "Serviços"}))
RETURN (m)
~~~