import numpy as np
import matplotlib.pyplot as plt
from scipy.integrate import solve_ivp

# Parameters
g = 9.81  # Gravitational acceleration (m/s^2)
L = 1.0  # Length of the pendulum (m)
gamma = 0.1  # Damping coefficient
F0 = 1.0  # Driving force amplitude
omega = 1.0  # Driving frequency
theta0 = 0.5  # Initial angular displacement (rad)
omega0 = 0.0  # Initial angular velocity (rad/s)

# Differential equation for the forced damped pendulum
def pendulum(t, y):
    theta, omega = y
    dydt = [omega, -2*gamma*omega - (g/L)*np.sin(theta) + F0*np.cos(omega*t)]
    return dydt

# Time span for the simulation
t_span = (0, 50)  # 50 seconds
t_eval = np.linspace(*t_span, 1000)

# Initial conditions
y0 = [theta0, omega0]

# Solve the differential equation using Runge-Kutta method
solution = solve_ivp(pendulum, t_span, y0, t_eval=t_eval)

# Extract results
theta = solution.y[0]
omega = solution.y[1]
time = solution.t

# Visualization of the motion
plt.figure(figsize=(12, 6))
plt.subplot(1, 2, 1)
plt.plot(time, theta)
plt.title('Angular Displacement vs Time')
plt.xlabel('Time (s)')
plt.ylabel('Angular Displacement (rad)')

# Phase space plot (theta vs omega)
plt.subplot(1, 2, 2)
plt.plot(theta, omega)
plt.title('Phase Space: Theta vs Omega')
plt.xlabel('Angular Displacement (rad)')
plt.ylabel('Angular Velocity (rad/s)')

plt.tight_layout()
plt.show()

# Poincare Section (plot at each time step where the velocity is zero)
poincare_theta = theta[omega == 0]

plt.figure(figsize=(8, 6))
plt.plot(poincare_theta, 'o', label='Poincare Section')
plt.title('Poincare Section')
plt.xlabel('Theta (rad)')
plt.ylabel('Poincare Points')
plt.legend()
plt.show()