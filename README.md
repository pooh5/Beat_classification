This project performs classification of heart sounds recorded from the neck into three categories: normal, murmur, and artifact. It uses a combination of signal processing and classical machine learning techniques for feature extraction and classification.
Project Overview
•	Input: .wav audio files sampled at 44.1 kHz
•	Classes: normal, murmur, artifact
•	Features extracted:
o	MFCC (13 coefficients) with delta and delta-delta features (mean and std)
o	Hilbert envelope: peak stats (height, width, prominence, IPI)
o	Shannon entropy envelope: mean, std, peak
o	ZCR (Zero Crossing Rate): mean and std
o	Wavelet energy (Daubechies, level 0–4)
•	Model used: XGBoost classifier
Key Results
•	For event detection F1 score-0.8317 
•	Weighted F1 Score for classification: 0.84
•	Top contributing features: Mean prominence from Hilbert, mean and standard deviation of width from Hilbert, standard deviation of Shannon envelop, MFCC features from 4 to 7, wavelet energy levels from 1 to 4 
•	Feature importance: Assessed via statistical tests (Kruskal-Wallis), Dunn’s post hoc test
Notable Observations
•	Features like mean_amplitude and ICA-based components were not included in the final model due to limited experimentation.
•	The classifier shows good discriminatory ability across two classes, could be improved for normal class 
•	Normalization was skipped (XGBoost is scale-invariant), but could be explored in future iterations.
Future Work
•	Incorporate ICA-based features and amplitude variations
•	Experiment with feature normalization
•	Use k-fold cross-validation instead of a single stratified split
•	Explore model ensembling (Random Forest, LightGBM, stacking)
•	Tune hyperparameters with Optuna for better generalization


