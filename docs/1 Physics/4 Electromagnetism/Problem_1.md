# Problem 1
import numpy as np
import matplotlib.pyplot as plt

# Constants
q = -1.6e-19  # Electron charge (Coulombs)
m = 9.11e-31  # Electron mass (kg)
B = np.array([0, 0, 1])  # Magnetic field (Tesla) along the z-axis
E = np.array([0, 0, 0])  # Electric field (V/m), set to zero for now

# Initial conditions
r = np.array([0.0, 0.0, 0.0])  # Initial position (meters)
v = np.array([1e5, 0.0, 0.0])  # Initial velocity (m/s) along x-axis

# Time parameters
dt = 1e-12  # Time step (seconds)
T = 1e-9  # Total simulation time (seconds)
steps = int(T / dt)  # Number of steps

# Arrays to store position data
x, y, z = [], [], []

# Simulation loop using Lorentz force
for _ in range(steps):
    # Lorentz force equation: F = q(E + v × B)
    F_electric = q * E
    F_magnetic = q * np.cross(v, B)
    F_total = F_electric + F_magnetic

    # Newton's Second Law: F = m * a  =>  a = F / m
    a = F_total / m

    # Update velocity using kinematic equation: v_new = v_old + a * dt
    v = v + a * dt

    # Update position using kinematic equation: r_new = r_old + v * dt
    r = r + v * dt

    # Store position values for plotting
    x.append(r[0])
    y.append(r[1])
    z.append(r[2])

# Plot the trajectory in 2D
plt.figure(figsize=(8, 6))
plt.plot(x, y, label="Electron Path")
plt.xlabel("X Position (m)")
plt.ylabel("Y Position (m)")
plt.title("Electron Motion in a Magnetic Field")
plt.legend()
plt.grid()
plt.show()