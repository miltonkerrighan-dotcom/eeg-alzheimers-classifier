# eeg-alzheimers-classifier
Machine learning pipeline classifying Alzheimer's disease from resting-state EEG, testing whether where slowing occurs on the scalp improves diagnosis (Python, MNE, scikit-learn).

# EEG Alzheimer's Classifier

**Can the location of EEG slowing on the scalp help distinguish Alzheimer's disease?**

An end-to-end Python pipeline, from raw resting-state clinical EEG recordings to a validated classifier.

## Background
Alzheimer's disease is associated with EEG slowing: power shifts from faster rhythms (alpha, beta) toward slower ones (delta, theta). The original study for this dataset reported 77.01% accuracy using 5 features averaged across the whole head. This project keeps all 19 electrodes separate (228 features per subject) to test whether *where* the slowing happens adds diagnostic information.

## Data
OpenNeuro [ds004504](https://openneuro.org/datasets/ds004504) (Miltiadous et al., 2023): 88 subjects, eyes-closed resting-state EEG, 19 electrodes, 500 Hz, with MMSE scores. The recordings are not included in this repo; download them from OpenNeuro.

## Pipeline
1. Load and preprocess raw recordings (MNE-Python)
2. Split continuous signals into epochs
3. Compute band power for each channel
4. Build the feature matrix (228 features per subject)
5. Train and cross-validate classifiers (scikit-learn)

## Status: in progress
- **Known issue:** eye-movement artifacts in the frontal channels (Fp1, Fp2, F7, F8); ICA-based removal is planned.
- **Open decisions:** frequency band boundaries, relative-power denominator, epoch overlap, and handling 228 features with a small sample size.

## Tools
Python · MNE-Python · NumPy · pandas · scikit-learn · Jupyter

## Author
Kerrighan Milton, B.S. Biochemistry–Molecular Biology, UC Santa Barbara
