# Problem 1
### **Measuring Earth's Gravitational Acceleration with a Pendulum**

In this experiment, we will measure the acceleration due to gravity \( g \) using a simple pendulum. The period of oscillation of a pendulum is related to the length of the pendulum and the gravitational acceleration. We will carry out the measurements, calculate the value of \( g \), and then analyze the uncertainties in the measurements.

---

### **1. Materials**

- **String** (1 or 1.5 meters long)
- **Small weight** (e.g., a bag of coins, bag of sugar, key chain) mounted on the string
- **Stopwatch** (or smartphone timer)
- **Ruler or measuring tape**

---

### **2. Setup**

1. **Pendulum Construction:**
   - Attach the weight to one end of the string, and securely tie the other end of the string to a fixed point.
   - Ensure the string is long enough (1 or 1.5 meters) and that the weight is small and dense, such as a bag of coins or a key chain.
   
2. **Measurement of Pendulum Length \( L \):**
   - Measure the length of the pendulum from the suspension point to the center of the weight using a ruler or measuring tape.
   - Record the resolution of the measuring tool. For example, if your ruler can measure to the nearest millimeter, the uncertainty in your length measurement will be half of the resolution: \( \Delta L = 0.5 \, \text{mm} \) (or 0.0005 m).

---

### **3. Data Collection**

1. **Oscillation and Timing:**
   - Displace the pendulum slightly (less than 15°) from its equilibrium position and release it.
   - Use the stopwatch to measure the time for 10 full oscillations. Repeat this measurement 10 times and record the results.
   
2. **Calculating the Mean Time \( T_{\text{mean}} \):**
   - After measuring the time for 10 oscillations, calculate the mean time \( T_{\text{mean}} \) for these 10 measurements. 
   - Also, calculate the standard deviation \( \sigma_T \) of the time measurements.

3. **Uncertainty in Mean Time \( \Delta T_{\text{mean}} \):**
   - The uncertainty in the mean time can be calculated using the formula:
   \[
   \Delta T_{\text{mean}} = \frac{\sigma_T}{\sqrt{n}}
   \]
   where \( n \) is the number of measurements (in this case, 10).

---

### **4. Calculations**

#### **1. Period Calculation:**

The **period \( T \)** is the time for one full oscillation, and we can calculate it as:
\[
T = \frac{T_{\text{mean}}}{10}
\]
where \( T_{\text{mean}} \) is the time for 10 oscillations.

#### **2. Determining \( g \):**

The period of a simple pendulum is related to its length \( L \) and the acceleration due to gravity \( g \) by the formula:
\[
T = 2\pi \sqrt{\frac{L}{g}}
\]

Rearranging this equation to solve for \( g \):
\[
g = \frac{4\pi^2 L}{T^2}
\]

#### **3. Propagating Uncertainties:**

To calculate the uncertainty in \( g \), we need to propagate the uncertainties in \( L \) and \( T \). The formula for uncertainty propagation in this case is:

\[
\Delta g = \sqrt{\left( \frac{\partial g}{\partial L} \Delta L \right)^2 + \left( \frac{\partial g}{\partial T} \Delta T \right)^2}
\]

From the formula \( g = \frac{4\pi^2 L}{T^2} \), the partial derivatives are:

\[
\frac{\partial g}{\partial L} = \frac{4\pi^2}{T^2}, \quad \frac{\partial g}{\partial T} = -\frac{8\pi^2 L}{T^3}
\]

Thus, the uncertainty in \( g \) becomes:

\[
\Delta g = \sqrt{\left( \frac{4\pi^2}{T^2} \Delta L \right)^2 + \left( -\frac{8\pi^2 L}{T^3} \Delta T \right)^2}
\]

---

### **5. Example Python Code**

Here is an example Python code to carry out the calculations and plot the results:

