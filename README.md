# Motion Compensated Pulse Rate Estimation

## Part 1: Pulse Rate Algorithm Project Overview

### Algorithm Specifications

You must build an algorithm that:

- estimates pulse rate from the PPG signal and a 3-axis accelerometer.

- assumes pulse rate will be restricted between 40BPM (beats per minute) and 240BPM

- produces an estimation confidence. A higher confidence value means that this estimate should be more accurate than an estimate with a lower confidence value.

- produces an output at least every 2 seconds.

### Success Criteria

Your algorithm performance success criteria are as follows: the mean absolute error at 90% availability must be less than 15 BPM on the test set. Put another way, the best 90% of your estimates--according to your own confidence output-- must have a mean absolute error of less than 15 BPM. The evaluation function is included in the starter code.

Note that you will not have access to the dataset that the unit test will call AggregateErrorMetric on the output of your RunPulseRateAlgorithm on a test dataset that you do not have access to. The result of this call must be less than 15 BPM for your algorithm's performance to pass. The test set should be easier than the training set, so as long as your algorithm is doing reasonably well on the training data set, it should pass this test.

### Some Helpful Tips

Remember to bandpass filter all your signals. Use the 40-240BPM range to create your pass band.

Use plt.specgram to visualize your signals in the frequency domain. You can plot your estimates on top of the spectrogram to see where things are going wrong.

When the dominant accelerometer frequency is the same as the PPG, try picking the next strongest PPG frequency if there is another good candidate.

Sometimes the cadence of the arm swing is the same as the heartbeat. So if you can't find another good candidate pulse rate outside of the accelerometer peak, it may be the same as the accelerometer.

One option for a confidence algorithm is to answer the question, "How much energy in the frequency spectrum is concentrated near the pulse rate estimate?" You can answer this by summing the frequency spectrum near the pulse rate estimate and dividing it by the sum of the entire spectrum.

### Dataset

You will be using the Troika[1] dataset to build your algorithm. Find the dataset under datasets/troika/training_data. The README in that folder will tell you how to interpret the data. The starter code contains a function to help load these files.

Zhilin Zhang, Zhouyue Pi, Benyuan Liu, ‘‘TROIKA: A General Framework for Heart Rate Monitoring Using Wrist-Type Photoplethysmographic Signals During Intensive Physical Exercise,’’IEEE Trans. on Biomedical Engineering, vol. 62, no. 2, pp. 522-531, February 2015. Link

### Getting Started

The starter code includes a few helpful functions. TroikaDataset, AggregateErrorMetric, and Evaluate do not need to be modified.

Use TroikaDataset to retrieve a list of .mat files containing reference and signal data.

Use scipy.io.loadmat to the .mat file into a python object.
The bulk of the code will be in the RunPulseRateAlgorithm function. You can and should break the code out into multiple functions.

RunPulseRateAlgorithm will take in two filenames and return a tuple of two NumPy arrays--per-estimate pulse rate error and confidence values. Note: Remember to write docstrings for all functions that you write (including RunPulseRateAlgorithm)
Finally, run the Evaluate function to call your algorithm on the Troika dataset and compute an aggregate error metric. Hint: While building the algorithm, you may want to inspect the algorithm errors in more detail.

## Part 2:

Part 2: Clinical Application
Now that you have built your pulse rate algorithm and tested your algorithm to know it works, we can use it to compute more clinically meaningful features and discover healthcare trends.

Specifically, you will use 24 hours of heart rate data from 1500 samples to try to validate the well-known trend that average resting heart rate increases up until middle age and then decreases into old age. We'll also see if resting heart rates are higher for women than men. See the trend illustrated in this image:

Follow the steps in the notebook to reproduce this result!

Dataset (CAST)

The data from this project comes from the Cardiac Arrhythmia Suppression Trial (CAST), which was sponsored by the National Heart, Lung, and Blood Institute (NHLBI). CAST collected 24 hours of heart rate data from ECGs from people who have had a myocardial infarction (MI) within the past two years.[1] This data has been smoothed and resampled to more closely resemble PPG-derived pulse rate data from a wrist wearable.[2]

CAST RR Interval Sub-Study Database Citation - Stein PK, Domitrovich PP, Kleiger RE, Schechtman KB, Rottman JN. Clinical and demographic determinants of heart rate variability in patients post-myocardial infarction: insights from the Cardiac Arrhythmia Suppression Trial (CAST). Clin Cardiol 23(3):187-94; 2000 (Mar)
Physionet Citation - Goldberger AL, Amaral LAN, Glass L, Hausdorff JM, Ivanov PCh, Mark RG, Mietus JE, Moody GB, Peng C-K, Stanley HE. PhysioBank, PhysioToolkit, and PhysioNet: Components of a New Research Resource for Complex Physiologic Signals (2003). Circulation. 101(23):e215-e220.

### References

- [Motion Compensated Pulse Rate Estimation.](https://github.com/TRoboto/Udacity/tree/master/AI%20for%20Healthcare%20Nanodegree/Project%20-%20Motion%20Compensated%20Pulse%20Rate%20Estimation)
- [Wearable Data Starter.](https://github.com/SaschaMet/Udacity-AI-for-Healthcare-NanoDegree/tree/main/Wearable%20Data%20Starter)

- [Motion Compensated Pulse Rate Estimation](https://github.com/raphl-stx/AI_for_healthcare_Udacity/tree/master/Motion_Compensated_Pulse_Rate_Estimation)
