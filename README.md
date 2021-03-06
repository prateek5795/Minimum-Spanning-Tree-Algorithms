# Minimum-Spanning-Tree-Algorithms

Implementation of Data Structures and Algorithms  
Fall 2018  
Long Project LP3: Minimum Spanning Tree Algorithms

Authors - Team LP101
- Prateek Sarna (pxs180012@utdallas.edu)
- Rahul Nalwade (rsn170330@utdallas.edu) (https://github.com/rahul1947)
- Bhavish Khanna Narayanan (bxn170002@utdallas.edu) (https://github.com/bhavish14)

Files Included
- BinaryHeap.java
- MST.java

BinaryHeap.java
  - Implemented BinaryHeap and its nested class IndexedHeap.

MST.java
  - Implemented the three versions of Prim's algorithm discussed in class, and Kruskal's algorithm. 
  
Observations
- In BinaryHeap - add(x), and remove() throws exception when they 
   encounter full and empty queue conditions respectively. But, offer(x), 
   and poll() silently returns false for the above conditions. 
   
- In BinaryHeap - we could have used resize() as we try to add an element 
   to fully occupied queue. But, as we are dealing with fixed graph, the 
   resize() is never being called.
   
- In MST Algorithms - the early exit optimization is applied but, when 
   tested it appears that Prim3 doesn't need such optimization. 
   Note that this optimization only helps in saving computations after you 
   add the last (n-1)th edge to the MST. 

- For Prim's Algorithm - Take 2:
   We may not need to use the constructor MSTVertex(MSTVertex u).
   As we could store the original vertex information for each MSTVertex,
   we can make copies of new MSTVertices out of the original Vertex, 
   instead of it's MSTVertex copy.
   For e.g. if we have Vertex v, we can use -
   MSTVertex vCopy = new MSTVertex(v) instead of
   MSTVertex vCopy = new MSTVertex(get(v)).

   These copies are used to store different distance and parent values 
   whereas, get(v) has the information about 'seen'ness of all MSTVertices 
   made out of v. 
   
- For Prim2 and Prim3, we are storing the information about the edge 
   which reaches out to this MSTVertex. It is used to form mst<Edge>.
  

RESULTS

Prim's Algorithm - Take 1
 
| File                    | Output   |  Time(mSec)  | Memory (used/avail)|  
|:-----------------------:|:--------:|:------------:|:------------------:|  
| mst-5-6-19.txt          | 19       | 2            | 1 MB / 117 MB      |  
| mst-50-140-84950.txt    | 84950    | 4            | 1 MB / 117 MB      |  
| mst-10k-30k-1085305.txt | 1085305  | 28           | 9 MB / 147 MB      |  
 ------------------------------------------------------------------------


Prim's Algorithm - Take 2

| File                    | Output   |  Time(mSec)  | Memory (used/avail)|  
|:-----------------------:|:--------:|:------------:|:------------------:|  
| mst-5-6-19.txt          | 19       | 2            | 1 MB / 117 MB      |  
| mst-50-140-84950.txt    | 84950    | 3            | 1 MB / 117 MB      |  
| mst-10k-30k-1085305.txt | 1085305  | 32           | 11 MB / 147 MB     |  
 ------------------------------------------------------------------------


Prim's Algorithm - Take 3
 
| File                    | Output   |  Time(mSec)  | Memory (used/avail)|  
|:-----------------------:|:--------:|:------------:|:------------------:|  
| mst-5-6-19.txt          | 19       | 3            | 1 MB / 117 MB      |
| mst-50-140-84950.txt    | 84950    | 3            | 1 MB / 117 MB      |
| mst-10k-30k-1085305.txt | 1085305  | 34           | 12 MB / 147 MB     |
 ------------------------------------------------------------------------


Kruskal's Algorithm
 
| File                    | Output   |  Time(mSec)  | Memory (used/avail)|   
|:-----------------------:|:--------:|:------------:|:------------------:|  
| mst-5-6-19.txt          | 19       | 2            | 1 MB / 117 MB      |  
| mst-50-140-84950.txt    | 84950    | 2            | 1 MB / 117 MB      |  
| mst-10k-30k-1085305.txt | 1085305  | 42           | 14 MB / 147 MB     |  
 ------------------------------------------------------------------------

NOTE: 
- Time and Memory might change, as you run the test the program on a 
  different system, but they could be comparable to the above values.
