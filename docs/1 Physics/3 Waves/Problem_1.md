# Problem 1
### Interference Patterns on a Water Surface

#### Motivation:
Interference patterns on a water surface occur when waves from different sources meet and interact. These interactions can lead to constructive interference (where waves reinforce each other) or destructive interference (where waves cancel each other out). The resulting interference pattern is often easy to observe visually and provides an excellent demonstration of fundamental wave properties such as phase, amplitude, and the principle of superposition.

Studying interference patterns helps us understand how waves interact in a variety of contexts, ranging from simple laboratory setups to complex systems in physics, acoustics, and optics. For example, interference plays a crucial role in the design of noise-canceling headphones, the study of diffraction, and even in the analysis of electromagnetic waves.

#### Objective:
- Explore the principles of wave interference by simulating the behavior of water waves.
- Investigate how wave sources at different positions interact with each other.
- Create visualizations of the resulting interference patterns on a water surface.

### 1. **Theory of Wave Interference**

Interference occurs when two or more waves overlap and combine. The nature of this combination depends on the phase difference between the waves:

- **Constructive Interference**: When waves are in phase (i.e., their peaks align), the resultant wave has an amplitude greater than that of the individual waves.
- **Destructive Interference**: When waves are out of phase (i.e., the peak of one wave coincides with the trough of another), the waves cancel each other out, leading to a reduced or zero amplitude.

For two-dimensional waves on a water surface, the wave function \( \psi(x, y, t) \) at any point on the surface can be represented as:

\[
\psi(x, y, t) = A \sin(kx + \phi) \cos(\omega t)
\]

Where:
- \( A \) is the amplitude of the wave,
- \( k \) is the wave number,
- \( x \) and \( y \) are the spatial coordinates,
- \( \phi \) is the phase of the wave,
- \( \omega \) is the angular frequency,
- \( t \) is time.

The interference pattern on the water surface is the result of the superposition of multiple wave functions.

### 2. **Setting Up the Simulation**

We can simulate the interference of waves on a water surface by modeling the behavior of waves from two or more point sources. To simplify, we assume that each point source generates a circular wave that propagates outward. The principle of superposition tells us that the net displacement at any point on the surface is the sum of the displacements due to each individual wave.

The general approach for simulating the interference patterns is as follows:

- **Step 1**: Define multiple point sources, each generating a wave.
- **Step 2**: For each point on the water surface, calculate the displacement by summing the contributions of all sources.
- **Step 3**: Visualize the resulting interference pattern.

### 3. **Numerical Simulation of Water Wave Interference**

We'll simulate the interference of two waves emanating from two different points on the surface of water. For simplicity, we'll assume the waves are circular and have the same frequency, amplitude, and wavelength. The resulting displacement at each point will be the sum of the individual wave displacements.

#### Python Code for Simulation:
![alt text](image.png)

### 4. **Explanation of the Simulation**

In this simulation:
- We define two sources at positions \( (5, 5) \) and \( (15, 15) \).
- The displacement at each point on the water surface is calculated using the superposition principle by adding the contributions from each source.
- We use a contour plot to visualize the interference pattern, with colors representing the wave displacement.

### 5. **Visualizing the Results**

- **Constructive Interference**: At points where the wave crests from both sources meet, the displacement will be large and positive (constructive interference).
- **Destructive Interference**: At points where a crest from one wave meets a trough from the other, the displacement will be small or zero (destructive interference).
- **Interference Pattern**: The resulting pattern will show regions of constructive and destructive interference, creating a distinct wave pattern on the surface.

### 6. **Applications of Interference Patterns**

Understanding water wave interference has several real-world applications:
- **Acoustics**: Interference is fundamental to sound waves, affecting how sound waves interact in various environments.
- **Optics**: Interference patterns are crucial for understanding diffraction and the behavior of light waves.
- **Engineering**: Interference is involved in the design of noise-canceling technology and vibration isolation systems.

### 7. **Conclusion**

The simulation of water wave interference allows us to visualize the principles of wave superposition and the resulting interference patterns. By altering parameters such as source position, wave amplitude, and wavelength, we can observe how these factors influence the resulting patterns, providing a deeper understanding of wave behavior.
