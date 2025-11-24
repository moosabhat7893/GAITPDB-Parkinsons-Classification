# GAITPDB-Parkinsons-Classification

Gait-based classification of Parkinson’s Disease (PD) patients vs Healthy controls using a 1D Convolutional Neural Network (CNN) built with TensorFlow/Keras. The model processes multi-channel gait signals from instrumented insoles to detect Parkinson’s disease based on walking patterns.

# Objective

To develop and evaluate a deep learning model capable of classifying PD patients and healthy individuals from multi-sensor gait data. The model learns temporal and spatial patterns from insole sensor readings to identify gait abnormalities associated with Parkinson’s disease.

# Technologies / Libraries

Python
TensorFlow / Keras

NumPy, Pandas, Scikit-learn

Matplotlib

# Dataset

The dataset consists of gait recordings from Parkinson’s patients and healthy controls using instrumented insoles with 8 sensors per foot, sampled at 100 Hz. Each .txt file corresponds to a walking session of a subject.

**Data Format (19 columns):** 

Column	Description
1	Time (seconds)

2–9	Vertical ground reaction force (VGRF) – left foot sensors L1–L8

10–17	VGRF – right foot sensors R1–R8

18	Total force – left foot

19	Total force – right foot

**File Naming Convention:**

 <Study><Co/Pt><Subject>_<Walk>.txt

Study: Ga, Ju, Si

Co/Pt: Control / PD patient

Walk: 01 = normal walk, 10 = dual-task walk



Citation:

APA:

Goldberger, A., Amaral, L., Glass, L., Hausdorff, J., Ivanov, P. C., Mark, R., ... & Stanley, H. E. (2000). PhysioBank, PhysioToolkit, and PhysioNet: Components of a new research resource for complex physiologic signals. Circulation [Online], 101(23), e215–e220. RRID:SCR_007345.

#  Key Features

Data Preprocessing: Normalization, segmentation using sliding windows (WINDOW_SIZE=128, OVERLAP=0.5)

1D CNN Architecture:

Conv1D → MaxPooling → Dropout → Conv1D → MaxPooling → Flatten → Dense → Dropout → Dense (sigmoid)

Binary classification (PD vs Healthy)

Training and Evaluation:

Train/Test split (80/20)

Accuracy and loss tracking over epochs

Gait Visualization:

Overlay PD vs Healthy signals for all 18 sensors

Random sample visualizations from test set

# Results
Metric	Value
Training Accuracy	99.41%
Training Loss	0.0175
Test Accuracy	98.55%
Test Loss	0.0472

# Insights:

CNN effectively captures temporal dependencies across sensors.

Model generalizes well to unseen test segments.

Visualization shows clear differences in gait waveforms between PD and healthy subjects.

# Visual Outputs

**Sample Gait Wave Overlays (PD , Healthy)**

This plot shows the difference in gait patterns between a Parkinson’s patient (red) and a healthy control (green).

The waveform is created by averaging all 18 insole sensors for each foot, giving a clear, single representation of overall gait forces.

The x-axis represents time steps, and the y-axis represents normalized force (N).

This visualization highlights how Parkinson’s patients exhibit altered gait patterns compared to healthy individuals.

![Gait Wave Overlay](images/gait_wave_overlay.png)

**Training Accuracy / Loss Plot**

![Accuracy/Loss](images/accuracy_loss.png)
# Future Enhancements

Incorporate more sensor modalities (accelerometer, gyroscope)

Experiment with LSTM or BiLSTM for temporal modeling

Implement real-time gait classification

Deploy as a web app for clinical use

# License

This project is open-source under the MIT License.

# Author

Muhammad Moosa Bhat
GitHub: moosabhat7893
