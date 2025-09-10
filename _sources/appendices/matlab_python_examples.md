# MATLAB and Python Examples

This appendix provides practical examples comparing MATLAB and Python implementations for common signal processing tasks.

## Environment Setup

### Python Setup
```python
import numpy as np
import matplotlib.pyplot as plt
import scipy.signal as signal
from scipy.fft import fft, fftfreq
```

### MATLAB Setup
```matlab
% Clear workspace and close all figures
clear all; close all; clc;

% Add signal processing toolbox to path
addpath(genpath('signal_processing_toolbox'));
```

## Signal Generation

### Unit Step Function

**Python:**
```python
def unit_step(t):
    """Generate unit step function"""
    return np.where(t >= 0, 1, 0)

# Example usage
t = np.linspace(-2, 2, 1000)
u = unit_step(t)
plt.plot(t, u)
plt.title('Unit Step Function')
plt.xlabel('Time (s)')
plt.ylabel('Amplitude')
plt.grid(True)
plt.show()
```

**MATLAB:**
```matlab
% Generate unit step function
t = linspace(-2, 2, 1000);
u = heaviside(t);  % or u = t >= 0;

% Plot
figure;
plot(t, u, 'b-', 'LineWidth', 2);
title('Unit Step Function');
xlabel('Time (s)');
ylabel('Amplitude');
grid on;
```

### Sinusoidal Signals

**Python:**
```python
def generate_sinusoid(t, A=1, f=1, phi=0):
    """Generate sinusoidal signal"""
    return A * np.sin(2 * np.pi * f * t + phi)

# Example
t = np.linspace(0, 2, 1000)
x = generate_sinusoid(t, A=2, f=2, phi=np.pi/4)
```

**MATLAB:**
```matlab
% Generate sinusoidal signal
t = linspace(0, 2, 1000);
A = 2; f = 2; phi = pi/4;
x = A * sin(2*pi*f*t + phi);
```

## System Analysis

### Impulse Response

**Python:**
```python
def find_impulse_response(system_coeffs, input_coeffs, t):
    """Find impulse response of LTI system"""
    # For system: a*y'' + b*y' + c*y = d*x' + e*x
    a, b, c = system_coeffs
    d, e = input_coeffs
    
    # Create system
    num = [d, e]
    den = [a, b, c]
    system = signal.TransferFunction(num, den)
    
    # Find impulse response
    t_imp, h = signal.impulse(system, T=t)
    return t_imp, h

# Example: y'' + 3y' + 2y = x' + x
t = np.linspace(0, 10, 1000)
t_imp, h = find_impulse_response([1, 3, 2], [1, 1], t)
```

**MATLAB:**
```matlab
% Define system: y'' + 3y' + 2y = x' + x
num = [1, 1];  % coefficients of x terms
den = [1, 3, 2];  % coefficients of y terms
sys = tf(num, den);

% Find impulse response
t = linspace(0, 10, 1000);
[h, t_imp] = impulse(sys, t);
```

### Convolution

**Python:**
```python
def convolution_example():
    """Demonstrate convolution operation"""
    # Define signals
    t = np.linspace(0, 5, 1000)
    x = np.exp(-t) * (t >= 0)  # Exponential decay
    h = np.sin(2*np.pi*t) * (t >= 0) * (t <= 1)  # Sinusoidal pulse
    
    # Compute convolution
    y = np.convolve(x, h, mode='same') * (t[1] - t[0])
    
    # Plot
    fig, axes = plt.subplots(3, 1, figsize=(10, 8))
    axes[0].plot(t, x, 'b-', label='x(t)')
    axes[0].set_title('Input Signal')
    axes[0].legend()
    axes[0].grid(True)
    
    axes[1].plot(t, h, 'r-', label='h(t)')
    axes[1].set_title('Impulse Response')
    axes[1].legend()
    axes[1].grid(True)
    
    axes[2].plot(t, y, 'g-', label='y(t) = x(t) * h(t)')
    axes[2].set_title('Output Signal (Convolution)')
    axes[2].legend()
    axes[2].grid(True)
    
    plt.tight_layout()
    plt.show()

convolution_example()
```

