# Deep Learning for Wireless Communication

## Overview

This project demonstrates a novel approach to signal modulation in wireless communication systems using deep learning. It implements an autoencoder-based neural network that learns to transmit and receive signals through a non-linear channel, comparing its performance against traditional QPSK (Quadrature Phase Shift Keying) modulation.

## Key Features

- **Autoencoder Architecture**: End-to-end trainable neural network for wireless communication
- **Non-Linear Channel Modeling**: Simulates realistic power amplifier saturation effects using tanh function
- **Adaptive Signal Design**: The neural network learns to pre-distort signals to compensate for channel non-linearities
- **Performance Comparison**: Benchmarks against standard QPSK modulation under identical channel conditions

## System Parameters

- **Modulation Order**: M = 4 (QPSK-like)
- **Channel Dimensions**: 2 (I/Q components)
- **Bits per Symbol**: k = 2
- **Non-Linearity**: tanh saturation (simulating power amplifier clipping)

## How It Works

### 1. Encoder (Transmitter)
- Takes one-hot encoded message symbols as input
- Transforms into 2-dimensional signal space
- Normalizes power to maintain constant energy

### 2. Non-Linear Channel
- Applies tanh distortion to simulate power amplifier saturation
- Adds Gaussian noise based on SNR level

### 3. Decoder (Receiver)
- Receives distorted and noisy signals
- Classifies back to original message symbols using softmax

### 4. Training
- 25,000 training samples
- 40 epochs with Adam optimizer
- Categorical cross-entropy loss

## Simulation Results

The program compares three approaches:
1. **Deep Learning Autoencoder**: Learned communication strategy
2. **Standard QPSK (Clipped)**: Traditional modulation through non-linear channel
3. **Theoretical QPSK**: Ideal performance in linear channel (reference)

Performance is evaluated across SNR range from 0 to 10 dB, plotting Symbol Error Rate (SER) curves.

## Key Insight

The autoencoder learns to avoid high amplitudes that would be severely distorted by the non-linear channel, achieving better error rates than conventional QPSK modulation under the same conditions.

## Requirements

```
numpy
tensorflow
matplotlib
scipy
```

## Usage

Run all cells in `DL_Wireless_Com.ipynb` sequentially. The final cell generates a performance comparison plot showing SER vs SNR for all three approaches.

## Results Interpretation

- Lower SER values indicate better performance
- The autoencoder typically outperforms standard QPSK in non-linear channels
- The gap between learned and conventional approaches highlights the benefit of end-to-end learning

## Technical Highlights

- Power normalization ensures fair comparison between methods
- Vectorized QPSK demodulation for efficient simulation
- 100,000 test samples per SNR point for statistical reliability
- Semi-log plotting for clear visualization of error rate trends

---

*This project demonstrates the potential of deep learning to optimize communication systems for realistic, non-ideal channel conditions.*
