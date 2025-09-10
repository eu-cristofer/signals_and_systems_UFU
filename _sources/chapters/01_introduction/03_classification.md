# Signal and System Classification

## Overview

This section provides a comprehensive classification framework for signals and systems, building upon the fundamental concepts introduced in the previous sections.

## Signal Classification

### By Time Domain Properties

#### Continuous-time vs Discrete-time
- **Continuous-time signals**: Defined for all values of time in a continuous interval
- **Discrete-time signals**: Defined only at discrete time instants

#### Periodic vs Aperiodic
- **Periodic signals**: Repeat themselves after a fixed time interval
- **Aperiodic signals**: Do not repeat themselves

#### Even vs Odd
- **Even signals**: Satisfy x(t) = x(-t)
- **Odd signals**: Satisfy x(t) = -x(-t)

### By Amplitude Properties

#### Analog vs Digital
- **Analog signals**: Continuous in both time and amplitude
- **Digital signals**: Discrete in both time and amplitude

#### Energy vs Power Signals
- **Energy signals**: Have finite energy and zero average power
- **Power signals**: Have finite average power and infinite energy

## System Classification

### By Linearity
- **Linear systems**: Satisfy the principle of superposition
- **Nonlinear systems**: Do not satisfy superposition

### By Time Invariance
- **Time-invariant systems**: System properties do not change with time
- **Time-varying systems**: System properties change with time

### By Causality
- **Causal systems**: Output depends only on present and past inputs
- **Non-causal systems**: Output may depend on future inputs

### By Memory
- **Memoryless systems**: Output depends only on current input
- **Systems with memory**: Output depends on past and/or future inputs

## Interactive Classification Examples

```{code-cell} python
import numpy as np
import matplotlib.pyplot as plt

# Example 1: Even and Odd Signal Decomposition
def classify_signal_properties():
    """Demonstrate signal classification"""
    t = np.linspace(-2, 2, 1000)
    
    # Original signal
    x = t**3 + t**2 + t + 1
    
    # Even component
    x_even = 0.5 * (x + np.flip(x))
    
    # Odd component  
    x_odd = 0.5 * (x - np.flip(x))
    
    # Plot
    fig, axes = plt.subplots(2, 2, figsize=(12, 8))
    
    axes[0,0].plot(t, x, 'b-', linewidth=2)
    axes[0,0].set_title('Original Signal x(t)')
    axes[0,0].grid(True)
    
    axes[0,1].plot(t, x_even, 'r-', linewidth=2)
    axes[0,1].set_title('Even Component')
    axes[0,1].grid(True)
    
    axes[1,0].plot(t, x_odd, 'g-', linewidth=2)
    axes[1,0].set_title('Odd Component')
    axes[1,0].grid(True)
    
    axes[1,1].plot(t, x_even + x_odd, 'm-', linewidth=2)
    axes[1,1].set_title('Reconstructed Signal')
    axes[1,1].grid(True)
    
    plt.tight_layout()
    plt.show()

classify_signal_properties()
```

## Summary

Understanding signal and system classification is fundamental to:
- Choosing appropriate analysis techniques
- Designing effective systems
- Predicting system behavior
- Optimizing signal processing algorithms

The classification framework provides a systematic approach to analyzing and designing signals and systems in various applications.
