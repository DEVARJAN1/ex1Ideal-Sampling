## Exp:1 Ideal Sampling
21223060044
## Aim
To demonstrate the process of ideal sampling, where a continuous sinusoidal signal is sampled at a sufficient rate and accurately reconstructed without loss of information.

## Tools Required
- Python
- NumPy
- Matplotlib
- SciPy

## Program
```python
import numpy as np
import matplotlib.pyplot as plt
from scipy.signal import resample

# Define parameters
fs = 100  # Sampling frequency
t = np.arange(0, 1, 1/fs)  # Time vector
f = 5  # Frequency of the sine wave

# Generate continuous signal
signal = np.sin(2 * np.pi * f * t)
plt.figure(figsize=(10, 4))
plt.plot(t, signal, label='Continuous Signal')
plt.title('Continuous Signal (fs = 100 Hz)')
plt.xlabel('Time [s]')
plt.ylabel('Amplitude')
plt.grid(True)
plt.legend()
plt.show()

# Sampling process
t_sampled = np.arange(0, 1, 1/fs)
signal_sampled = np.sin(2 * np.pi * f * t_sampled)
plt.figure(figsize=(10, 4))
plt.plot(t, signal, label='Continuous Signal', alpha=0.7)
plt.stem(t_sampled, signal_sampled, linefmt='r-', markerfmt='ro', basefmt='r-', label='Sampled Signal (fs = 100 Hz)')
plt.title('Sampling of Continuous Signal (fs = 100 Hz)')
plt.xlabel('Time [s]')
plt.ylabel('Amplitude')
plt.grid(True)
plt.legend()
plt.show()

# Reconstruction process
reconstructed_signal = resample(signal_sampled, len(t))
plt.figure(figsize=(10, 4))
plt.plot(t, signal, label='Continuous Signal', alpha=0.7)
plt.plot(t, reconstructed_signal, 'r--', label='Reconstructed Signal (fs = 100 Hz)')
plt.title('Reconstruction of Sampled Signal (fs = 100 Hz)')
plt.xlabel('Time [s]')
plt.ylabel('Amplitude')
plt.grid(True)
plt.legend()
plt.show()`
```

## Output Waveform
![image](https://github.com/user-attachments/assets/0bdcdf6f-52a6-446b-acb4-73f2328fd8a0)


## Result
The original continuous sine wave was successfully sampled at 100 Hz.
The sampled signal was plotted using discrete red markers.
The signal was reconstructed using resampling techniques, closely matching the original signal.
