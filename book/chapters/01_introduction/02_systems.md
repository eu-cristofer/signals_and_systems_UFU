# Systems

## Definition of Systems

A **system** is a physical device or algorithm that operates on an input signal to produce an output signal. Mathematically, a system can be represented as:

```{math}
y(t) = T[x(t)]
```

where:
- $x(t)$ is the input signal
- $y(t)$ is the output signal  
- $T[\cdot]$ represents the system transformation

## System Properties

### Linearity

A system is **linear** if it satisfies the principle of superposition:

```{math}
T[a_1 x_1(t) + a_2 x_2(t)] = a_1 T[x_1(t)] + a_2 T[x_2(t)]
```

### Time Invariance

A system is **time-invariant** if a time shift in the input results in the same time shift in the output:

```{math}
\text{If } y(t) = T[x(t)], \text{ then } y(t - t_0) = T[x(t - t_0)]
```

### Causality

A system is **causal** if the output at any time depends only on the input at the present and past times:

```{math}
y(t) \text{ depends only on } x(\tau) \text{ for } \tau \leq t
```

### Stability

A system is **stable** if every bounded input produces a bounded output (BIBO stability):

```{math}
|x(t)| \leq M \text{ for all } t \Rightarrow |y(t)| \leq N \text{ for all } t
```

### Memory

- **Memoryless**: Output depends only on the current input
- **With memory**: Output depends on past and/or future inputs

## Linear Time-Invariant (LTI) Systems

LTI systems are particularly important because they have special properties that make analysis easier. For LTI systems:

1. The output can be expressed as the convolution of the input with the impulse response
2. Frequency domain analysis is straightforward
3. Many analysis tools (Fourier, Laplace, Z-transforms) are applicable

## Impulse Response

The **impulse response** $h(t)$ of a system is the output when the input is a unit impulse $\delta(t)$:

```{math}
h(t) = T[\delta(t)]
```

For LTI systems, the impulse response completely characterizes the system.

## Convolution

For LTI systems, the output is given by the convolution integral:

```{math}
y(t) = x(t) * h(t) = \int_{-\infty}^{\infty} x(\tau) h(t - \tau) \, d\tau
```

## Interactive Examples

Let's explore system properties with Python:

```{code-cell} python
import numpy as np
import matplotlib.pyplot as plt
from scipy import signal

# Define a simple LTI system: y(t) = x(t) + 0.5*x(t-1)
def simple_lti_system(x, dt):
    """Simple LTI system with delay and scaling"""
    y = np.zeros_like(x)
    delay_samples = int(1.0 / dt)  # 1 second delay
    
    for i in range(len(x)):
        y[i] = x[i]  # Current input
        if i >= delay_samples:
            y[i] += 0.5 * x[i - delay_samples]  # Delayed input
    
    return y

# Time vector
dt = 0.01
t = np.arange(0, 5, dt)

# Test signals
x1 = np.sin(2 * np.pi * t)  # Sinusoid
x2 = np.exp(-t) * (t >= 0)  # Exponential decay
x3 = np.where((t >= 1) & (t <= 2), 1, 0)  # Rectangular pulse

# Apply system to each input
y1 = simple_lti_system(x1, dt)
y2 = simple_lti_system(x2, dt)
y3 = simple_lti_system(x3, dt)

# Test linearity: y(a*x1 + b*x2) = a*y(x1) + b*y(x2)
a, b = 2, 3
x_combined = a * x1 + b * x2
y_combined = simple_lti_system(x_combined, dt)
y_linear_combination = a * y1 + b * y2

# Plot results
fig, axes = plt.subplots(3, 2, figsize=(15, 12))

# Input signals
axes[0,0].plot(t, x1, 'b-', label='x₁(t) = sin(2πt)', linewidth=2)
axes[0,0].plot(t, x2, 'r-', label='x₂(t) = e⁻ᵗu(t)', linewidth=2)
axes[0,0].set_title('Input Signals')
axes[0,0].legend()
axes[0,0].grid(True)
axes[0,0].set_xlabel('Time (s)')
axes[0,0].set_ylabel('Amplitude')

# Output signals
axes[0,1].plot(t, y1, 'b-', label='y₁(t)', linewidth=2)
axes[0,1].plot(t, y2, 'r-', label='y₂(t)', linewidth=2)
axes[0,1].set_title('Output Signals')
axes[0,1].legend()
axes[0,1].grid(True)
axes[0,1].set_xlabel('Time (s)')
axes[0,1].set_ylabel('Amplitude')

# Linearity test
axes[1,0].plot(t, x_combined, 'g-', label='a·x₁ + b·x₂', linewidth=2)
axes[1,0].set_title('Combined Input: a·x₁ + b·x₂')
axes[1,0].legend()
axes[1,0].grid(True)
axes[1,0].set_xlabel('Time (s)')
axes[1,0].set_ylabel('Amplitude')

axes[1,1].plot(t, y_combined, 'g-', label='T[a·x₁ + b·x₂]', linewidth=2)
axes[1,1].plot(t, y_linear_combination, 'm--', label='a·y₁ + b·y₂', linewidth=2)
axes[1,1].set_title('Linearity Test')
axes[1,1].legend()
axes[1,1].grid(True)
axes[1,1].set_xlabel('Time (s)')
axes[1,1].set_ylabel('Amplitude')

# Impulse response
impulse = np.where(np.abs(t - 1) < dt/2, 1/dt, 0)  # Approximate impulse
h = simple_lti_system(impulse, dt)

axes[2,0].plot(t, impulse, 'k-', label='δ(t)', linewidth=2)
axes[2,0].set_title('Input: Unit Impulse')
axes[2,0].legend()
axes[2,0].grid(True)
axes[2,0].set_xlabel('Time (s)')
axes[2,0].set_ylabel('Amplitude')

axes[2,1].plot(t, h, 'k-', label='h(t)', linewidth=2)
axes[2,1].set_title('Impulse Response')
axes[2,1].legend()
axes[2,1].grid(True)
axes[2,1].set_xlabel('Time (s)')
axes[2,1].set_ylabel('Amplitude')

plt.tight_layout()
plt.show()

# Verify linearity
linearity_error = np.max(np.abs(y_combined - y_linear_combination))
print(f"Linearity test error: {linearity_error:.2e}")
print("System is linear!" if linearity_error < 1e-10 else "System is not linear!")
```

## System Interconnections

### Series (Cascade) Connection

```{math}
y(t) = T_2[T_1[x(t)]]
```

### Parallel Connection

```{math}
y(t) = T_1[x(t)] + T_2[x(t)]
```

### Feedback Connection

```{math}
y(t) = T_1[x(t) - T_2[y(t)]]
```

## Differential and Difference Equations

Many physical systems can be described by differential equations (continuous-time) or difference equations (discrete-time).

### Continuous-time LTI Systems

```{math}
\sum_{k=0}^N a_k \frac{d^k y(t)}{dt^k} = \sum_{k=0}^M b_k \frac{d^k x(t)}{dt^k}
```

### Discrete-time LTI Systems

```{math}
\sum_{k=0}^N a_k y[n-k] = \sum_{k=0}^M b_k x[n-k]
```

## Summary

In this section, we've covered:

- Basic definitions and properties of systems
- Linear Time-Invariant (LTI) systems and their importance
- System properties: linearity, time-invariance, causality, stability
- Impulse response and convolution
- System interconnections
- Mathematical representations using differential/difference equations

These concepts form the foundation for analyzing and designing systems in both time and frequency domains.
