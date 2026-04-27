## MATRICES
### Adjacency Matrix
* **Principal Eigenvector:** Each component is a node 
* Highest value identifies the most important node

### Laplacian Matrix
* **Undirected:** Symmetric, all eigenvalues real and non-negative. Multiplicity of 0 equals the number of connected components.
* **Directed:** Non-symmetric. 0 eigenvalues signify strongly connected components.

## MICROSCALE
* Role of nodes
* Centrality, degree, betweenness

### 1. CENTRALITY
* **Degree:** Number of links a node has. Importance relative to nearest neighbors.
* **Degree Vector:** $Adjacency \times (1, 1, ..., 1) = (\text{Node degree vector})$
* **Out-degree & In-degree**
* **Strength:** Sum of weights of connections (for weighted networks)
* **Distance between nodes:** # of links in shortest path. Corresponds to the first power at which the matrix entry becomes non-zero.

> **NetworkX functions:** `degree_centrality`, `in_degree_centrality`, `out_degree_centrality`



#### 1.A. CLOSENESS
* Nodes close to many other nodes.
* **Closeness Centrality (CC):** Avg distance from a node to others.
* **Calculation:** Compute distance matrix $\rightarrow$ vector of distance-sums for each node $\rightarrow$ $CC = \frac{n-1}{\text{sum of distances}}$.

> **NetworkX (shortest paths):** `shortest_path`, `all_shortest_paths`, `shortest_path_length`, `average_shortest_path_length`, `has_path`, `closeness_centrality`

#### 1.B. BETWEENNESS
* How often a node lies on shortest paths between other pairs.
* **Betweenness Centrality:** Localizes bottlenecks and vulnerable points. A node can have low degree but high betweenness.

> **NetworkX functions:** `betweenness_centrality`, `edge_betweenness_centrality`



#### 1.C. EIGENVECTOR CENTRALITY
* Importance based on number and quality of links.
* High score for nodes connected to other highly connected nodes.
* **Score:** Sum of centrality scores of neighbors.
* **Calculation:** Eigenvalue problem. Unique largest real eigenvalue has an eigenvector with components $> 0$ (the result for each node).

> **NetworkX functions:** `eigenvector_centrality`, `eigenvector_centrality_numpy`, `katz_centrality`, `katz_centrality_numpy`, `pagerank`

* **PageRank:** Node importance = stationary probability of a random walker following links with occasional jumps. Recursive $\rightarrow$ fast convergence.
* **Katz Centrality:** Generalization of degree and eigenvector centrality. Considers longer paths, attenuated by a factor that decreases with length.

### 2. CLUSTERING
* Probability that two neighbors of node $i$ are connected.
* Fraction of possible triangles involving $i$ that are actually present.
* **Local Clustering**

> **NetworkX functions:** `triangles`, `transitivity`, `clustering`, `average_clustering`