# Problem 1
import numpy as np
import matplotlib.pyplot as plt
from scipy.integrate import solve_ivp

# Constants
eq = 1.6e-19  # Electron charge (C)
m = 9.11e-31  # Electron mass (kg)
B = np.array([0, 0, 1])  # Magnetic field (Tesla) [in z-direction]
E = np.array([0, 0, 0])  # Electric field (V/m)

# Lorentz force function
def lorentz_force(t, y):
    r = y[:3]  # Position vector
    v = y[3:]  # Velocity vector
    F = eq * (E + np.cross(v, B))  # Lorentz force
    a = F / m  # Acceleration
    return np.concatenate((v, a))

# Initial conditions
r0 = np.array([0, 0, 0])  # Initial position
v0 = np.array([1e6, 1e6, 0])  # Initial velocity (m/s)
y0 = np.concatenate((r0, v0))

# Time range
t_span = (0, 1e-7)
t_eval = np.linspace(t_span[0], t_span[1], 1000)

# Solution
tol = 1e-9  # Precision
sol = solve_ivp(lorentz_force, t_span, y0, t_eval=t_eval, rtol=tol, atol=tol)

# 3D Motion Plot
fig = plt.figure(figsize=(12, 6))
ax = fig.add_subplot(121, projection='3d')
ax.plot(sol.y[0], sol.y[1], sol.y[2], label="Particle Path")
ax.set_xlabel("X (m)")
ax.set_ylabel("Y (m)")
ax.set_zlabel("Z (m)")
ax.set_title("Charged Particle Motion in a Magnetic Field")
ax.legend()

# 2D Projection Plots
ax2 = fig.add_subplot(222)
ax2.plot(sol.t, sol.y[0], label="X Position")
ax2.plot(sol.t, sol.y[1], label="Y Position")
ax2.plot(sol.t, sol.y[2], label="Z Position")
ax2.set_xlabel("Time (s)")
ax2.set_ylabel("Position (m)")
ax2.set_title("Position vs. Time")
ax2.legend()

ax3 = fig.add_subplot(224)
ax3.plot(sol.t, np.linalg.norm(sol.y[3:], axis=0), label="Velocity Magnitude")
ax3.set_xlabel("Time (s)")
ax3.set_ylabel("Velocity (m/s)")
ax3.set_title("Velocity vs. Time")
ax3.legend()

plt.tight_layout()
plt.show()


