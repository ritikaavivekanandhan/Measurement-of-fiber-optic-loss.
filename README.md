# Measurement-of-fiber-optic-loss.
# Experimental Verification of Various Fiber Losses — Propagation Loss and Bending Loss

# Propagation and Bending Losses in Plastic Fiber

## AIM

To measure propagation loss and bending loss for different wavelengths in the plastic optical fiber provided with the kit.

---

## EQUIPMENTS REQUIRED

- Link-B Kit with power supply
- Patch cords
- Dual-channel oscilloscope
- Function generator
- Optical fiber cable

---

## THEORY

Optical fibers are available in different varieties of materials. These materials are selected based on their absorption characteristics for different wavelengths of light.

Since signals in optical fibers are transmitted in the form of light, the interaction between light and the fiber material must be considered to understand the losses occurring during transmission.

### Propagation Loss

Propagation loss is the reduction in optical signal power as light travels through an optical fiber.

- A portion of the light is absorbed by the fiber material, causing absorption loss.
- Light may be scattered due to impurities and imperfections in the fiber.
- The signal power decreases as the fiber length increases.
- Plastic optical fibers generally have higher attenuation than glass optical fibers.

### Bending Loss

Bending loss occurs when an optical fiber is bent, causing some of the guided light to escape from the fiber.

- When the fiber is bent, the condition for total internal reflection may be disturbed.
- A smaller bending radius generally causes greater optical power loss.
- The received signal amplitude decreases as the bending becomes tighter.
- Additional losses may occur at the light source and photodetector connections.

---

## CODE

~~~
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt

# Change these values whenever you want
frequency = 1000

# Propagation loss values
length = [1, 2, 3, 4]
input_amp = [5.0, 5.0, 5.0, 5.0]
output_amp = [4.5, 4.2, 3.9, 3.6]

# Bending loss values
diameter = [30, 25, 20, 15]
bend_input = [5.0, 5.0, 5.0, 5.0]
bend_output = [4.8, 4.5, 4.0, 3.2]

# Calculate propagation loss
prop_loss = [
    20 * np.log10(i / o)
    for i, o in zip(input_amp, output_amp)
]

# Calculate bending loss
bend_loss = [
    20 * np.log10(i / o)
    for i, o in zip(bend_input, bend_output)
]

# Display propagation table
print("PROPAGATION LOSS")
display(pd.DataFrame({
    "Length (m)": length,
    "Input (V)": input_amp,
    "Output (V)": output_amp,
    "Loss (dB)": np.round(prop_loss, 2)
}))

# Display bending table
print("BENDING LOSS")
display(pd.DataFrame({
    "Diameter (mm)": diameter,
    "Input (V)": bend_input,
    "Output (V)": bend_output,
    "Loss (dB)": np.round(bend_loss, 2)
}))

# Generate graphs
t = np.linspace(0, 4 / frequency, 1000)

plt.figure(figsize=(10, 5))
for i in range(4):
    plt.plot(t, input_amp[i] * np.sin(2*np.pi*frequency*t),
             label=f"Input {length[i]} m")
    plt.plot(t, output_amp[i] * np.sin(2*np.pi*frequency*t),
             "--", label=f"Output {length[i]} m")

plt.title("Propagation Loss")
plt.xlabel("Time (s)")
plt.ylabel("Voltage (V)")
plt.grid(True)
plt.legend(ncol=2)
plt.show()

plt.figure(figsize=(10, 5))
for i in range(4):
    plt.plot(t, bend_input[i] * np.sin(2*np.pi*frequency*t),
             label=f"Input {diameter[i]} mm")
    plt.plot(t, bend_output[i] * np.sin(2*np.pi*frequency*t),
             "--", label=f"Output {diameter[i]} mm")

plt.title("Bending Loss")
plt.xlabel("Time (s)")
plt.ylabel("Voltage (V)")
plt.grid(True)
plt.legend(ncol=2)
plt.show()

~~~

### Formula for Propagation Loss

The attenuation coefficient can be calculated using:

`α = ln(V1/V2) / (L2 - L1)`

Where:

- `α` = attenuation coefficient in nepers per unit length
- `V1` = received signal voltage for the shorter fiber
- `V2` = received signal voltage for the longer fiber
- `L1` = length of the shorter fiber
- `L2` = length of the longer fiber

### OUTPUT
<img width="744" height="696" alt="Screenshot (329)" src="https://github.com/user-attachments/assets/c890e8a0-abf0-414e-b2be-a0fdd46325c7" />

### TABULATION

<img width="898" height="1437" alt="WhatsApp Image 2026-10-15 at 2 42 04 PM" src="https://github.com/user-attachments/assets/f0934b20-c2af-49ba-ab3d-832e8fcb2f98" />


### RESULT 



