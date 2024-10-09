# Challenge Two: The Quest to return

## Overview

This challenge requires the participants to identify a song/audio file they would like to use and complete the task in MATLAB and apply three different filter techniques of your choice.

## Knowledge

- MATLAB
- signal filtering


## Dependencies & Tools

- MATLAB

## Documentation

Here's how you could procede:
- high Level Steps
- identify audio file
- convert to WAV file
- read WAV file in MATLAB
- create a Power Spectrum Plot of Original
- design your filter
- apply your filter
- create a Power Spectrum Plot of the Filtered

Helpful Hints and Example Code
```matlab
% Step 1: Read the WAV file
[audio, fs] = audioread('your_audio_file.wav');

% Step 2: Design a low-pass filter
cutoff_freq = 1000; % Cutoff frequency in Hz
[b, a] = butter(6, cutoff_freq/(fs/2), 'low'); % 6th order Butterworth filter

% Step 3: Apply the filter
filtered_audio = filter(b, a, audio);

% Step 4: Play the original and filtered audio
sound(audio, fs); % Play original audio
pause(length(audio)/fs + 1); % Wait for the audio to finish
sound(filtered_audio, fs); % Play filtered audio

% Step 5: Save the filtered audio (optional)
audiowrite('filtered_audio_file.wav', filtered_audio, fs);

% Step 6: Create a power spectrum plot
% Compute the FFT of the original audio
N = length(audio);
f = (0:N-1)*(fs/N); % Frequency vector
audio_fft = fft(audio);
power_audio = abs(audio_fft).^2/N; % Power spectrum

% Compute the FFT of the filtered audio
filtered_audio_fft = fft(filtered_audio);
power_filtered_audio = abs(filtered_audio_fft).^2/N; % Power spectrum

% Plot the power spectrum
figure;
subplot(2,1,1);
plot(f, power_audio);
title('Power Spectrum of Original Audio');
xlabel('Frequency (Hz)');
ylabel('Power');

subplot(2,1,2);
plot(f, power_filtered_audio);
title('Power Spectrum of Filtered Audio');
xlabel('Frequency (Hz)');
ylabel('Power');
```


## Evaluation Criteria

The solution will be evaluated base on the following criteria:
 - methodology: was the task created in an innovative and creative way? (working solution, minimal redundant logic, etc)

- working solution: was the task executed successfully or were there unknown bugs/glitches?

## Submission

To complete the challenge, use [this form]() to submit a `.zip` file containing:
- power Spectrum Plots for Original and Filtered Signals
- audio files of original and filtered signals
- short Explanations (2-3 sentences) of each filter and it’s intended objective
- MATLAB Code