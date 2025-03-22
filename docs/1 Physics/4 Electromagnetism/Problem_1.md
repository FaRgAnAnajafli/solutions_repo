# Problem 1

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

# Simulation loop using Lorentz force equation
positions = []
for _ in range(steps):
    # Lorentz force equation: F = q(E + v × B)
    F_electric = q * E
    F_magnetic = q * np.cross(v, B)
    F_total = F_electric + F_magnetic

    # Newton’s Second Law: F = m * a  →  a = F / m
    a = F_total / m

    # Update velocity: v_new = v_old + a * dt
    v = v + a * dt

    # Update position: r_new = r_old + v * dt
    r = r + v * dt

    # Store position
    positions.append(r)

# Print final position and velocity
print("Final Position:", positions[-1])
print("Final Velocity:", v)