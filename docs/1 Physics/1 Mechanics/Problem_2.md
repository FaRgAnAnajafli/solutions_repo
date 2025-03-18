# Newton's Laws of Motion 🚀

Newton's laws of motion describe the relationship between the motion of an object and the forces acting on it. These laws are fundamental principles in physics.

## **1st Law: Law of Inertia**
> An object at rest stays at rest, and an object in motion stays in motion with the same speed and in the same direction unless acted upon by an unbalanced force.

Mathematically:
\[
F_{\text{net}} = 0 \Rightarrow \text{constant velocity}
\]

## **2nd Law: Law of Acceleration**
> The acceleration of an object is directly proportional to the net force acting on it and inversely proportional to its mass.

\[
F = m a
\]

Where:
- \( F \) = Net force (N)
- \( m \) = Mass (kg)
- \( a \) = Acceleration (m/s²)

## **3rd Law: Action and Reaction**
> For every action, there is an equal and opposite reaction.

Mathematically:
\[
F_{\text{action}} = -F_{\text{reaction}}
\]

This means forces always occur in **pairs**.

---

## **Code Example: Newton's 2nd Law in Python**
```python
# Newton's Second Law: F = m * a

def newton_second_law(mass, acceleration):
    """Calculate Force using Newton's 2nd Law."""
    return mass * acceleration

# Example
mass = 10  # kg
acceleration = 5  # m/s²
force = newton_second_law(mass, acceleration)

print(f"Force: {force} N")  # Output: Force: 50 N
