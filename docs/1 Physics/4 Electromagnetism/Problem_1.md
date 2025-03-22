# Problem 1

## Problem 1

$```python
import numpy as np

# Constants
q = -1.6e-19   # Electron charge (Coulombs)
m = 9.11e-31   # Electron mass (kg)
B = np.array([0, 0, 1])  # Magnetic field (Tesla) along the z-axis
E = np.array([0, 0, 0])  # Electric field (V/m), set to zero

# Initial conditions
r = np.array([0.0, 0.0, 0.0])  # Initial position (m)
v = np.array([1e5, 0.0, 0.0])   # Initial velocity (m/s) along x-axis

# Time parameters
dt = 1e-12    # Time step (seconds)
T = 1e-9      # Total simulation time (seconds)
steps = int(T / dt)  # Number of steps

# Simulation loop
for _ in range(steps):
    F = q * (E + np.cross(v, B))  # Lorentz force
    a = F / m  # Acceleration (F = ma)
    v = v + a * dt  # Update velocity
    r = r + v * dt  # Update position

# Print results
print("Final Position:", r)
print("Final Velocity:", v)
```$