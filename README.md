## EX-4 -Delta-Modulation 
## LOKESH KUMAR.B_212223060139
##  Delta-Modulation using phyton 
 
## AIM
To perform Delta-Modulation using phyton 
## APPARATUS REQUIRED:
  Python 3.x
## PROGRAM
```
import numpy as np
import matplotlib.pyplot as plt

# Generate a sine wave signal
fs = 100  # Sampling frequency
t = np.arange(0, 1, 1/fs)  # Time vector
f = 5  # Frequency of sine wave
x = np.sin(2 * np.pi * f * t)  # Original signal

# Delta Modulation Parameters
delta = 0.1  # Step size
dm = []  # Delta modulated output (1s and 0s)
x_dm = [0]  # Step approximation

# Delta Modulation (Encoding)
for i in range(1, len(x)):
    if x[i] > x_dm[i - 1]:  # Compare with previous value
        dm.append(1)  # 1 for positive step
        x_dm.append(x_dm[i - 1] + delta)
    else:
        dm.append(0)  # 0 for negative step
        x_dm.append(x_dm[i - 1] - delta)

# Delta Demodulation (Decoding)
x_rec = [0]  # Reconstructed signal
for i in range(len(dm)):
    if dm[i] == 1:
        x_rec.append(x_rec[i] + delta)
    else:
        x_rec.append(x_rec[i] - delta)

# Plot results
plt.figure(figsize=(12, 6))

plt.subplot(3, 1, 1)
plt.plot(t, x, label="Original Signal", color='b')
plt.title("Original Signal")
plt.legend()

plt.subplot(3, 1, 2)
plt.step(t[:-1], x_dm[:-1], label="Delta Modulated Signal", color='r', where='post')
plt.title("Delta Modulated Signal (Step Approximation)")
plt.legend()

plt.subplot(3, 1, 3)
plt.plot(t, x_rec, label="Reconstructed Signal", color='g')
plt.title("Demodulated Signal (Reconstructed)")
plt.legend()

plt.tight_layout()
plt.show()

```
## PROGRAM WAVEFRONT
![image](https://github.com/user-attachments/assets/f70aeb00-e625-40e1-b823-1922e8672cb3)


## RESULT
  THUS THE DELTA MODULATION SIGNAL IS PERFORMED USING PHYTON 
