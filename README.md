# Bearing Fault Diagnosis using Convolutional Neural Networks and Vibration Spectrogram

Description: Vibrational Analysis for CWRU Bearing Dataset

This is a Python code implementation of the following publications: 

1.  Accurate Bearing Fault Diagnosis under Variable Shaft Speed using Convolutional Neural Networks and Vibration Spectrogram
- Authors: Minh Tuan Pham, Jong-Myon Kim and Cheol Hong Kim
- https://www.mdpi.com/2076-3417/10/18/6385
- The authors of this paper decided to use Matlab to extract a time domain signal that does not change over time, he has a Matlab tool to apply this feature engineering approach prior to the time domain to frequency domain conversion. I have decided not to use the feature engineering, instead, I've kept the time domain signal intact and I've applied STFT to the entirety of the signal.

- PLEASE PAY ATTENTION HERE, EVERYTHING YOU SEE DOWN HERE IS ACTUALLY WRITTEN BY THE AUTHOR OF THIS PAPER, I haven't used this Shaft speed dataset, I only tried to use this approach on CWRU bearing dataset to verify the feasibility of this approach.

2. Proposed Bearing Fault Diagnosis Method: 
An overview of the proposed bearing fault diagnosis method is shown in Figure 1. First, the vibration signals are split into fixed-cycle 5 seconds segments. The Short-Time Fourier Transform (STFT) is then applied for each signal segment to produce the spectrogram. 

Then, spectrogram images generated from the vibration signals corresponding to the bearing faults are used to train network architecture CNN-VGG16, and the trained CNN-VGG16 model is used to classify bearing faults automatically in the test stage.

![image](https://user-images.githubusercontent.com/80536675/178956647-bc5c3118-9313-464e-8579-fcd8e9c81f55.png)

2.1. Signal Preprocessing

The vibration signals acquired from electrical machines are nonstationary as they contain bearing fault information modulated for variable rotational speeds and surrounding environmental noise. The frequency of the obtained signal is continuous, and its time-domain statistical features change with time. Nonstationary signals typically lack useful information in the time or frequency domains but may have useful information through merge representation within the time-frequency (t, f ) space. In varying working conditions of bearings (various types of single and compound faults and various degradation levels at variable rotational speeds), traditional signal processing methods such as envelope spectrum analysis and wavelet package transform are challenging to obtain meaningful information. Under these conditions, the signal’s spectrum varies greatly in amplitude and frequency. Therefore, it is troublesome to recognize the deficiencies of bearings under adverse working conditions, using conventional signal processing methods. For appropriate analysis and synthesis of nonstationary signals, Short-Time Fourier Transform (STFT) is a typical Fourier transform (FT) applied to create the spectrograms of signals. The spectrogram is a visual representation of the signals in both the time-frequency domains, using a color scale of the image to indicate the frequency’s amplitude.

2.1.1. Short-Time Fourier Transform

STFT applies a Fourier transform for localization both in the frequency and time domains for signals that are time-varying or nonstationary [11]. The process for the STFT can be represented as follows 

![image](https://user-images.githubusercontent.com/80536675/178957789-3c78c661-37c2-4f1b-9c75-128e9f426171.png)

2.1.2. Implementing STFT Analysis for Spectrograms (NOTE I've NOT USED THIS MATLAB TOOL)

With the advantages of frequency-domain analysis for nonstationary signals, STFT can be a good approach for analyzing the bearing signals under complex conditions or with background noise.
To efficiently apply STFT to bearing fault signals, the STFT matrix can be determined by a new routine with the MATLAB tool to achieve high accuracy and computational efficiency [12]. After analyzing which segment duration of the signal has essential features (such as mean, RMS, standard deviation, variance, kurtosis, skewness, crest factor, and form factor that do not change with time), the window length (window length) is set as 1024. The accuracy is prioritized to window length, although the shorter windows affect the calculation volume in a negative manner. The hop size is set to wlen/4 based on various experiments [12].
Figure 2 shows the spectrograms produced by applying STFT to vibrations signals with four different shaft speeds (1730, 1750, 1772, and 1797 RPM) with three kinds of faults (inner race fault, outer race fault, and roller fault).

- I haven't use VGG model either, i've used Resnet18.


## Stargazers over time

[![Stargazers over time](https://starchart.cc/Abdulhamid97Mousa/Bearing-Fault-Diagnosis-CNNs-and-Vibration-Spectrogram.svg)](https://starchart.cc/Abdulhamid97Mousa/Bearing-Fault-Diagnosis-CNNs-and-Vibration-Spectrogram)
