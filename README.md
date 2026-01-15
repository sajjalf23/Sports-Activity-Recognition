# Sports-Based Activity Recognition Using Video Data

## 📌 Project Overview

This project presents a comparative study between **traditional machine learning models** and **neural network-based approaches** for **Sports-Based Human Activity Recognition (HAR)** using video data.

Sports activity recognition aims to automatically identify athletic actions such as basketball dunk, tennis swing, bowling, and boxing from video sequences. The task is challenging due to fast movements, camera motion, occlusion, and similarity between actions.

This study evaluates how well traditional handcrafted spatio-temporal features perform compared to neural networks that learn directly from frame appearance, especially when training data is limited.

---

## 🎯 Objectives

- Compare traditional ML models vs neural networks for sports action recognition  
- Evaluate performance using accuracy and F1-score  
- Analyze overfitting behavior  
- Identify strengths and weaknesses of each paradigm  
- Provide insights for future research directions  

---

## 📂 Dataset

- Dataset: **UCF-101**
- Total videos in dataset: **13,451**
- Classes in dataset: **101**
- Subset used: **1,456 videos**
- Activities used (10):

| Activities |
|----------|
| Basketball Dunk |
| Tennis Swing |
| Soccer Penalty |
| Archery |
| Boxing Punching Bag |
| Golf Swing |
| Skate Boarding |
| Bowling |
| Baseball Pitch |
| Diving |

### Data Split

- Training: 70% (1,012 videos)
- Validation: 15% (216 videos)
- Testing: 15% (228 videos)

---

## 🧠 Methodology

Two different recognition pipelines are evaluated:

---

### 🔹 Traditional Machine Learning Pipeline

#### Feature Extraction
Spatio-temporal motion features using improved dense trajectories:

| Feature | Purpose |
|------|------|
| HOG | Appearance / Shape |
| HOF | Motion |
| MBH | Motion Boundaries |
| Trajectory Shape | Kinematic Path |

#### Temporal Statistics
- Maximum  
- Minimum  
- Mean  
- Standard Deviation  

These are concatenated with histogram vectors to form a high-dimensional feature vector.

#### Feature Processing
- Normalization
- PCA dimensionality reduction (38,448 → 500 features)

#### Classifiers
- Logistic Regression  
- Random Forest  
- XG Boost  
- Support Vector Machine (RBF Kernel)  

---

### 🔹 Neural Network Pipeline

Video frames are converted to grayscale and used as appearance features.

Neural networks used:

- Fully Connected Neural Network (FCNN)
- Recurrent Neural Network (RNN)
- Long Short-Term Memory (LSTM)
- Gated Recurrent Unit (GRU)

All models:
- Adam Optimizer  
- Cross Entropy Loss  
- Multiclass classification  

---

## 📊 Experimental Results

### Traditional Models Accuracy

| Model | Accuracy |
|------|---------|
| SVM | **70.61%** |
| Logistic Regression | 69.74% |
| Random Forest | ~65% |
| XG Boost | ~64% |

SVM achieved the best performance with strong generalization and minimal overfitting.

---

### Neural Networks Accuracy

| Model | Accuracy |
|------|---------|
| FCNN | **42.54%** |
| GRU | 40.8% |
| LSTM | 39.0% |
| RNN | 37.3% |

Neural networks struggled due to limited dataset size and lack of rich learned features.

---

## 📈 Key Findings

- Traditional models with handcrafted spatio-temporal features outperform neural networks on small datasets.
- SVM achieved the best balance of accuracy and generalization.
- Neural networks showed higher overfitting.
- GRU performed better than RNN and LSTM among neural networks.
- Archery remained the most difficult class across all models.

---

## 🔍 Discussion

Traditional models benefit from strong handcrafted motion descriptors that provide meaningful representations even with limited data. Neural networks, however, require large datasets and richer inputs to learn effective representations.

Spatio-temporal features alone struggle in actions involving minimal body movement and similar postures.

---

## 🏁 Conclusion

This study demonstrates that:

- Traditional ML models with spatio-temporal features outperform neural networks when data is limited.
- There exists a **28% accuracy gap** between the best traditional model and the best neural network.
- SVM achieved the highest accuracy and lowest overfitting.
- Neural networks require larger datasets and advanced architectures such as 3D CNNs for better performance.

---

## 🚀 Future Work

- Use 3D CNNs and deep spatio-temporal networks  
- Integrate optical flow into neural models  
- Increase dataset size  
- Use multimodal inputs  
- Improve feature engineering for stationary sports  
- Perform fairer comparisons with equivalent feature richness  

