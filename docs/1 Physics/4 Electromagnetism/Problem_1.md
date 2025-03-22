# Problem 1

import numpy as np
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