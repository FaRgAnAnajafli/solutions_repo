# Problem 1

import numpy as np

# Constants
q = -1.6e-19   # Electron charge (C)
m = 9.11e-31   # Electron mass (kg)
B = np.array([0, 0, 1])  # Magnetic field (T) along the z-axis
E = np.array([0, 0, 0])  # Electric field (V/m), set to zero

# Initial conditions
r = np.array([0.0, 0.0, 0.0])  # Position (m)
v = np.array([1e5, 0.0, 0.0])   # Velocity (m/s) along x-axis

# Time parameters
dt = 1e-12    # Time step (s)
T = 1e-9      # Total simulation time (s)
steps = int(T / dt)  # Number of steps

# Arrays to store results
positions = np.zeros((steps, 3))
velocities = np.zeros((steps, 3))

# Simulation loop
for i in range(steps):
    F = q * (E + np.cross(v, B))  # Lorentz force: F = q(E + v × B)
    a = F / m  # Acceleration: a = F / m
    v = v + a * dt  # Update velocity: v_new = v_old + a * dt
    r = r + v * dt  # Update position: r_new = r_old + v * dt

    positions[i] = r
    velocities[i] = v

# Print final results
print("Final Position (m):", positions[-1])
print("Final Velocity (m/s):", velocities[-1])