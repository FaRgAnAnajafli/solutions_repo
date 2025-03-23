# Problem 1
### **Equivalent Resistance Using Graph Theory**

#### **Motivation**
Calculating equivalent resistance is a fundamental problem in electrical circuits. As circuits become more complex, using traditional methods like series and parallel resistor combinations can become cumbersome. By applying graph theory, we can efficiently analyze complex circuits. The concept involves representing a circuit as a graph, where nodes represent junctions and edges represent resistors with weights equal to their resistance values.

Graph theory provides a structured and systematic way to simplify circuits. This method is particularly useful in network design, circuit simulation, and optimization.

#### **Task: Option 1 - Simplified Task - Algorithm Description**

In this task, we will describe an algorithm for calculating the equivalent resistance of a circuit using graph theory.

---

### **Algorithm for Calculating Equivalent Resistance using Graph Theory**

1. **Represent the Circuit as a Graph:**
   - Each junction in the circuit is represented as a node.
   - Each resistor is represented as an edge between two nodes. The weight of the edge corresponds to the resistance value of the resistor.

2. **Identify Series and Parallel Connections:**
   - **Series connection**: Resistors are in series if they share a common node and are connected end-to-end. The equivalent resistance for resistors in series is the sum of their individual resistances:
     \[
     R_{\text{eq}} = R_1 + R_2 + \dots + R_n
     \]
   - **Parallel connection**: Resistors are in parallel if they are connected between the same two nodes. The equivalent resistance for resistors in parallel is given by:
     \[
     \frac{1}{R_{\text{eq}}} = \frac{1}{R_1} + \frac{1}{R_2} + \dots + \frac{1}{R_n}
     \]

3. **Iterative Reduction of the Graph:**
   - Traverse the graph using Depth-First Search (DFS) or Breadth-First Search (BFS) to identify series and parallel resistor groups.
   - **For series**: Collapse the resistors in series into a single equivalent resistor and remove the intermediate nodes. Add the resistance of the series group to the circuit.
   - **For parallel**: Collapse the resistors in parallel into a single equivalent resistor and remove the intermediate nodes. Calculate the combined resistance using the formula for parallel resistors.

4. **Handle Nested Configurations:**
   - Nested series and parallel combinations can be handled by recursively applying the series and parallel reduction rules. If new series or parallel groups are identified after the first reduction, apply the rules again to simplify the circuit further.
   - If a cycle is detected, the graph should be handled using Kirchhoff's laws or numerical methods.

5. **Repeat Until a Single Equivalent Resistance is Found:**
   - Continue reducing the graph iteratively by simplifying series and parallel groups until only one node remains, representing the equivalent resistance of the entire circuit.

---

### **Pseudocode for the Algorithm**

Here’s a high-level pseudocode for the algorithm:

```python
def find_equivalent_resistance(circuit_graph):
    # Initialize graph
    while len(circuit_graph) > 1:  # While more than one node exists
        # Step 1: Identify series connections
        for each series_group in find_series(circuit_graph):
            equivalent_resistance = sum([resistor for resistor in series_group])
            # Collapse the series group into one resistor
            circuit_graph = collapse_series(circuit_graph, series_group, equivalent_resistance)

        # Step 2: Identify parallel connections
        for each parallel_group in find_parallel(circuit_graph):
            equivalent_resistance = 1 / sum([1 / resistor for resistor in parallel_group])
            # Collapse the parallel group into one resistor
            circuit_graph = collapse_parallel(circuit_graph, parallel_group, equivalent_resistance)
    
    return circuit_graph[0]  # The final node contains the equivalent resistance
```

### **Explanation of Algorithm Components**

- **find_series(circuit_graph)**: A function that scans the graph to find resistors that are connected in series (i.e., connected end-to-end with a common node). This function returns a list of series groups.
  
- **find_parallel(circuit_graph)**: A function that scans the graph to find resistors connected in parallel (i.e., connected between the same two nodes). This function returns a list of parallel groups.

- **collapse_series(circuit_graph, series_group, equivalent_resistance)**: A function that collapses a series group of resistors into a single resistor with the calculated equivalent resistance and removes the intermediate nodes.

- **collapse_parallel(circuit_graph, parallel_group, equivalent_resistance)**: A function that collapses a parallel group of resistors into a single resistor with the calculated equivalent resistance and removes the intermediate nodes.

---

### **Handling Nested Configurations**

Nested combinations of series and parallel resistors can be handled by recursively applying the reduction rules. For example:

1. **First pass**: Identify and reduce series and parallel groups in the circuit.
2. **Second pass**: After the initial reductions, new series and parallel groups might emerge from the simplification. Apply the rules again to further reduce the circuit.
3. **Repeat**: Continue applying these steps until the graph simplifies to a single node, which represents the equivalent resistance of the entire circuit.

---

### **Efficiency Considerations**

- **Graph traversal**: To identify series and parallel connections, graph traversal algorithms such as DFS or BFS are employed. These are typically linear in time complexity.
  
- **Repetitive simplification**: The circuit may have complex configurations, requiring multiple iterations of series and parallel reduction. The algorithm’s efficiency depends on how quickly it can identify and reduce these groups.

- **Cycle detection**: If cycles are present in the graph, they must be handled using Kirchhoff’s laws or numerical solvers to avoid non-linear systems. These systems can require more sophisticated methods like matrix inversion or iterative solvers.

---

### **Potential Improvements**

- **Optimized traversal**: For large circuits, advanced algorithms for detecting series and parallel groups, such as dynamic programming or optimized DFS/BFS, can speed up the process.
- **Handling large cycles**: For circuits with multiple loops, algorithms based on Kirchhoff’s laws or numerical solvers might be necessary.
- **Parallel processing**: If multiple independent circuits or sections of a circuit exist, parallel computing techniques can be employed to solve them concurrently.

---

### **Electromagnetism: Simulating the Effects of the Lorentz Force**

#### **Motivation**

The Lorentz force is fundamental in many physics applications, including particle accelerators, mass spectrometers, and plasma confinement. By simulating this force, we can better understand how charged particles behave in electric and magnetic fields.

#### **Task**

1. **Explore Applications**: 
   - **Particle accelerators**: The Lorentz force governs the acceleration of charged particles in cyclotrons and synchrotrons.
   - **Mass spectrometers**: The force helps separate particles based on their charge-to-mass ratio.
   - **Plasma confinement**: Magnetic fields control the movement of charged particles in fusion reactors.

2. **Simulate Particle Motion**:
   - **Uniform magnetic field**: Simulate a particle moving in a uniform magnetic field to observe circular motion (Lorentz force).
   - **Combined electric and magnetic fields**: Simulate a charged particle’s trajectory in a region with both electric and magnetic fields.
   - **Crossed electric and magnetic fields**: Explore how crossed fields affect particle motion, leading to drift or helical motion.

3. **Parameter Exploration**:
   - Vary the field strengths, initial velocities, and particle properties (charge, mass) to observe changes in trajectory.

4. **Visualization**:
   - Use 2D or 3D plots to show the particle’s path.
   - Highlight phenomena like the Larmor radius, drift velocity, and helicity of the motion.

---

This simulation will provide insights into the fundamental behavior of charged particles in fields, with applications ranging from accelerator physics to plasma research.