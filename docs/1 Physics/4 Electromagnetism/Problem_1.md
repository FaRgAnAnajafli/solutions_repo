# Problem 1

import numpy as np
import matplotlib.pyplot as plt

# Constants
q = -1.6e-19  # Electron charge (Coulombs)
m = 9.11e-31  # Electron mass (kg)
B = np.array([0, 0, 1])  # Magnetic field (Tesla)
E = np.array([0, 0, 0])  # Electric field (Volt/m) - set to zero here

# Initial conditions
r = np.array([0, 0, 0])  # Initial position (meters)
v = np.array([1e5, 0, 0])  # Initial velocity (m/s)

# Time parameters
dt = 1e-12  # Time step (seconds)
time = np.arange(0, 1e-9, dt)  # Time array (seconds)

# Motion equations
positions = []
for t in time:
    F_electric = q * E  # Electric force
    F_magnetic = q * np.cross(v, B)  # Magnetic force (Lorentz force)
    F_total = F_electric + F_magnetic  # Total force

    # Update velocity and position
    a = F_total / m  # Acceleration
    v = v + a * dt  # Update velocity
    r = r + v * dt  # Update position

    positions.append(r)

# Plot the trajectory
positions = np.array(positions)
plt.plot(positions[:, 0], positions[:, 1])
plt.xlabel('X position (m)')
plt.ylabel('Y position (m)')
plt.title('Electron Motion in a Magnetic Field')
plt.show()
