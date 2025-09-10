# Exercises - Chapter 1: Introduction to Signals and Systems

## Exercise 1.1: Signal Classification

Classify the following signals as continuous-time or discrete-time, periodic or aperiodic, even or odd:

1. $x(t) = \sin(2\pi t)$
2. $x[n] = \cos(\frac{\pi n}{4})$
3. $x(t) = e^{-t}u(t)$
4. $x(t) = t^2$
5. $x[n] = (-1)^n$

## Exercise 1.2: Signal Properties

For the signal $x(t) = A\cos(\omega t + \phi)$:

1. Find the period $T$
2. Determine if it's an energy or power signal
3. Calculate the average power
4. Find the even and odd components

## Exercise 1.3: System Properties

Determine which of the following systems are linear, time-invariant, causal, and stable:

1. $y(t) = x(t-2)$
2. $y(t) = x^2(t)$
3. $y(t) = tx(t)$
4. $y(t) = \int_{-\infty}^t x(\tau) d\tau$
5. $y[n] = x[n] + x[n-1]$

## Exercise 1.4: Impulse Response

Find the impulse response of the following systems:

1. $y(t) = x(t-1)$
2. $y(t) = \int_{-\infty}^t x(\tau) d\tau$
3. $y[n] = x[n] - x[n-1]$

## Exercise 1.5: Convolution

Compute the convolution $y(t) = x(t) * h(t)$ for:

1. $x(t) = u(t)$ and $h(t) = e^{-t}u(t)$
2. $x(t) = \delta(t-1)$ and $h(t) = u(t)$
3. $x[n] = u[n]$ and $h[n] = a^n u[n]$ where $|a| < 1$

## Exercise 1.6: System Interconnections

For the system shown below, find the overall impulse response:

```
x(t) → [h₁(t)] → [h₂(t)] → y(t)
```

where $h_1(t) = \delta(t-1)$ and $h_2(t) = e^{-t}u(t)$.

## Exercise 1.7: MATLAB/Python Implementation

Implement the following in Python or MATLAB:

1. Generate and plot a unit step function
2. Generate and plot a unit impulse function (approximation)
3. Implement a simple LTI system: $y[n] = 0.5x[n] + 0.3x[n-1]$
4. Test the linearity of the system from part 3

## Exercise 1.8: Energy and Power

Calculate the energy and power for the following signals:

1. $x(t) = e^{-2t}u(t)$
2. $x(t) = \cos(2\pi t)$
3. $x[n] = \sin(\frac{\pi n}{4})$

## Exercise 1.9: Signal Decomposition

Decompose the following signals into their even and odd components:

1. $x(t) = t^3 + t^2 + t + 1$
2. $x(t) = e^{-t}u(t)$
3. $x[n] = n^2$

## Exercise 1.10: System Analysis

Consider the system described by the differential equation:

$$\frac{dy(t)}{dt} + 2y(t) = x(t)$$

1. Find the impulse response
2. Determine if the system is stable
3. Find the step response
4. Calculate the output for input $x(t) = e^{-t}u(t)$

## Solutions

```{admonition} Note
Solutions will be provided in a separate solutions file. Try to solve the problems first before checking the answers!
```

## Additional Resources

- Practice with MATLAB Signal Processing Toolbox
- Explore Python's scipy.signal module
- Review complex number operations
- Study basic calculus and linear algebra concepts
