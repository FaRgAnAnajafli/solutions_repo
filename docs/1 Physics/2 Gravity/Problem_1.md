

import math

# Gravitational constant (m^3 kg^-1 s^-2)
G = 6.67430e-11

# Mass of Earth (kg)
M_EARTH = 5.972e24

# Radius of Earth (m)
R_EARTH = 6.371 * (10 ** 6)

def gravitational_force(m1, m2, r):
    """
    This function calculates the gravitational force between two masses.
    
    Parameters:
    m1 -- Mass of the first object (in kg)
    m2 -- Mass of the second object (in kg)
    r -- Distance between the two masses (in meters)
    
    Returns:
    Gravitational force (in Newtons)
    """
    # Gravitational force formula: F = G * (m1 * m2) / r^2
    force = G * (m1 * m2) / (r ** 2)
    return force

def free_fall_velocity(t, g=9.81):
    """
    This function calculates the velocity of an object during free fall.
    
    Parameters:
    t -- Time of free fall (in seconds)
    g -- Gravitational acceleration (in m/s^2, default value is 9.81 m/s^2)
    
    Returns:
    Velocity during free fall (in m/s)
    """
    # Free fall velocity formula: v = g * t
    velocity = g * t
    return velocity

def free_fall_distance(t, g=9.81):
    """
    This function calculates the distance fallen by an object during free fall.
    
    Parameters:
    t -- Time of free fall (in seconds)
    g -- Gravitational acceleration (in m/s^2, default value is 9.81 m/s^2)
    
    Returns:
    Distance fallen during free fall (in meters)
    """
    # Free fall distance formula: d = 0.5 * g * t^2
    distance = 0.5 * g * (t ** 2)
    return distance

def orbital_velocity(r, M=M_EARTH):
    """
    This function calculates the orbital velocity required for an object to stay in orbit.
    
    Parameters:
    r -- Orbital radius (in meters)
    M -- Mass of Earth (in kg, default value is Earth's mass)
    
    Returns:
    Orbital velocity (in m/s)
    """
    # Orbital velocity formula: v = √(G * M / r)
    velocity = math.sqrt(G * M / r)
    return velocity

def escape_velocity(R, M=M_EARTH):
    """
    This function calculates the escape velocity required to leave Earth's gravity.
    
    Parameters:
    R -- Distance from Earth's surface (in meters)
    M -- Mass of Earth (in kg, default value is Earth's mass)
    
    Returns:
    Escape velocity (in m/s)
    """
    # Escape velocity formula: v_escape = √(2 * G * M / R)
    velocity = math.sqrt(2 * G * M / R)
    return velocity