**MATLAB:**
```matlab
% Define signals
t = linspace(0, 5, 1000);
x = exp(-t) .* (t >= 0);  % Exponential decay
h = sin(2*pi*t) .* (t >= 0) .* (t <= 1);  % Sinusoidal pulse

% Compute convolution
y = conv(x, h, 'same') * (t(2) - t(1));

% Plot
figure;
subplot(3,1,1);
plot(t, x, 'b-', 'LineWidth', 2);
title('Input Signal');
legend('x(t)');
grid on;

subplot(3,1,2);
plot(t, h, 'r-', 'LineWidth', 2);
title('Impulse Response');
legend('h(t)');
grid on;

subplot(3,1,3);
plot(t, y, 'g-', 'LineWidth', 2);
title('Output Signal (Convolution)');
legend('y(t) = x(t) * h(t)');
grid on;
```

## Frequency Domain Analysis

### Fourier Transform

**Python:**
```python
def fourier_analysis_example():
    """Demonstrate Fourier transform analysis"""
    # Generate signal
    fs = 1000  # Sampling frequency
    t = np.arange(0, 1, 1/fs)
    f1, f2 = 50, 120  # Frequencies
    x = np.sin(2*np.pi*f1*t) + 0.5*np.sin(2*np.pi*f2*t)
    
    # Compute FFT
    X = fft(x)
    freqs = fftfreq(len(x), 1/fs)
    
    # Plot
    fig, axes = plt.subplots(2, 1, figsize=(10, 6))
    
    # Time domain
    axes[0].plot(t[:200], x[:200], 'b-')
    axes[0].set_title('Time Domain Signal')
    axes[0].set_xlabel('Time (s)')
    axes[0].set_ylabel('Amplitude')
    axes[0].grid(True)
    
    # Frequency domain
    axes[1].plot(freqs[:len(freqs)//2], np.abs(X[:len(X)//2]), 'r-')
    axes[1].set_title('Frequency Domain (Magnitude)')
    axes[1].set_xlabel('Frequency (Hz)')
    axes[1].set_ylabel('Magnitude')
    axes[1].grid(True)
    
    plt.tight_layout()
    plt.show()

fourier_analysis_example()
```

**MATLAB:**
```matlab
% Generate signal
fs = 1000;  % Sampling frequency
t = 0:1/fs:1-1/fs;
f1 = 50; f2 = 120;  % Frequencies
x = sin(2*pi*f1*t) + 0.5*sin(2*pi*f2*t);

% Compute FFT
X = fft(x);
freqs = (0:length(x)-1) * fs / length(x);

% Plot
figure;
subplot(2,1,1);
plot(t(1:200), x(1:200), 'b-', 'LineWidth', 2);
title('Time Domain Signal');
xlabel('Time (s)');
ylabel('Amplitude');
grid on;

subplot(2,1,2);
plot(freqs(1:length(freqs)/2), abs(X(1:length(X)/2)), 'r-', 'LineWidth', 2);
title('Frequency Domain (Magnitude)');
xlabel('Frequency (Hz)');
ylabel('Magnitude');
grid on;
```

## Filter Design

### Low-pass Filter

**Python:**
```python
def design_lowpass_filter():
    """Design and test a low-pass filter"""
    # Design Butterworth low-pass filter
    order = 4
    cutoff_freq = 0.1  # Normalized frequency
    b, a = signal.butter(order, cutoff_freq, btype='low')
    
    # Generate test signal
    t = np.linspace(0, 10, 1000)
    x = np.sin(2*np.pi*0.05*t) + 0.5*np.sin(2*np.pi*0.3*t)
    
    # Apply filter
    y = signal.filtfilt(b, a, x)
    
    # Plot
    fig, axes = plt.subplots(2, 1, figsize=(10, 6))
    
    axes[0].plot(t, x, 'b-', label='Input')
    axes[0].plot(t, y, 'r-', label='Filtered')
    axes[0].set_title('Filtered Signal')
    axes[0].legend()
    axes[0].grid(True)
    
    # Frequency response
    w, h = signal.freqz(b, a, worN=8000)
    axes[1].plot(w/np.pi, 20*np.log10(np.abs(h)))
    axes[1].set_title('Filter Frequency Response')
    axes[1].set_xlabel('Normalized Frequency')
    axes[1].set_ylabel('Magnitude (dB)')
    axes[1].grid(True)
    
    plt.tight_layout()
    plt.show()

design_lowpass_filter()
```

