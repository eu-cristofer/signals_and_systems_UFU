# Mathematical Review

This appendix provides a review of essential mathematical concepts used throughout the signals and systems course.

## Complex Numbers

### Definition
A complex number $z$ can be written in rectangular form as:
```{math}
z = x + jy
```
where $x$ is the real part, $y$ is the imaginary part, and $j = \sqrt{-1}$.

### Polar Form
```{math}
z = r e^{j\theta} = r(\cos\theta + j\sin\theta)
```
where:
- $r = |z| = \sqrt{x^2 + y^2}$ (magnitude)
- $\theta = \angle z = \arctan(y/x)$ (phase)

### Euler's Formula
```{math}
e^{j\theta} = \cos\theta + j\sin\theta
```

### Properties
- $|z_1 z_2| = |z_1| |z_2|$
- $\angle(z_1 z_2) = \angle z_1 + \angle z_2$
- $z^* = x - jy$ (complex conjugate)
- $|z|^2 = z z^*$

## Calculus

### Derivatives
- $\frac{d}{dt}[e^{at}] = ae^{at}$
- $\frac{d}{dt}[\sin(\omega t)] = \omega\cos(\omega t)$
- $\frac{d}{dt}[\cos(\omega t)] = -\omega\sin(\omega t)$
- Product rule: $\frac{d}{dt}[f(t)g(t)] = f'(t)g(t) + f(t)g'(t)$
- Chain rule: $\frac{d}{dt}[f(g(t))] = f'(g(t))g'(t)$

### Integrals
- $\int e^{at} dt = \frac{1}{a}e^{at} + C$
- $\int \sin(\omega t) dt = -\frac{1}{\omega}\cos(\omega t) + C$
- $\int \cos(\omega t) dt = \frac{1}{\omega}\sin(\omega t) + C$
- Integration by parts: $\int u dv = uv - \int v du$

### Definite Integrals
- $\int_0^{\infty} e^{-at} dt = \frac{1}{a}$ (for $a > 0$)
- $\int_{-\infty}^{\infty} e^{-t^2} dt = \sqrt{\pi}$

## Linear Algebra

### Vectors
A vector $\mathbf{v} = [v_1, v_2, \ldots, v_n]^T$ has:
- **Norm**: $||\mathbf{v}|| = \sqrt{v_1^2 + v_2^2 + \cdots + v_n^2}$
- **Dot product**: $\mathbf{u} \cdot \mathbf{v} = \sum_{i=1}^n u_i v_i$

### Matrices
For matrix $\mathbf{A} = [a_{ij}]$:
- **Transpose**: $\mathbf{A}^T = [a_{ji}]$
- **Determinant**: For 2×2: $\det(\mathbf{A}) = a_{11}a_{22} - a_{12}a_{21}$
- **Inverse**: $\mathbf{A}^{-1} = \frac{1}{\det(\mathbf{A})}\begin{bmatrix} a_{22} & -a_{12} \\ -a_{21} & a_{11} \end{bmatrix}$

### Eigenvalues and Eigenvectors
For matrix $\mathbf{A}$, eigenvalues $\lambda$ satisfy:
```{math}
\mathbf{A}\mathbf{v} = \lambda\mathbf{v}
```
where $\mathbf{v}$ is the corresponding eigenvector.

## Series and Summations

### Geometric Series
```{math}
\sum_{n=0}^{N-1} r^n = \frac{1-r^N}{1-r} \quad \text{for } r \neq 1
```

```{math}
\sum_{n=0}^{\infty} r^n = \frac{1}{1-r} \quad \text{for } |r| < 1
```

### Arithmetic Series
```{math}
\sum_{n=1}^N n = \frac{N(N+1)}{2}
```

