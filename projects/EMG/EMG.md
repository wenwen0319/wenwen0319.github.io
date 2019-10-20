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

Mathematically, the updating principles can be written as:
<img src="http://www.forkosh.com/mathtex.cgi? $$\textup{i}_{t}=\sigma(U_{i}X_{t}+W_{i}h_{t-1})$$">
$$\textup{f}_{t}=\sigma(U_{f}X_{t}+W_{f}h_{t-1})$$
$$\textup{o}_{t}=\sigma(U_{o}X_{t}+W_{o}h_{t-1})$$
$$\tilde{c}_{t}=\tanh(U_{c}X_{t}+W_{c}h_{t-1})$$
$$\textup{c}_{t}=\textup{f}_{t}\cdot\textup{c}_{t-1}+\textup{i}_{t}\cdot\tilde{c}_{t}$$
$$h_{t}=\tanh(\textup{c}_{t})\cdot o_{t}$$

where $X_{t}$ is the $t$-th input FFT vector, $\textup{i}_{t}$ is the $t$-th input gate activation vector, $h_{t}$ is the $t$-th hidden state, $\textup{f}_{t}$ is the $t$-th forget gate activation vector, $o_{t}$ is the $t$-th output gate activation vector, $c_{t}$ is the $t$th cell state vector, and $\tilde{c}_{t}$ is the $t$-th new memory content. 
LSTM outputs the representations of FFT features and a classifier is trained to predict the final label. The classifier $C(\cdot)$ is a fully connected network with softmax activation. We choose the last hidden layer of LSTM as the input of $C(\cdot)$. The loss function is as follow.
$$L = \|Y-C(G(F(X))\|_\textup{F}^2$$
where $Y$ is the instance label, $X$ is the original data in time domain. $F(\cdot)$ is the feature extractor using sliding window and FFT. $G(\cdot)$ is LSTM network. $C(\cdot)$ is a full connected network.

## The result
![avatar](/projects/EMG/EMG_result_2.png)

The result denotes that the our approach significantly outperforms conventional methods which also indicates the effectiveness of EMG in action analytical tasks.