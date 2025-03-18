import math

# Universal Gravitational Constant (N·m²/kg²)
G = 6.674 * (10 ** -11)

# Mass of Earth (kg)
M_EARTH = 5.972 * (10 ** 24)

# Radius of Earth (m)
R_EARTH = 6.371 * (10 ** 6)

def gravitational_force(m1, m2, r):
    """Calculates the gravitational force between two masses."""
    return G * (m1 * m2) / (r ** 2)

def free_fall_velocity(t, g=9.81):
    """Calculates velocity during free fall (m/s)."""
    return g * t

def free_fall_distance(t, g=9.81):
    """Calculates distance fallen during free fall (m)."""
    return 0.5 * g * (t ** 2)

def orbital_velocity(r, M=M_EARTH):
    """Calculates the orbital velocity required for an object to stay in orbit (m/s)."""
    return math.sqrt(G * M / r)

def escape_velocity(R, M=M_EARTH):
    """Calculates the escape velocity required to leave Earth's gravity (m/s)."""
    return math.sqrt(2 * G * M / R)

# Example usage
mass1 = 70  # kg (human mass)
mass2 = M_EARTH  # kg (Earth mass)
distance = R_EARTH  # m (Earth's surface)

force = gravitational_force(mass1, mass2, distance)
fall_time = 5  # seconds
velocity = free_fall_velocity(fall_time)
distance_fallen = free_fall_distance(fall_time)
orbit_speed = orbital_velocity(R_EARTH)
escape_speed = escape_velocity(R_EARTH)

# Print results
print(f"Gravitational Force: {force:.2f} N")
print(f"Velocity after {fall_time} seconds of free fall: {velocity:.2f} m/s")
print(f"Distance fallen after {fall_time} seconds: {distance_fallen:.2f} m")
print(f"Orbital speed for Earth: {orbit_speed:.2f} m/s")
print(f"Escape velocity for Earth: {escape_speed:.2f} m/s")