### Trigonometric Identities
- $\sin^2\theta + \cos^2\theta = 1$
- $\sin(A \pm B) = \sin A \cos B \pm \cos A \sin B$
- $\cos(A \pm B) = \cos A \cos B \mp \sin A \sin B$
- $\sin A \sin B = \frac{1}{2}[\cos(A-B) - \cos(A+B)]$
- $\cos A \cos B = \frac{1}{2}[\cos(A-B) + \cos(A+B)]$

## Differential Equations

### First-Order Linear
```{math}
\frac{dy}{dt} + ay = x(t)
```
Solution: $y(t) = e^{-at}\int e^{at}x(t)dt + Ce^{-at}$

### Second-Order Linear
```{math}
\frac{d^2y}{dt^2} + a\frac{dy}{dt} + by = x(t)
```
Characteristic equation: $s^2 + as + b = 0$

## Fourier Series

### Trigonometric Form
```{math}
f(t) = a_0 + \sum_{n=1}^{\infty} [a_n\cos(n\omega_0 t) + b_n\sin(n\omega_0 t)]
```

### Exponential Form
```{math}
f(t) = \sum_{n=-\infty}^{\infty} c_n e^{jn\omega_0 t}
```

### Coefficients
```{math}
c_n = \frac{1}{T} \int_{-T/2}^{T/2} f(t) e^{-jn\omega_0 t} dt
```

## Probability and Statistics

### Mean and Variance
For random variable $X$:
- **Mean**: $\mu = E[X]$
- **Variance**: $\sigma^2 = E[(X-\mu)^2] = E[X^2] - \mu^2$

### Gaussian Distribution
```{math}
f(x) = \frac{1}{\sigma\sqrt{2\pi}} e^{-\frac{(x-\mu)^2}{2\sigma^2}}
```

## Useful Approximations

### Small Angle Approximation
- $\sin\theta \approx \theta$ (for small $\theta$)
- $\cos\theta \approx 1 - \frac{\theta^2}{2}$ (for small $\theta$)

### Taylor Series
- $e^x = 1 + x + \frac{x^2}{2!} + \frac{x^3}{3!} + \cdots$
- $\sin x = x - \frac{x^3}{3!} + \frac{x^5}{5!} - \cdots$
- $\cos x = 1 - \frac{x^2}{2!} + \frac{x^4}{4!} - \cdots$

## Interactive Examples

Let's explore some of these concepts with Python:

```{code-cell} python
import numpy as np
import matplotlib.pyplot as plt

# Complex numbers
z1 = 3 + 4j
z2 = 2 * np.exp(1j * np.pi/4)

print(f"z1 = {z1}")
print(f"|z1| = {abs(z1)}")
print(f"∠z1 = {np.angle(z1):.3f} radians")
print(f"z1* = {z1.conjugate()}")

# Euler's formula demonstration
theta = np.linspace(0, 2*np.pi, 100)
euler_real = np.cos(theta)
euler_imag = np.sin(theta)

plt.figure(figsize=(10, 4))

plt.subplot(1, 2, 1)
plt.plot(theta, euler_real, 'b-', label='cos(θ)')
plt.plot(theta, euler_imag, 'r-', label='sin(θ)')
plt.xlabel('θ (radians)')
plt.ylabel('Amplitude')
plt.title('Euler\'s Formula Components')
plt.legend()
plt.grid(True)

plt.subplot(1, 2, 2)
plt.plot(euler_real, euler_imag, 'g-', linewidth=2)
plt.xlabel('Real part')
plt.ylabel('Imaginary part')
plt.title('Unit Circle: e^(jθ)')
plt.axis('equal')
plt.grid(True)

plt.tight_layout()
plt.show()

# Geometric series
r = 0.5
N = 10
geometric_sum = sum(r**n for n in range(N))
theoretical_sum = (1 - r**N) / (1 - r)

print(f"\nGeometric series with r={r}, N={N}:")
print(f"Calculated sum: {geometric_sum:.6f}")
print(f"Theoretical sum: {theoretical_sum:.6f}")
```

This mathematical foundation will be essential for understanding the concepts presented throughout the signals and systems course.
