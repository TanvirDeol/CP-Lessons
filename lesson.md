#**Breadth First Search vs Depth First Search**

**Prerequisites: Recursion, Queues, Graph Representation**

**Introduction**

 ![](RackMultipart20200422-4-hytfpc_html_610487326e0daad3.png) Breadth-first (BFS) search and depth-first search (DFS) are two different ways a graph can be traversed. In the context of computer science, a graph is a representation of a network of nodes, as shown below.

Both approaches can start from any node and branch out to its adjacent nodes, and soon enough, the entire graph is searched.

**Motivation**

To use an example, lets assume the graph above represents restaurants 1,2,3...6 and the lines between them (known as edges) are roads that connect these restaurants. You are at restaurant **1** and you want to know if there is a path you can take to reach restaurant **6**. In a problem like this, you would use either BFS or DFS to find out if there is a valid path.

**Depth First Search**

Depth-first search is an approach where the program recursively visits all the neighbors (adjacent nodes) of a node and stops once it reaches a node with no neighbors. Below is a table of each node and its adjacent neighbors:

| Node | Neighbors |
| --- | --- |
| **1** | 2 5 |
| --- | --- |
| **2** | 1 3 5 |
| **3** | 2 4 |
| **4** | 3 5 6 |
| **5** | 1 2 4 |
| **6** | 4 |

A table like this is known as an adjacency list in computer science

and it can be constructed using 2D arrays or vectors

Using this data, a depth-first search can be simulated, making sure nodes are only visited once:

- Start at node 1 and visit its first neighbor, node 2.
- From node 2, skip node 1 as its visited and continue to node 3.
- From node 3, go to node 4.
- From node 4, go to node 5.
- Once the function points to node 5, there are no unvisited neighbors, so the function call will return nothing, and node 4 will continue to search.
- The program will come back to node 4, and visit its last neighbor, node 6. Search complete.
-

Given any graph, DFS is guaranteed to eventually visit all nodes and output the correct answer. However, note that it takes 4 iterations to go from node 1 to 5; yet node 5 lies right next to node 1. A more calculated approach would find this in one iteration.

**Breadth-First Search**

Breadth-First search, commonly known as BFS, searches the graph level-by-level. Think of the graph above as a social circle; a representation of node 1&#39;s mutual friends/connections. Node 2 and 5 are **directly related** of node 1; while the rest of the nodes are **indirectly related** to node 1 through another node.

| Node | # of connections away from node 1. |
| --- | --- |
| **1** | 0 |
| --- | --- |
| **2** | 1 |
| **3** | 2 |
| **4** | 2 |
| **5** | 1 |
| **6** | 3 |

Think of the number of connections away from

node 1 as **levels** , BFS searches level-by-level.

A level-by-level search is implemented with a **queue** ; remember that the first element inserted in a queue is the first element to come out (FIFO: First In, First Out). Let&#39;s run a search to find node 6 again:

- Start at node 1 and insert its neighbors, node 2 and 5 in the queue. [2 , 5]
- Pop node 2 from the queue and insert its unvisited neighbors behind 5. [5 , 3]
- Pop node 5 and insert its neighbor, node 4 behind node 3. [3 , 4]
- Pop node 3, and skip the inserting since all its neighbors are visited [4]
- Pop node 4 and you have found node 6. Search complete. []

**Conclusions**

As shown, DFS and BFS both take around 5 iterations to find node 6, however BFS only takes one iteration to find node 5 unlike DFS which took 4. These excess iterations translate to wasted computing time in real life situations. Three extra iterations barely puts a load on modern computers, capable of billions of calculations in an instant; but in competitive programming data sets that exceed the millions, an optimization like this can make the difference between an AC and a Time Limit Exceeded solution.
