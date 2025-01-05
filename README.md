# **Wearables to Context-Aware Fitness: Strength Training Tracker**

## **Overview**
This repository hosts the code and resources for building a **context-aware fitness tracker** capable of:
- Identifying strength training exercises.
- Counting repetitions.
- Detecting improper form.

The project leverages data from wearable sensors and applies advanced machine learning techniques to deliver insights that mimic the role of a personal trainer.

---

## **Features**
- **Exercise Classification:** Automatically identifies barbell exercises (Bench Press, Deadlift, Overhead Press, Barbell Row, and Squat).
- **Repetition Counting:** Accurately counts repetitions for each exercise.
- **Form Detection:** Detects common errors in exercise execution, ensuring safety and proper technique.
- **Real-World Application:** Designed using real workout data collected from wrist-worn Meta Motion sensors.

---

## **Project Motivation**
This project is a fusion of my two passions: fitness and technology. With a background in strength training, including winning two consecutive gold medals at university bodybuilding championships and training high-profile clients like South Indian celebrity Vijay Devarakonda, I wanted to create a tool that could help others achieve their fitness goals safely and efficiently.

---

### **Acknowledgments**
This project is inspired by the research conducted by **Dave Ebbelaar**. His paper, *"Exploring the Possibilities of Context-Aware Applications for Strength Training"*, provided the foundation for the methodologies and approaches used in this project. You can find more of his work on his GitHub profile: [@daveebbelaar](https://github.com/daveebbelaar).

---

## **Technologies Used**
### **Hardware**
- Meta Motion Sensor (Wrist-Worn): Captures accelerometer and gyroscope data.

### **Software**
- **Programming Language:** Python
- **Libraries:** 
  - Data Processing: `pandas`, `numpy`, `scipy`
  - Machine Learning: `scikit-learn`
  - Visualization: `matplotlib`, `seaborn`
- **Development Tools:**
  - Jupyter Notebooks for exploration and experimentation.
  - Pickle for storing and loading intermediate datasets.

---

## **Project Structure**

```plaintext
├── LICENSE
├── README.md         # Project overview and usage guide
├── data              # Data storage directory
│   ├── external      # Data from third-party sources
│   ├── interim       # Intermediate transformed datasets
│   ├── processed     # Final, clean datasets for modeling
│   └── raw           # Original sensor data
├── docs              # Documentation files
├── models            # Trained models and predictions
├── notebooks         # Jupyter notebooks for analysis
├── references        # Manuals and explanatory materials
├── reports           # Analysis reports with figures
├── src               # Source code for project
│   ├── data          # Data preparation scripts
│   ├── features      # Feature engineering scripts
│   ├── models        # Model training and evaluation scripts
│   └── visualization # Scripts for data visualization
└── requirements.txt  # Dependencies for project setup
``` 
---
### **How It Works**

#### **1. Data Collection**
- The dataset is collected using **Meta Motion sensors** worn on the wrist, mimicking the placement of a smartwatch. 
- The sensors capture **accelerometer** (measuring acceleration along X, Y, Z axes) and **gyroscope** (measuring angular velocity) data during strength training exercises.
- Five foundational barbell exercises are recorded:
  - Bench Press
  - Deadlift
  - Overhead Press
  - Barbell Row
  - Squat

#### **2. Data Processing**
- **Outlier Removal:** Detected and removed anomalies from the dataset using Local Outlier Factor (LOF).
- **Data Smoothing:** Applied low-pass filtering to remove high-frequency noise and ensure smooth signals.
- **Temporal Aggregation:** Summarized motion data over time windows, calculating mean, standard deviation, and other metrics.
- **Frequency Analysis:** Used Fourier Transformations to identify periodic patterns, such as repetitions in exercises.

#### **3. Feature Engineering**
- **Dimensionality Reduction:** Used Principal Component Analysis (PCA) to simplify the dataset while retaining critical motion patterns.
- **Clustering-Based Features:** Grouped similar movements using k-means clustering to distinguish between overlapping exercises.
- **Scalar Magnitudes:** Combined sensor data into orientation-independent metrics to capture overall motion intensity.

#### **4. Model Training**
- Machine learning models are trained to classify exercises, count repetitions, and detect improper form:
  - **Classification Accuracy:** Achieved 98.5% using Random Forest for exercise identification.
  - **Repetition Counting:** Used peak detection algorithms to count repetitions with ~95% accuracy.
  - **Form Detection:** Trained separate models to detect improper execution of exercises (e.g., incorrect bench press form).

#### **5. Results**
- **Exercise Classification Accuracy:** 98.5%
- **Repetition Counting Error:** ~5%
- **Form Detection Accuracy:** 98.5%

---

### **Key Files**
- `src/data/make_dataset.py`: Processes raw data into a usable format.
- `src/features/build_features.py`: Generates features for machine learning.
- `src/models/train_model.py`: Contains scripts for training and evaluating models.
- `src/visualization/visualize.py`: Visualizes motion patterns and results.

---

### **Future Directions**
- **Dataset Expansion:** Include data from a broader participant base to improve model generalization.
- **Integration with Additional Sensors:** Combine data from heart rate monitors, EMG sensors, or other devices for more comprehensive insights.
- **Real-Time Applications:** Implement real-time tracking and feedback via smartwatch SDKs.
- **Enhanced Form Detection:** Expand improper form detection to include more exercises and detailed analysis.

---

### **Contributing**
We welcome contributions from the community! If you have ideas or enhancements, please:
1. Fork this repository.
2. Create a new branch for your changes.
3. Submit a pull request detailing your updates.

---

### **Contact**
Have questions or feedback? Feel free to reach out:
- **Medium Blog:** [Wearables to Context-Aware Fitness](https://medium.com/@srinivasbarla2000/wearables-to-context-aware-fitness-building-a-strength-training-tracker-f5b3093bb0cc)