**MATLAB:**
```matlab
% Design Butterworth low-pass filter
order = 4;
cutoff_freq = 0.1;  % Normalized frequency
[b, a] = butter(order, cutoff_freq, 'low');

% Generate test signal
t = linspace(0, 10, 1000);
x = sin(2*pi*0.05*t) + 0.5*sin(2*pi*0.3*t);

% Apply filter
y = filtfilt(b, a, x);

% Plot
figure;
subplot(2,1,1);
plot(t, x, 'b-', 'LineWidth', 2);
hold on;
plot(t, y, 'r-', 'LineWidth', 2);
title('Filtered Signal');
legend('Input', 'Filtered');
grid on;

% Frequency response
subplot(2,1,2);
freqz(b, a);
title('Filter Frequency Response');
```

## Performance Comparison

### Execution Time Comparison

**Python:**
```python
import time

def performance_test():
    """Compare execution times for different operations"""
    n = 10000
    
    # FFT performance
    x = np.random.randn(n)
    start_time = time.time()
    X = fft(x)
    fft_time = time.time() - start_time
    
    # Convolution performance
    h = np.random.randn(100)
    start_time = time.time()
    y = np.convolve(x, h, mode='same')
    conv_time = time.time() - start_time
    
    print(f"FFT time: {fft_time:.4f} seconds")
    print(f"Convolution time: {conv_time:.4f} seconds")

performance_test()
```

**MATLAB:**
```matlab
% Performance test
n = 10000;

% FFT performance
x = randn(n, 1);
tic;
X = fft(x);
fft_time = toc;

% Convolution performance
h = randn(100, 1);
tic;
y = conv(x, h, 'same');
conv_time = toc;

fprintf('FFT time: %.4f seconds\n', fft_time);
fprintf('Convolution time: %.4f seconds\n', conv_time);
```

## Best Practices

### Code Organization

**Python:**
```python
class SignalProcessor:
    """Signal processing class for organized code"""
    
    def __init__(self, fs=1000):
        self.fs = fs
    
    def generate_signal(self, duration, frequencies, amplitudes):
        """Generate multi-tone signal"""
        t = np.linspace(0, duration, int(duration * self.fs))
        signal = np.zeros_like(t)
        
        for freq, amp in zip(frequencies, amplitudes):
            signal += amp * np.sin(2 * np.pi * freq * t)
        
        return t, signal
    
    def apply_filter(self, signal, filter_type='low', cutoff=0.1):
        """Apply filter to signal"""
        b, a = signal.butter(4, cutoff, btype=filter_type)
        return signal.filtfilt(b, a, signal)

# Usage
processor = SignalProcessor(fs=1000)
t, x = processor.generate_signal(1, [50, 120], [1, 0.5])
y = processor.apply_filter(x, 'low', 0.1)
```

**MATLAB:**
```matlab
classdef SignalProcessor < handle
    properties
        fs
    end
    
    methods
        function obj = SignalProcessor(fs)
            if nargin < 1
                obj.fs = 1000;
            else
                obj.fs = fs;
            end
        end
        
        function [t, signal] = generate_signal(obj, duration, frequencies, amplitudes)
            t = linspace(0, duration, duration * obj.fs);
            signal = zeros(size(t));
            
            for i = 1:length(frequencies)
                signal = signal + amplitudes(i) * sin(2*pi*frequencies(i)*t);
            end
        end
        
        function filtered = apply_filter(obj, signal, filter_type, cutoff)
            [b, a] = butter(4, cutoff, filter_type);
            filtered = filtfilt(b, a, signal);
        end
    end
end

% Usage
processor = SignalProcessor(1000);
[t, x] = processor.generate_signal(1, [50, 120], [1, 0.5]);
y = processor.apply_filter(x, 'low', 0.1);
```

## Summary

Both MATLAB and Python offer powerful tools for signal processing:

- **MATLAB**: Excellent for rapid prototyping, built-in toolboxes, intuitive syntax
- **Python**: Free, extensive libraries, good for integration with other systems

Choose based on your specific needs, budget, and existing infrastructure.
