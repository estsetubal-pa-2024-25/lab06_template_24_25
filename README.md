# Programação Avançada | Lab6

:gb: [English version](README_EN.md)

## Objectivos 
- Reforçar a compreensão e manipulação da TAD (ADT) Graph (Edisponibilizado pela biblioteca `com.brunomnsilva:smartgraph:1.0.0`, como lecionado nas aulas teóricas e explorado no Laboratório 5).
- Implementar o algoritmo de Dijkstra;
- Determinar o caminho de menor custo entre dois vértices de um grafo.

## 1 -Introdução
O algoritmo de Dijkstra é utilizado para encontrar o caminho de menor custo (ou distância mínima) a partir de um dado vértice de um grafo até todos os outros vértices. Este laboratório tem como objetivo implementar o algoritmo de Dijkstra e explorar a sua aplicação na determinação de caminhos mínimos em grafos ponderados com pesos não negativos.

Para realizar este laboratório, consulte a especificação do algoritmo em linguagem natural apresentada na **Figura 1** e revise os slides disponibilizados no Moodle referentes à aula TP sobre o algoritmo de Dijkstra.
```console
function Dijkstra(Graph, Source):
    create an empty set of unvisited vertices
    for each vertex V in the Graph:
        assign infinite cost to V        
        assign null predecessor to V
        add V to the set of unvisited vertices
    assign cost 0 to the Source vertex
    while there are unvisited vertices:
        select the unvisited vertex V with the smallest current cost
        mark V as visited (remove from the set)
        for each neighbor W of V:
            if the current cost of [V + weight of edge (V, W)] is less 
                                   than the current cost of W:
                update the cost of W
                set V as the predecessor of W
    return the result (costs and predecessors)
```
Figura 1



O output do algoritmo de Dijkstra consiste em:

1. **Distância mínima**: A menor distância a partir de um vértice de origem para todos os outros vértices de um grafo.
2. **Caminho mais curto**: O conjunto de arestas ou sequência de vértices que forma o caminho mais curto entre o vértice de origem e qualquer outro vértice.

Este output pode ser representado por duas estruturas:

- **Tabela de Distâncias**: Armazena, para cada vértice, a menor distância desde o vértice de origem.
- **Tabela de Predecessores**: Armazena, para cada vértice, o vértice anterior no caminho mais curto até à origem. Esta tabela é utilizada para reconstruir o caminho mais curto.





## 2 - Implementação do Algoritmo de Dijkstra.

Crie uma classe `Dijkstra` que disponibiliza um método estático para calcular o caminho de menor custo entre dois vértices de um grafo.

- O método deve receber como input:
  - Vértice de origem
  - O grafo
- O método deve retornar como output:
  - Um objeto contendo a tabela de distâncias e a tabela de predecessores.


## 3 - Implementação do Calculo do Caminho Mais Curto

Na classe `Dijkstra`, implemente também um método para calcular o caminho mais curto entre dois vértices específicos. O método deve:

- Receber como input:
  - Vértice de origem
  - Vértice de destino
  - O grafo
- Retornar como output:
	- O valor do caminho de menor custo.
  	- O caminho de menor custo entre o vértice de origem e o vértice de destino, que pode ser representado por uma lista de vértices (para a versão mais simples, que funciona em grafos sem arestas paralelas);
  
## Utilização do método de calculo do caminho mais curto.

- Utilize a classe DijkstraProgram e o grafo disponibilizado para testar o método implementado em 2, entre os seguintes pontos:
- Origem A - Destino F
- Origem D - Destino A

# Exercícios Complementares

- ### a) Calculo do caminho de menor custo vs caminho mais curto.

  No seu projeto, existe um tipo enumerado `TypeOfCost` que permite identificar dois tipos de custos:

  - `LEAST_COST_PATH`: Caminho de menor custo;
  - `SHORTEST_PATH`: Caminho mais curto (ou seja, o caminho com o menor número de arestas).

  A classe `Weight` já está preparada para que o método `getCost` retorne:

  - O valor do custo da aresta (variável) para calcular o **caminho de menor custo**;
  - Um valor constante, caso seja necessário calcular o **caminho mais curto**.

  **Tarefa**: Altere a classe `Dijkstra` para incluir um parâmetro adicional no método que calcula o caminho de menor custo. Este parâmetro será o `costType`, e, em função deste, o método deverá calcular:

  - O caminho de menor custo (`LEAST_COST_PATH`);
  - Ou o caminho mais curto, considerando o menor número de arestas (`SHORTEST_PATH`).

  ### b) Criação de Testes Unitários

  Crie os testes unitários para verificar o correto funcionamento do método alterado na alínea anterior. Os testes devem cobrir:

  - Cálculo do **caminho de menor custo** (usando `LEAST_COST_PATH`);
  - Cálculo do **caminho mais curto** (usando `SHORTEST_PATH`);
  - Testes com diferentes tipos de grafos, incluindo grafos com arestas paralelas e múltiplos pesos.

  ### c) Manipulação de Arestas Paralelas no Algoritmo de Dijkstra

  Quando o grafo possui **arestas paralelas**, e precisamos calcular o **caminho de menor custo** (incluindo essas arestas), o método de Dijkstra deverá ser modificado para também calcular uma **tabela de arestas predecessoras**.

  **Objetivo**: O método de Dijkstra deve ser alterado para que o output inclua:

  1. **Tabela de Distâncias**: Armazena, para cada vértice, a menor distância desde o vértice de origem.
  2. **Tabela de Predecessores**: Armazena, para cada vértice, o vértice anterior no caminho mais curto até à origem. Esta tabela é usada para reconstruir o caminho mais curto.
  3. **Tabela de Arestas Predecessoras**: Armazena, para cada vértice, a aresta percorrida anteriormente no caminho mais curto até à origem. Esta tabela é usada para reconstruir o conjunto de arestas que compõem o caminho mais curto.

  **Resultado esperado**: O método Dijkstra deverá retornar um objeto que contenha as três tabelas mencionadas acima, permitindo a reconstrução tanto dos vértices quanto das arestas que compõem o caminho mais curto ou de menor custo.