```python
import numpy as np
import matplotlib.pyplot as plt

# Given values
L = 1.0  # Length of the pendulum in meters (example)
n = 10  # Number of measurements
T_measurements = np.array([20.1, 20.2, 19.9, 20.0, 20.3, 20.1, 20.0, 19.8, 20.2, 19.9])  # Times for 10 oscillations (in seconds)

# Calculate the mean and standard deviation
T_mean = np.mean(T_measurements)
T_std = np.std(T_measurements)

# Calculate the period for one oscillation
T = T_mean / n

# Uncertainty in the mean time
delta_T_mean = T_std / np.sqrt(n)

# Calculate g
g = (4 * np.pi**2 * L) / (T**2)

# Uncertainty in g (propagating uncertainty)
delta_L = 0.0005  # Uncertainty in length (example: 0.5 mm)
delta_T = delta_T_mean / n  # Uncertainty in period (adjusted for 1 oscillation)
delta_g = np.sqrt((4 * np.pi**2 / T**2 * delta_L)**2 + (-8 * np.pi**2 * L / T**3 * delta_T)**2)

# Print results
print(f"Estimated g = {g:.4f} m/s²")
print(f"Uncertainty in g = {delta_g:.4f} m/s²")

# Tabulated data
data = {
    'Measurement': T_measurements,
    'Mean Time (T_mean)': T_mean,
    'Standard Deviation (σ_T)': T_std,
    'Period (T)': T,
    'Gravitational Acceleration (g)': g,
    'Uncertainty in g (Δg)': delta_g
}

# Plotting the data
plt.hist(T_measurements, bins=10, alpha=0.7, label="Time Measurements")
plt.axvline(T_mean, color='red', linestyle='dashed', linewidth=2, label=f"Mean Time = {T_mean:.2f} s")
plt.xlabel('Time (s)')
plt.ylabel('Frequency')
plt.title('Histogram of Pendulum Time Measurements')
plt.legend()
plt.show()
```

---

### **6. Discussion and Analysis**

#### **1. Compare Measured \( g \) with Standard Value**

The measured value of \( g \) should be compared with the standard value of \( g \) (approximately \( 9.81 \, \text{m/s}^2 \)) to assess the accuracy of the experiment. The difference between the measured and standard values can be attributed to experimental uncertainties.

#### **2. Uncertainty in Length Measurement**

The resolution of the measuring tool directly affects the uncertainty in \( L \), which then propagates into the calculation of \( g \). A more precise measurement of the pendulum length would reduce the uncertainty in the calculated \( g \).

#### **3. Variability in Timing and Its Impact on \( g \)**

Variability in timing, due to human reaction time or stopwatch accuracy, can affect the uncertainty in the period and, consequently, the acceleration due to gravity. A more accurate timer or a greater number of measurements can help reduce this variability.

#### **4. Assumptions and Experimental Limitations**

- **Small Angle Approximation:** The pendulum should be displaced by less than 15° to avoid significant errors due to the non-linear relationship between the period and the amplitude.
- **Air Resistance:** This model assumes negligible air resistance, but in practice, air drag can affect the pendulum's motion, especially for longer pendulums or larger amplitudes.
- **Measurement Error:** Human error in timing and measuring the length can contribute to uncertainties.

---

### **Deliverables**

1. **Tabulated Data** in markdown:
   - **Time measurements**: Raw data of the time for 10 oscillations.
   - **Mean time** (\( T_{\text{mean}} \)), **standard deviation** (\( \sigma_T \)), **period** (\( T \)), **gravitational acceleration** (\( g \)), and **uncertainty in \( g \)**.

2. **Discussion on Uncertainties**:
   - Analyze the impact of uncertainties in length, timing, and measurement resolution on the results.
   
3. **Python Code**:
   - Code to calculate the period, gravitational acceleration, and uncertainties.

4. **Plots**:
   - Histogram of time measurements and the visualization of how the uncertainty propagates in the experiment.

By following this procedure, you will gain insights into the accuracy of your measurements and the role of uncertainty in experimental physics.
