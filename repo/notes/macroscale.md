# Macroscale Network Analysis

## Index of Contents
1. [Shortest Paths & Connectedness](#1-connectedness-and-distance)
2. [Clustering](#2-clustering)
3. [Distributions](#3-degree-distributions)
4. [Statistical Properties & Betweenness](#4-betweenness)
5. [Correlations](#5-correlations)

---

## 1. Connectedness and Distance

### Connectivity
* **Undirected Graphs:** Focus on **Connected Components**.
* **Directed Graphs:**
    * **Strongly Connected Components:** Every node is reachable from every other node.
    * **Weakly Connected Components:** Connected if edge directions are ignored.
    * **In-component:** Nodes that can reach a specific node.
    * **Out-component:** Nodes reachable from a specific node.

### Distance and Centrality
* **Distance:** The number of links in the shortest path between two nodes.
* **Centrality:** Identifies nodes that are "close" to many other nodes.
* **Global Centrality:** The sum of minimum distances to all other nodes in the network.

### Global Network Measures
* **Mean Shortest Path ($L$):** The average distance over all pairs of nodes.
* **Diameter:** The largest distance between any pair of nodes.
* **Small World Property:** In many real networks, $L \sim \ln(N)$. The max distance is proportional to $\frac{\log(N)}{\log(\langle k \rangle)}$.

### NetworkX Functions
| Function | Description |
| :--- | :--- |
| `eccentricity()` | Max distance from a node to all other nodes. |
| `diameter()` | The maximum eccentricity. |
| `radius()` | The minimum eccentricity. |
| `center()` | Set of nodes where eccentricity == radius. |
| `periphery()` | Set of nodes where eccentricity == diameter. |
| `dijkstra_path()` | Shortest paths in a weighted graph. |

---

## 2. Clustering

Measures how nodes tend to cluster together (triadic closure).

* **Clustering Coefficient (Node):** Local density of a node’s neighborhood.
* **Clustering Coefficient (Network/Watts-Strogatz):** How clustered a network is locally (average of local coefficients).
* **Transitivity (Newman):** How clustered the network is as a whole (ratio of triangles to triples).
* **Real World Observation:** Clustering coefficients in real networks are much larger than in equivalent random networks.

### NetworkX Functions
* `triangles()`
* `transitivity()`
* `clustering()`
* `average_clustering()`
* `square_clustering()`

---

## 3. Degree Distributions

### Statistical Properties
The Degree Distribution $P(k)$ is the probability that a random node has degree $k$.
* **Random/Lattice Networks:** Majority of nodes have roughly the same degree (Poisson or Normal distribution).
* **Real Networks:** Heterogeneous; "Scale-free" with a **Power Law** tail.

### Power Laws
Standard formula: $P(k) = a \cdot k^{-\gamma}$, where $2 < \gamma < 3$.
* **Log-Log Plot:** Appears as a straight line with slope $= -\gamma + 1$.
* **Fitting Issues:** Least squares regression often gives incorrect exponents due to the heavy tail. 
* **Solutions:** * Bin data into exponentially wider bins.
    * Normalize by bin width.
    * Use **Cumulative Distribution (CDF)**: $P(K \le k) = 1 - k^{-\gamma+1}$.

### Alternative Distributions
* **Power Law with Exponential Cutoff:** $p(x) \sim x^{-\alpha} e^{-x/\kappa}$ (Common in power grids or email networks to avoid "blackouts").

---

## 4. Betweenness

* **Observation:** Hubs (high degree) usually have high betweenness, but high betweenness nodes are not always hubs (e.g., bridges between two large communities).

---

## 5. Correlations

### Degree Correlations
Expected degree of neighbors as a function of a node's own degree.
* **Detailed Balance Equation:** $P(k_1, k_2) = k_1 P(k_1) P(k_2|k_1) = k_2 P(k_2) P(k_1|k_2)$.
* **Avg. Degree of Nearest Neighbors ($k_{nn}$):** $k_{nn}(k) = \sum_{k'} k' P(k'|k) = f(k)$.

### Assortativity ($r$)
A global measure (Newman) of correlation between degrees at both ends of all edges.
* **Assortative ($r > 0$):** High-degree nodes connect to high-degree nodes ($k_{nn}$ increases with $k$).
* **Dissortative ($r < 0$):** High-degree nodes connect to low-degree nodes ($k_{nn}$ decreases with $k$).

### NetworkX Functions
* `degree_assortativity_coefficient()`
* `attribute_assortativity_coefficient()`
* `numeric_assortativity_coefficient()`
* `degree_pearson_correlation_coefficient()`
* `average_neighbor_degree()`