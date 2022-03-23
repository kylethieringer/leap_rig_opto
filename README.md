# Opto Genetic Experiments in the LEAP rigs

This repository contains a notebook and the measurements required to create stimulus files for opto experiments in the leap rigs. 

The goal of this repo is to make creating stimulus files easy and seamless, and to have a place to store the data safely.

The notebook called 'create_opto_stim.ipynb' contains a function asking what power level you would like to use for experiments. It returns the voltage required to produce that power density for each specific rig. 

You can then create a stimulus file in the notebook or you can pass this voltage output in matlab and create the actual stimulus like this:

```
voltage = 1.23456;
fs = 10000; % daq samplerate
stimLength = 5; % seconds
daqStimLength = fs * stimLength;

stim = [ones(daqStimLength,1)*voltage; zeros(10000, 1)];
save('opto_stims/example_stim.mat', 'stim');
```

**REMEMBER:** you need to save an rig specific .mat file onto each computer in "C:\code\leap_rigs\opto_stims"