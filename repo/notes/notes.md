# Network Analysis Notes

## REPRESENTATION
* **Network**
* **Structure**
* **Functionality**

## CHARACTERIZATION
* **Centrality:** * Local (who collaborates with whom)
    * Global (who is closer to the rest)
* **Communities**
* **Statistics** (distribution, divergencies)

## DYNAMICS
* Diffusion
* Epidemics
* Forecasting

## STRUCTURAL VS RELATIONAL

## SCALES
* **Micro** *
* **Meso**
* **Macro**

## THEME
* Node
* Links
* Networks

---

## KEY QUESTIONS & CONCEPTS
* Who is central? Who bridges groups? Who is peripheral?
* **Links:** Directly given or inferred?
* **Graph vs. Matrix**
* **Link Pairs vs. Neighbors List**
* **Degree of a node**
* **Number of links**
* **Average Degree:** Typical local connectivity
* **Sparsification:**
    * Weight thresholding (local)
    * Minimum Spanning Tree (global)
* **Bipartite Networks**
* **Density → Memory:** Avoid adjacency matrix for large and sparse networks

---

## MATRICES
### Adjacency Matrix
* **Principal Eigenvector:** Each component is a node 
* Highest value identifies the most important node

### Laplacian Matrix
* **Undirected:** Symmetric, all eigenvalues real and non-negative. Multiplicity of 0 equals the number of connected components.
* **Directed:** Non-symmetric. 0 eigenvalues signify strongly connected components.
