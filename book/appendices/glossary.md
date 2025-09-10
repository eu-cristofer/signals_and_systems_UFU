# Glossary

This glossary defines key terms used throughout the Signals and Systems course.

## A

**Aliasing** - A phenomenon that occurs when a signal is sampled at a rate lower than twice its highest frequency component, causing high-frequency components to appear as lower frequencies.

**Amplitude** - The magnitude or strength of a signal at any given time.

**Analog Signal** - A continuous signal that can take on any value within a continuous range.

**Aperiodic Signal** - A signal that does not repeat itself over time.

**Autocorrelation** - A measure of similarity between a signal and a time-shifted version of itself.

## B

**Bandwidth** - The range of frequencies over which a signal or system operates effectively.

**BIBO Stability** - Bounded Input, Bounded Output stability; a system is BIBO stable if every bounded input produces a bounded output.

**Butterworth Filter** - A type of filter with a maximally flat frequency response in the passband.

## C

**Causal System** - A system whose output at any time depends only on the input at the present and past times, not on future inputs.

**Chebyshev Filter** - A type of filter with equiripple behavior in either the passband or stopband.

**Circular Convolution** - Convolution performed in the frequency domain using the DFT, which assumes periodic extension of signals.

**Continuous-Time Signal** - A signal defined for all values of time in a continuous interval.

**Convolution** - A mathematical operation that describes how the shape of one function is modified by another function.

**Cutoff Frequency** - The frequency at which a filter's response drops to a specified level (typically -3 dB).

## D

**Decimation** - The process of reducing the sampling rate of a signal by an integer factor.

**Digital Signal** - A discrete signal that can take on only a finite number of values.

**Discrete-Time Signal** - A signal defined only at discrete time instants.

**Discrete Fourier Transform (DFT)** - A transform that converts a finite sequence of equally-spaced samples into a sequence of complex numbers representing the frequency domain.

**Discrete-Time Fourier Transform (DTFT)** - The Fourier transform of a discrete-time signal.

## E

**Energy Signal** - A signal with finite energy and zero average power.

**Even Signal** - A signal that satisfies x(t) = x(-t) for all t.

**Exponential Signal** - A signal of the form x(t) = Ae^(st) where A and s are complex constants.

## F

**Fast Fourier Transform (FFT)** - An efficient algorithm for computing the DFT.

**Filter** - A system that selectively passes or blocks certain frequency components of a signal.

**Fourier Series** - A representation of a periodic signal as a sum of sinusoidal components.

**Fourier Transform** - A transform that converts a time-domain signal into its frequency-domain representation.

**Frequency** - The number of cycles per unit time, measured in Hertz (Hz).

**Frequency Response** - The response of a system to sinusoidal inputs of different frequencies.

## G

**Group Delay** - The negative derivative of the phase response with respect to frequency.

## H

**Harmonic** - A frequency component that is an integer multiple of the fundamental frequency.

**High-pass Filter** - A filter that passes high frequencies and attenuates low frequencies.

**Homogeneous Solution** - The solution to a differential equation when the input is zero.

## I

**Impulse Response** - The output of a system when the input is a unit impulse function.

**Interpolation** - The process of increasing the sampling rate of a signal.

**Inverse Fourier Transform** - The transform that converts a frequency-domain signal back to the time domain.

**Inverse Laplace Transform** - The transform that converts a Laplace-domain signal back to the time domain.

**Inverse Z-Transform** - The transform that converts a Z-domain signal back to the time domain.

## L

**Laplace Transform** - A transform used for analyzing continuous-time systems, converting time-domain functions to the s-domain.

**Linear System** - A system that satisfies the principle of superposition.

**Linear Time-Invariant (LTI) System** - A system that is both linear and time-invariant.

**Low-pass Filter** - A filter that passes low frequencies and attenuates high frequencies.

## M

**Magnitude Response** - The absolute value of the frequency response of a system.

**Memoryless System** - A system whose output at any time depends only on the input at that same time.

**Modulation** - The process of varying a carrier signal with an information signal.

## N

**Nyquist Frequency** - Half the sampling frequency; the highest frequency that can be accurately represented in a sampled signal.

**Nyquist Rate** - The minimum sampling rate required to avoid aliasing, equal to twice the highest frequency component.

## O

**Odd Signal** - A signal that satisfies x(t) = -x(-t) for all t.

**Orthogonal** - Two signals are orthogonal if their inner product is zero.

## P

**Parseval's Theorem** - A theorem relating the energy in the time domain to the energy in the frequency domain.

**Passband** - The range of frequencies that a filter passes with minimal attenuation.

**Period** - The smallest positive value T for which a periodic signal repeats itself.

**Periodic Signal** - A signal that repeats itself after a fixed time interval.

**Phase** - The angular displacement of a sinusoidal signal relative to a reference.

**Phase Response** - The phase of the frequency response of a system.

**Power Signal** - A signal with finite average power and infinite energy.

**Pulse Width Modulation (PWM)** - A modulation technique where the width of pulses is varied to encode information.

## Q

**Quality Factor (Q)** - A measure of the sharpness of a resonant peak in a filter or system.

## R

**Reconstruction** - The process of recovering a continuous-time signal from its samples.

**Region of Convergence (ROC)** - The set of values for which a transform converges.

**Resonance** - The tendency of a system to oscillate at a particular frequency.

## S

**Sampling** - The process of converting a continuous-time signal to a discrete-time signal.

**Sampling Theorem** - A theorem stating that a signal can be perfectly reconstructed from its samples if the sampling rate is at least twice the highest frequency component.

**Signal** - A function that carries information about a physical phenomenon.

**Sinc Function** - The function sinc(x) = sin(πx)/(πx).

**Spectral Density** - A measure of the power or energy per unit frequency.

**Stability** - A property of a system indicating whether it produces bounded outputs for bounded inputs.

**Stopband** - The range of frequencies that a filter attenuates significantly.

**Superposition** - The principle that the response of a linear system to a sum of inputs is the sum of the responses to each input individually.

**System** - A physical device or algorithm that operates on an input signal to produce an output signal.

## T

**Time Constant** - A parameter characterizing the exponential decay or rise time of a system.

**Time Invariance** - A property of a system where a time shift in the input results in the same time shift in the output.

**Transfer Function** - The ratio of the Laplace transform of the output to the Laplace transform of the input.

**Transient Response** - The temporary response of a system before it reaches steady state.

## U

**Unit Impulse** - A signal with infinite amplitude at t=0 and zero elsewhere, with unit area.

**Unit Step** - A signal that is zero for t<0 and one for t≥0.

## W

**Windowing** - The process of multiplying a signal by a window function to reduce spectral leakage.

## Z

**Z-Transform** - A transform used for analyzing discrete-time systems, converting time-domain sequences to the z-domain.

**Zero** - A value of z for which the transfer function becomes zero.

**Zero-Order Hold** - A reconstruction method that holds the sample value constant until the next sample.

---

*This glossary is continuously updated as new terms are introduced throughout the course.*
