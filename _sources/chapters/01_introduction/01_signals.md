# Signals

## Definition of Signals

A **signal** is a function that carries information about a physical phenomenon. In the context of signals and systems, we typically deal with signals that vary with time.

Mathematically, a signal can be represented as:

```{math}
x(t) \quad \text{for continuous-time signals}
```

```{math}
x[n] \quad \text{for discrete-time signals}
```

where:
- $t$ is a continuous variable (time)
- $n$ is a discrete variable (sample number)

## Classification of Signals

### Continuous-time vs Discrete-time

**Continuous-time signals** are defined for all values of time $t$ in a continuous interval.

**Discrete-time signals** are defined only at discrete time instants, typically at regular intervals.

### Analog vs Digital

- **Analog signals**: Continuous in both time and amplitude
- **Digital signals**: Discrete in both time and amplitude

### Periodic vs Aperiodic

A signal $x(t)$ is **periodic** if there exists a positive constant $T$ such that:

```{math}
x(t) = x(t + T) \quad \text{for all } t
```

The smallest such $T$ is called the **fundamental period**.

### Even vs Odd

A signal is **even** if:
```{math}
x(t) = x(-t)
```

A signal is **odd** if:
```{math}
x(t) = -x(-t)
```

## Common Signals

### Unit Step Function

```{math}
u(t) = \begin{cases}
1 & \text{if } t \geq 0 \\
0 & \text{if } t < 0
\end{cases}
```

### Unit Impulse Function (Dirac Delta)

```{math}
\delta(t) = \begin{cases}
\infty & \text{if } t = 0 \\
0 & \text{if } t \neq 0
\end{cases}
```

with the property:
```{math}
\int_{-\infty}^{\infty} \delta(t) \, dt = 1
```

### Sinusoidal Signals

```{math}
x(t) = A \cos(\omega t + \phi)
```

where:
- $A$ is the amplitude
- $\omega$ is the angular frequency (rad/s)
- $\phi$ is the phase (rad)

## Interactive Examples

Let's explore some of these signals using Python:

```{code-cell} python
import numpy as np
import matplotlib.pyplot as plt

# Time vector
t = np.linspace(-2, 2, 1000)

# Unit step function
def unit_step(t):
    return np.where(t >= 0, 1, 0)

# Unit impulse approximation
def unit_impulse(t, width=0.1):
    return np.where(np.abs(t) <= width/2, 1/width, 0)

# Sinusoidal signal
def sinusoidal(t, A=1, omega=2*np.pi, phi=0):
    return A * np.cos(omega * t + phi)

# Plot the signals
fig, axes = plt.subplots(2, 2, figsize=(12, 8))

# Unit step
axes[0,0].plot(t, unit_step(t), 'b-', linewidth=2)
axes[0,0].set_title('Unit Step Function u(t)')
axes[0,0].grid(True)
axes[0,0].set_xlabel('Time (s)')
axes[0,0].set_ylabel('Amplitude')

# Unit impulse
axes[0,1].plot(t, unit_impulse(t), 'r-', linewidth=2)
axes[0,1].set_title('Unit Impulse Function δ(t)')
axes[0,1].grid(True)
axes[0,1].set_xlabel('Time (s)')
axes[0,1].set_ylabel('Amplitude')

# Sinusoidal signal
axes[1,0].plot(t, sinusoidal(t), 'g-', linewidth=2)
axes[1,0].set_title('Sinusoidal Signal')
axes[1,0].grid(True)
axes[1,0].set_xlabel('Time (s)')
axes[1,0].set_ylabel('Amplitude')

# Even and odd components
x_even = 0.5 * (sinusoidal(t) + sinusoidal(-t))
x_odd = 0.5 * (sinusoidal(t) - sinusoidal(-t))

axes[1,1].plot(t, x_even, 'b-', label='Even component', linewidth=2)
axes[1,1].plot(t, x_odd, 'r-', label='Odd component', linewidth=2)
axes[1,1].set_title('Even and Odd Components')
axes[1,1].legend()
axes[1,1].grid(True)
axes[1,1].set_xlabel('Time (s)')
axes[1,1].set_ylabel('Amplitude')

plt.tight_layout()
plt.show()
```

## Energy and Power

For a signal $x(t)$, we define:

**Energy**:
```{math}
E = \int_{-\infty}^{\infty} |x(t)|^2 \, dt
```

**Power** (for periodic signals):
```{math}
P = \frac{1}{T} \int_0^T |x(t)|^2 \, dt
```

A signal is called:
- **Energy signal** if $E < \infty$ and $P = 0$
- **Power signal** if $P < \infty$ and $E = \infty$

## Summary

In this section, we've covered:

- Basic definitions of signals
- Classification schemes for signals
- Common signal types and their mathematical representations
- Energy and power concepts
- Interactive examples using Python

These fundamental concepts will be essential as we move forward to study systems and their analysis.
