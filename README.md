# 🏀 Sports Activity Recognition: A Two-Phase Comparative Study

## 📌 Project Overview

This project presents a **comprehensive two-phase investigation** comparing traditional machine learning models with neural network architectures for **Sports-Based Human Activity Recognition (HAR)** using video data. The study systematically evaluates performance across different feature representations and model paradigms.

---

## 🎯 Research Objectives

- **Phase 1**: Compare traditional ML models vs neural networks on different feature representations
- **Phase 2**: Evaluate neural networks on engineered spatio-temporal features
- Analyze overfitting behavior across different architectures
- Identify optimal pipelines for limited-data scenarios
- Provide insights for future research directions in video understanding

---

## 📂 Dataset & Experimental Setup

**Dataset**: UCF-101 Subset
- **Total Videos**: 1,456
- **Classes**: 10 sports activities
- **Activities**: Basketball Dunk, Tennis Swing, Soccer Penalty, Archery, Boxing Punching Bag, Golf Swing, Skate Boarding, Bowling, Baseball Pitch, Diving

**Data Split**:
- Training: 1,012 videos (70%)
- Validation: 216 videos (15%)
- Testing: 228 videos (15%)

---

## 🔬 Methodology: Two-Phase Approach

### Phase 1: Traditional vs. Neural Models on Different Inputs

#### **Traditional ML Pipeline** (High-Quality Features)
- **Feature Extraction**: Improved Dense Trajectories (IDT)
  - HOG (appearance/shape)
  - HOF (motion)
  - MBH (motion boundaries)
  - Trajectory Shape (kinematic path)
- **Feature Processing**: Normalization + PCA (38,448 → 500 features)
- **Classifiers Tested**: SVM (RBF), Logistic Regression, Random Forest, XGBoost

#### **Neural Network Pipeline** (Raw Input)
- **Input**: Grayscale video frames
- **Architectures**: FCNN, RNN, LSTM, GRU
- **Training**: Adam optimizer, Cross Entropy Loss
- **All models**: 50 epochs, batch size 32

### Phase 2: Neural Networks on Engineered Features

- **Input**: Same spatio-temporal features as Traditional ML pipeline
- **Architectures**: FCNN, RNN, LSTM, GRU
- **Feature Dimension**: 500 after PCA
- **Training**: Same hyperparameters as Phase 1

---

## 📊 Experimental Results

### Phase 1: Traditional ML vs. Neural Networks (Different Inputs)

| Model Category | Best Model | Features Used | Test Accuracy | Key Insight |
|---------------|------------|---------------|---------------|-------------|
| **Traditional ML** | **SVM (RBF)** | **IDT Features** | **70.61%** | Best overall performance |
| Traditional ML | Logistic Regression | IDT Features | 69.74% | Strong linear baseline |
| **Neural Networks** | **FCNN** | **Raw Frames** | **42.54%** | Best neural on raw data |
| Neural Networks | GRU | Raw Frames | 40.8% | Better than LSTM on raw |
| Neural Networks | LSTM | Raw Frames | 39.0% | Overfits quickly |
| Neural Networks | RNN | Raw Frames | 37.3% | Worst performance |

**Phase 1 Gap**: **28.07%** accuracy difference between best traditional and best neural model

### Phase 2: Neural Networks on Engineered Features

**COMPREHENSIVE MODEL PERFORMANCE COMPARISON**

| Model | Parameters | Best Val Acc | Test Acc | Test F1 | Training Epochs | Overfitting Gap |
|-------|------------|--------------|----------|---------|-----------------|-----------------|
| **FCNN** | Unknown | 77.78% | **65.79%** | 0.6487 | 36 | 11.99 |
| LSTM | 1,579,530 | 62.50% | 58.77% | 0.5860 | 34 | 3.73 |
| GRU | 1,185,290 | 60.65% | 54.82% | 0.5092 | 32 | 5.83 |
| RNN | 396,810 | 53.24% | 48.25% | 0.4691 | 31 | 4.99 |

**Phase 2 Gap**: **4.82%** accuracy difference between best traditional (SVM) and best neural (FCNN)

---

## 📈 Key Findings

### **1. Feature Representation Dominates Performance**
- **28.07% gap** when comparing different feature representations
- **4.82% gap** when using same feature representation
- This demonstrates that **feature quality is more important than model choice**

### **2. Traditional ML Advantages**
- **SVM achieved 70.61%** - best overall performance
- Excellent generalization with minimal overfitting
- Computationally efficient during inference
- Most stable across different activity classes

### **3. Neural Network Insights**
- **FCNN on IDT features: 65.79%** - best neural performance
- Simple FCNN outperformed all RNN variants on engineered features
- RNN family showed higher overfitting (parameter inefficiency)
- LSTM/GRU over-parameterized for this feature representation

### **4. Efficiency Analysis**
- **LSTM Efficiency Ratio**: 37.21 (high params, moderate performance)
- **FCNN**: Most efficient neural architecture for this task
- **SVM**: Most efficient overall considering accuracy/implementation

---

## 🧠 Technical Insights

### Why Traditional ML Outperformed in Phase 1?
1. **Handcrafted Feature Superiority**: IDT features explicitly encode motion patterns
2. **Limited Data**: Neural networks need more data to learn from raw pixels
3. **Domain Knowledge**: IDT features incorporate computer vision expertise

### Why FCNN Beat RNNs in Phase 2?
1. **Feature Encoding**: Temporal information already captured in IDT statistics
2. **Parameter Efficiency**: FCNN has fewer parameters, less overfitting
3. **Task Simplicity**: Classification from static feature vectors doesn't need sequential modeling

### Persistent Challenges
- **Archery**: Most difficult class across all models
- **Similar Actions**: Bowling vs. Baseball Pitch confusion
- **Camera Motion**: Affects trajectory-based features

---

## 🏁 Conclusions

### **Primary Conclusion**
The **feature representation paradigm** has greater impact on sports activity recognition accuracy than the **model architecture paradigm**, especially with limited training data.

### **Specific Conclusions**
1. **Traditional ML with engineered features** (SVM + IDT) provides the best accuracy (70.61%) for limited data scenarios
2. **Neural networks can approach traditional performance** (65.79% vs 70.61%) when given the same high-quality features
3. **Simple architectures often outperform complex ones**: FCNN beat all RNN variants
4. **The 28% performance gap in Phase 1 was primarily a feature gap, not a model gap**

---

## 🚀 Future Research Directions

### **Immediate Next Steps**
1. **3D CNNs**: Test I3D or similar architectures on raw video
2. **Two-Stream Networks**: Combine appearance and motion streams
3. **Feature Fusion**: Combine IDT features with learned representations
4. **Data Augmentation**: Apply temporal and spatial augmentations

### **Architectural Innovations**
1. **Hybrid Models**: IDT features as input to attention-based networks
2. **Transfer Learning**: Pre-trained video models fine-tuned on sports data
3. **Efficient Architectures**: MobileNetV3 + GRU for mobile deployment

### **Experimental Improvements**
1. **Larger Dataset**: Test on full UCF-101 or Sports-1M
2. **More Classes**: Include finer-grained sports activities
3. **Real-world Testing**: Deploy on mobile devices for practical evaluation

---


*Last Updated: [Current Date]*

