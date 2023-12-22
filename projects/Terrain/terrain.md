---
layout: page
title: Terrain Generation Using Single Image
subtitle: Use GNN, GAN to train a model use a single 128*128 image.
---

## Rendering Result 
![avatar](/projects/Terrain/rendering_result_1.png)



<!-- ## The model
![avatar](/projects/EMG/EMG_model.png)

The framework of our approach is shown in Figure 1. Sliding windows are first employed to extract EMG signal from each channel. Differently, we utilize Fast Fourier Transform (FFT) instead of RMS as the initial feature extraction approach. This strategy has two advantages. Firstly, FFT decomposes the time series EMG data in frequency domain which automatically separates EMG with high/low noise. Thus, denoising procedures can be omitted. Secondly, FFT provides more comprehensive signal information in each sliding window. After obtaining FFT feature, we utilize the amplitude of each frequency as feature vector, and concatenate the four channels (i.e., left/right forearm/shank) together and input them into a Long Short-Term Memory (LSTM) networks.

LSTM outputs the representations of FFT features and a classifier is trained to predict the final label. The classifier C(.) is a fully connected network with softmax activation. We choose the last hidden layer of LSTM as the input of C(.). The loss function is as follow.

<center><img src="http://chart.googleapis.com/chart?cht=tx&chl= L = \|Y-C(G(F(X))\|_F^2" style="border:none;"></center>

where Y is the instance label, X is the original data in time domain. F(.) is the feature extractor using sliding window and FFT. G(.) is LSTM network. C(.) is a full connected network.

## The result
![avatar](/projects/EMG/EMG_result_2.png)

The result denotes that the our approach significantly outperforms conventional methods which also indicates the effectiveness of EMG in action analytical tasks. -->