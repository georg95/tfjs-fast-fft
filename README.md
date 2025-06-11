## Fast FFT, IFFT, tf.signal.stft

This script overrides tensorflow.js FFT, IFFT and `tf.signal.stft` with fast implementations.

It works for `webgl` and `webgpu` backends when input tensor dimension is power of 2: 2, 4, 8, 16, 32, 64, 128...

If not, it fallbacks with warning.

## How to use
Put script after tensorflow.js scripts

`<script src="https://georg95.github.io/tfjs-fast-fft/fft.js"></script>`

Or copy-paste code from https://github.com/georg95/tfjs-fast-fft/blob/main/fft.js

## Optimizations:
- Cooley-Tukey `N*log(N)` algorithm
- Stft framing window with single webgl/webgpu call
- Rearranged imaginary and real values in single tensor for cache locality and less gpu calls
- Special algorithm for non-complex stft input

