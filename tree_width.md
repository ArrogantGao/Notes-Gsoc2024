# Tree-width Algorithms for Simple Graphs

In this note, I will introduce various algorithms for computing the tree-width of simple graphs, including the Boudhitté and Todinca dynamic programming algorithm for tree width[^Bouchitté] and the Tamaki2022 algorithm for exact tree width[^Tamaki].

## Introduction to Concepts

In this section, I will introduce the basic concepts and definitions to be used in the following introduction to the algorithms.

### Tree Decomposition and Tree Width

The tree decomposition of a graph is a tree whose nodes are subsets of the vertices of the graph, and the following conditions are satisfied:
1. Each vertex of the graph is in at least one node of the tree.
2. For each edge of the graph, there is a node of the tree containing both vertices of the edge.
3. Bags containing the same vertex have to be connected in the tree.

An example is shown in the following figure, where the tree width is two.

<p align="center">
  <img src="figs/Tree_decomposition.svg.png" style="width:50%" />
</p>

For a given tree decomposition, the width of the tree decomposition is defined as the maximum size of the bags minus one, and tree width of graph $G$, $tw(G)$, is defined as the minimum width of all possible tree decompositions of $G$.

### Chordal Graphs

Chordal graph of a graph $G$ is a graph in which every cycle of length four or more has a chord, which is an edge that is not part of the cycle but connects two vertices of the cycle. An example of the chordal graph is shown below. It should be noted that the chordal is not complete, and the chordal graph of a graph is not necessarily unique.

<p align="center">
  <img src="figs/chordal.png" style="width:50%" />
</p>

With chordal graph, we can further define the minimum triangulation of graphs: Given a simple graph $G$ and a chordal graph $H$, if $V(G) = V(H)$ and $E(G) \subseteq E(H)$, then we call $H$ is a triangulation of $G$. If no proper subset of $H$ is a triangulation of $G$, we call $H$ a minimum triangulation of $G$. An example is shown below.

<p align="center">
  <img src="figs/triangulation.png" style="width:80%" />
</p>

### Potential Maximum Clique and Minimum Separator

The potential maximum cliques and the minimum separators are two important concepts in the tree-width algorithms, since all tree bags are potential maximum cliques and intersections of tree bags are minimum separators.

Maximum clique is a subset of vertices in a graph such that every two distinct vertices in the clique are adjacent, i.e., the clique is complete and cannot be extended by adding another vertex. For a given graph $G$, a potential maximum clique is a subset of vertices that is a maximum clique in one of its minimum triangulation $H$. Generally, a potential maximum clique is labeled as $\Omega$, and the set of all potential maximum cliques is denoted as $\Pi_k(G)$, where $k$ for the maximum size of the clique. If all tree bags of a tree decomposition is in $\Pi_k(G)$, we call the tree decomposition a $k$-tree decomposition and admitted by $\Pi_k(G)$.

For a given connected graph $G$, the $a-b$ separator $S$ is a set of vertices such that the removal of $S$ from $G$ disconnects the vertices $a$ and $b$, and for a minimum separator, no proper subset of $S$ is a separator. All minimum separators are intersections of connected potential maximum cliques. For a given graph $G$ and a set of vertices $K$, $\Delta_G(K)$ represents all separators of $G$ in $K$.

After the removal of $S$, the graph $G$ is divided into a few connected components denoted as $\mathcal{C}_G(S)$. For $C \in \mathcal{C}_G(S)$, we call $(S, C)$ a block associated with $S$. If all vertices in $S$ are adjacent vertices in $C$, we call $(S, C)$ a full block, otherwise, we call it a non-full block. $R(S, C) = G_S[S \cup C]$ represents the relazation of $G$ the block $(S, C)$, where $G_S$ for adding an edge between every pair of nonadjacent vertices of $S$.

## The Algorithms

In this section, I will introduce the algorithms to search the tree-width of a simple graph. Generally speaking, the BT algorithm aims to search the best tree decomposition on a given $\Pi_K(G)$ in $O(|\Pi_K(G)| + |\Delta(G)| + 1)$ times. Thus, I will start with the algorithm to search all possible potential maximum cliques and minimum separators.

### Searching Potential Maximum Clique and Minimum Separator

### The Boudhitté-Todinca Algorithm

#### Understanding the BT algorithm via the cop-robber game

#### The dynamic programming algorithm

### The Tamaki2022 Algorithm

#### Upper bound algorithm

#### Lower bound algorithm


<!-- Reference -->

[^Bouchitté]: Bouchitté, Vincent, and Ioan Todinca. “Treewidth and Minimum Fill-in: Grouping the Minimal Separators.” SIAM Journal on Computing 31, no. 1 (January 2001): 212–32. https://doi.org/10.1137/S0097539799359683.

[^Tamaki]: Tamaki, Hisao. “Heuristic Computation of Exact Treewidth.” Application/pdf, 2022, 16 pages, 743963 bytes. https://doi.org/10.4230/LIPICS.SEA.2022.17.
