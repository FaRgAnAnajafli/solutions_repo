# Problem 1
### Equivalent Resistance Using Graph Theory

#### Motivation:
Calculating the equivalent resistance of a complex electrical circuit can be challenging when using traditional methods like series and parallel resistor rules. In circuits with many components, this process can become cumbersome. However, by representing electrical circuits as graphs, where nodes correspond to junctions and edges represent resistors, graph theory provides an efficient and systematic way to calculate the equivalent resistance of even the most intricate networks.

#### Approach:
In this approach, the circuit is modeled as a graph:
- **Nodes**: Represent junctions in the circuit.
- **Edges**: Represent resistors between those junctions, with edge weights equal to the resistance values.

### Option 1: Simplified Task – Algorithm Description

The core idea of using graph theory for calculating equivalent resistance is to reduce the graph step-by-step, simplifying series and parallel resistor connections iteratively until only one equivalent resistance remains. Let's break down the steps and describe the algorithm in detail.

#### Algorithm Overview:

1. **Graph Representation**:
   - The circuit is represented as a graph \( G = (V, E) \), where \( V \) are the nodes (junctions) and \( E \) are the edges (resistors).
   - Each edge \( (u, v) \in E \) has a weight corresponding to the resistance \( R \) between nodes \( u \) and \( v \).

2. **Identify Series and Parallel Connections**:
   - **Series Connection**: Two resistors are in series if they are connected end-to-end, meaning there is no other node between them.
     - Equivalent resistance for two resistors \( R_1 \) and \( R_2 \) in series: 
       \[
       R_{\text{eq}} = R_1 + R_2
       \]
   - **Parallel Connection**: Two resistors are in parallel if they share both the same nodes.
     - Equivalent resistance for two resistors \( R_1 \) and \( R_2 \) in parallel:
       \[
       \frac{1}{R_{\text{eq}}} = \frac{1}{R_1} + \frac{1}{R_2}
       \]

3. **Graph Reduction**:
   - The graph is iteratively reduced by identifying pairs of nodes connected by series or parallel resistors.
   - **Series Reduction**: If two nodes are connected by a series of resistors, replace them with a single equivalent resistor whose resistance is the sum of the individual resistances.
   - **Parallel Reduction**: If two nodes are connected by resistors in parallel, replace them with a single equivalent resistor using the parallel formula.

4. **Handle Nested Configurations**:
   - If a reduction leads to a new series or parallel configuration (i.e., the new equivalent resistor becomes part of a larger network), repeat the process.
   - Continue simplifying the graph until only one node remains, representing the equivalent resistance of the entire circuit.

#### Pseudocode:

```plaintext
1. Initialize the circuit graph G(V, E), where V is the set of nodes and E is the set of edges with resistance values.
2. While the graph has more than one node:
   a. Search for series connections in the graph.
      - For each pair of nodes (u, v) connected by resistors in series:
         - Replace the series connection with an equivalent resistor whose resistance is the sum of individual resistances.
   b. Search for parallel connections in the graph.
      - For each pair of nodes (u, v) connected by resistors in parallel:
         - Replace the parallel connection with an equivalent resistor calculated using the parallel formula.
   c. If new series or parallel combinations are formed, repeat step 2.
3. Once only one node remains, return the equivalent resistance.
```

#### Explanation:
- The algorithm starts by iterating over the graph to find series or parallel resistor configurations.
- After reducing the graph step-by-step, it continues simplifying until a single equivalent resistor is calculated.
- The algorithm ensures that both simple and nested resistor networks are handled efficiently by applying reductions iteratively.

### Option 2: Advanced Task – Full Implementation

In this more advanced task, we will implement the algorithm described above in Python using the **NetworkX** library, which allows easy manipulation of graphs. The full implementation handles arbitrary resistor configurations, including nested series and parallel combinations.

#### Python Code Implementation:

```python
import networkx as nx

def calculate_equivalent_resistance(G):
    """
    Calculates the equivalent resistance of a circuit represented as a graph using series and parallel reductions.
    """
    while len(G.nodes) > 1:
        # Look for series connections (two resistors in series)
        for edge in list(G.edges(data=True)):
            u, v, data = edge
            R = data['resistance']
            # Check if u and v are connected only by this resistor (series connection)
            if len(list(G.neighbors(u))) == 2 and len(list(G.neighbors(v))) == 2:
                # Combine u and v into a new node with the equivalent resistance
                new_node = u
                G.add_edge(u, v, resistance=R)
                G.remove_edge(u, v)
                
                # Recalculate the resistance after combining the two resistors
                G[u][v]['resistance'] = R  # Update resistance

        # Look for parallel connections (two resistors in parallel)
        for edge in list(G.edges(data=True)):
            u, v, data = edge
            R = data['resistance']
            if u and v connected directly in parallel:
