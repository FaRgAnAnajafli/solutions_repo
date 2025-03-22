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

```python
import numpy as np
import matplotlib.pyplot as plt

# Constants
A = 1.0  # Amplitude of the waves
wavelength = 5.0  # Wavelength in meters
k = 2 * np.pi / wavelength  # Wave number
omega = 2 * np.pi  # Angular frequency (arbitrary for this simulation)
t = 0  # Time at the initial moment
source1 = np.array([5, 5])  # Position of source 1 (x1, y1)
source2 = np.array([15, 15])  # Position of source 2 (x2, y2)

# Create a grid for the water surface
x = np.linspace(0, 20, 400)
y = np.linspace(0, 20, 400)
X, Y = np.meshgrid(x, y)

# Function to compute the wave displacement at each point (superposition principle)
def wave_displacement(X, Y, source, A, k, omega, t):
    # Distance from the point (X, Y) to the wave source
    r = np.sqrt((X - source[0])**2 + (Y - source[1])**2)
    # Wave displacement (sinusoidal wave)
    displacement = A * np.sin(k * r - omega * t)
    return displacement

# Calculate the total displacement from both sources
displacement1 = wave_displacement(X, Y, source1, A, k, omega, t)
displacement2 = wave_displacement(X, Y, source2, A, k, omega, t)
total_displacement = displacement1 + displacement2

# Plotting the interference pattern
plt.figure(figsize=(8, 6))
plt.contourf(X, Y, total_displacement, levels=50, cmap='RdGy')
plt.colorbar(label='Displacement')
plt.title('Interference Pattern of Water Waves from Two Sources')
plt.xlabel('X Position (m)')
plt.ylabel('Y Position (m)')
plt.scatter(source1[0], source1[1], color='red', label='Source 1')
plt.scatter(source2[0], source2[1], color='blue', label='Source 2')
plt.legend()
plt.show()
```

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
