---
layout: page
title: Action Recognition based on EMG signal
subtitle: Action Recognition based on EMG signal based on FFT and LSTM
---

## Introduction of EMG and action recognition 
![avatar](/projects/EMG/EMG_explain.png)
Electromyography (EMG) is an electrodiagnostic technique to evaluate the electrical activity produced by skeletal muscles. EMG signals provide easy access to physiological processes that cause muscles to generate force, produce movement and perform actions. Typically, EMG is used in neural science, biomechanics, and signal processing fields. For Instance, EMG is used in hand gesture recognition, robot arm control, expression classification and human-computer interactions. Since EMG activates before motion are visible which could foresee potential information such as intention, force, and even mental activities–information that cannot be recognized with visual evidence alone. To this end, we consider EMG as another crucial clue for exploring actions.

## The model
![avatar](/projects/EMG/EMG_model.png)
The framework of our approach is shown in Figure 1. Sliding windows are first employed to extract EMG signal from each channel. Differently, we utilize Fast Fourier Transform (FFT) instead of RMS as the initial feature extraction approach. This strategy has two advantages. Firstly, FFT decomposes the time series EMG data in frequency domain which automatically separates EMG with high/low noise. Thus, denoising procedures can be omitted. Secondly, FFT provides more comprehensive signal information in each sliding window. After obtaining FFT feature, we utilize the amplitude of each frequency as feature vector, and concatenate the four channels (i.e., left/right forearm/shank) together and input them into a Long Short-Term Memory (LSTM) networks.

## The result
![avatar](/projects/EMG/EMG_result_2.png)

The result denotes that the our approach significantly outperforms conventional methods which also indicates the effectiveness of EMG in action analytical tasks.