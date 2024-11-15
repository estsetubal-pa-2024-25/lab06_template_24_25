# Advanced Programming | Lab6

## Objectives
- Reinforce the understanding and manipulation of the ADT Graph (provided by the `com.brunomnsilva:smartgraph:1.0.0` library, as taught in theoretical classes and explored in Lab 5).
- Implement Dijkstra's algorithm;
- Determine the lowest-cost path between two vertices in a graph.

## 1 - Introduction
Dijkstra's algorithm is used to find the lowest-cost path (or shortest distance) from a given vertex in a graph to all other vertices. This lab aims to implement Dijkstra's algorithm and explore its application in determining the shortest paths in weighted graphs with non-negative weights.

To complete this lab, refer to the natural language algorithm specification shown in **Figure 1** and review the slides available on Moodle related to the TP class about Dijkstra's algorithm.
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
Figure 1

The output of Dijkstra's algorithm consists of:

1. **Minimum cost**: The lowest cost from a source vertex to all other vertices in a graph.
2. **Lowest-cost path**: The set of edges or sequence of vertices that forms the lowest-cost path between the source vertex and any other vertex.

This output can be represented by two structures:

- **Cost Table**: Stores, for each vertex, the lowest cost from the source vertex.
- **Predecessor Table**: Stores, for each vertex, the previous vertex on the lowest-cost path to the source. This table is used to reconstruct the lowest-cost path.

## 2 - Implementation of Dijkstra's Algorithm

Create a class `Dijkstra` that provides a static method to calculate the lowest-cost path between two vertices in a graph.

- The method should take as input:
  - Source vertex
  - The graph
- The method should return as output:
  - An object containing the distance table and the predecessor table.

## 3 - Implementation of the Lowest-Cost Path Calculation

In the `Dijkstra` class, also implement a method to calculate the lowest-cost path between two specific vertices. The method should:

- Take as input:
  - Source vertex
  - Destination vertex
  - The graph
- Return as output:
  - The value of the lowest-cost path.
  - The lowest-cost path between the source and destination vertices, which can be represented as a list of vertices (for the simplest version, which works on graphs without parallel edges).

## 4 - Using the Lowest-Cost Path Calculation Method

- Modify the `FlightView` class to be able to use the method developed in section 3 to calculate the shortest distance between two airports.
- It is suggested to replicate the combo boxes for airport selection to choose the source and destination airports. Add a `TextArea` component to display the result.

## Supplemental Exercise

### Handling Parallel Edges in Dijkstra's Algorithm

When the graph has **parallel edges** and we need to calculate the **lowest-cost path** (including these edges), Dijkstra's method must be modified to also calculate a **predecessor edge table**.

**Objective**: The Dijkstra method must be modified so that the output includes:

1. **Cost Table**: Stores, for each vertex, the lowest cost from the source vertex.
2. **Predecessor Table**: Stores, for each vertex, the previous vertex on the lowest-cost path to the source. This table is used to reconstruct the shortest path.
3. **Predecessor Edge Table**: Stores, for each vertex, the edge previously traversed on the lowest-cost path to the source. This table is used to reconstruct the set of edges that make up the lowest-cost path.

**Expected Result**: The Dijkstra method should return an object containing the three mentioned tables, allowing the reconstruction of both the vertices and edges that make up the lowest-cost path. Test the method again.
(Remove the comments from the instructions to add parallel edges in the `private void createInitialModel()` method).