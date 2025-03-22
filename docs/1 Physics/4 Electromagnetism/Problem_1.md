# Problem 1

import numpy as np

# Constants
q = -1.6e-19   # Electron charge (Coulombs)
m = 9.11e-31   # Electron mass (kg)
B = np.array([0, 0, 1])  # Magnetic field (Tesla) along the z-axis
E = np.array([0, 0, 0])  # Electric field (Volts per meter), set to zero

# Initial conditions
r = np.array([0.0, 0.0, 0.0])  # Initial position (meters)
v = np.array([1e5, 0.0, 0.0])   # Initial velocity (m/s) along x-axis

# Time parameters
dt = 1e-12    # Time step (seconds)
T = 1e-9      # Total simulation time (seconds)
steps = int(T / dt)  # Number of steps (total time / time step)

# Simulation loop
for _ in range(steps):
    # Lorentz force: F = q * (E + v x B)
    F = q * (E + np.cross(v, B))  
    
    # Calculate acceleration: a = F / m
    a = F / m  
    
    # Update velocity: v(t+dt) = v(t) + a * dt
    v = v + a * dt  
    
    # Update position: r(t+dt) = r(t) + v * dt
    r = r + v * dt  

# Print results
print("Final Position:", r)
print("Final Velocity:", v)

