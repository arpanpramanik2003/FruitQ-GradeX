# 🍎🍌🍊 FruitQ-GradeX: Intelligent Fruit Quality Assessment

![Python](https://img.shields.io/badge/python-v3.8+-blue.svg)
![TensorFlow](https://img.shields.io/badge/TensorFlow-v2.x-orange.svg)
![Streamlit](https://img.shields.io/badge/Streamlit-v1.x-red.svg)
![License](https://img.shields.io/badge/license-MIT-green.svg)

## 🚀 Overview

**FruitQ-GradeX** is an advanced deep learning system that simultaneously classifies fruit **type** (Apple, Banana, Guava, Orange) and **quality condition** (Good/Bad) using a custom multi-headed Convolutional Neural Network architecture. The system integrates **Grad-CAM** visualization for model interpretability and features a user-friendly **Streamlit interface** for real-time predictions.

### 🎯 Project Purpose
- Enable automated fruit quality assessment for agricultural and retail applications
- Provide explainable AI insights through visual heatmaps
- Support both batch processing and real-time inference
- Bridge the gap between deep learning research and practical deployment

---

## ✨ Key Features

- 🔄 **Dual Prediction System**: Simultaneous fruit type and quality classification
- 🔍 **Explainable AI**: Grad-CAM visualizations for both prediction heads
- 📱 **Interactive Interface**: Clean Streamlit web app with real-time predictions
- 📊 **Confidence Scoring**: Probability distributions for all predictions
- 🎛️ **Custom Data Pipeline**: Automated data preprocessing and augmentation
- 📸 **Multiple Input Methods**: Upload images or use live webcam capture
- 🎨 **Visual Feedback**: Heatmap overlays highlighting decision-relevant regions
- 📈 **Performance Metrics**: Comprehensive evaluation with accuracy and F1-scores
- 🔧 **Modular Architecture**: Easy to extend for additional fruit types

---

## 📊 Dataset Information

**Source**: FruitNet - Indian Fruits Dataset with Quality Labels

### Distribution by Category

| Fruit Type | Good Quality | Bad Quality | Total |
|------------|--------------|-------------|-------|
| 🍎 Apple   | 1,149        | 1,141       | 2,290 |
| 🍌 Banana  | 1,113        | 1,087       | 2,200 |
| 🥭 Guava   | 1,152        | 1,129       | 2,281 |
| 🍊 Orange  | 1,216        | 1,159       | 2,375 |
| **Total**  | **4,630**    | **4,516**   | **9,146** |

### Dataset Characteristics
- 📦 **Total Images**: 9,146
- 🏷️ **Classes**: 8 (4 fruit types × 2 quality conditions)
- 📏 **Image Resolution**: Variable (preprocessed to 224×224)
- 🎨 **Color Space**: RGB
- 📂 **Format**: JPEG/PNG

---

## 📈 Performance Metrics

### Model Performance Summary

| Metric | Training | Validation | Test |
|--------|----------|------------|------|
| **Fruit Type Accuracy** | 97.75% | 97.71% | 96.8% |
| **Quality Accuracy** | 98.21% | 99.18% | 98.5% |
| **Fruit F1-Score** | 0.978 | 0.976 | 0.972 |
| **Quality F1-Score** | 0.991 | 0.992 | 0.989 |
| **Combined Loss** | 0.2969 | 0.2435 | 0.2890 |

### Key Performance Indicators
- ✅ **High Accuracy**: >97% for both classification tasks
- ✅ **Excellent Generalization**: Minimal overfitting observed
- ✅ **Balanced Performance**: Consistent across all fruit categories
- ✅ **Multi-label Support**: Robust dual-head architecture

---

## 💻 Technical Stack

### Core Technologies
- **🧠 Deep Learning Framework**: TensorFlow 2.x + Keras
- **🏗️ Model Architecture**: Custom Multi-Head CNN
- **🔍 Explainability**: Grad-CAM (Gradient-weighted Class Activation Mapping)
- **🌐 Web Interface**: Streamlit
- **📸 Computer Vision**: OpenCV
- **📊 Data Processing**: NumPy, Pandas
- **📈 Visualization**: Matplotlib, Seaborn

### Development Environment
- **🐍 Python**: 3.8+
- **💾 Version Control**: Git
- **📝 Development**: Jupyter Notebooks
- **🔧 Package Management**: pip/conda

---

## 🛠️ Installation & Setup

### Prerequisites
```bash
# Python 3.8 or higher
python --version
```

### 1. Clone the Repository
```bash
git clone https://github.com/arpanpramanik2003/FruitQ-GradeX.git
cd FruitQ-GradeX
```

### 2. Create Virtual Environment (Recommended)
```bash
# Using venv
python -m venv fruitq_env

# Activate environment
# Windows
fruitq_env\Scripts\activate
# Linux/Mac
source fruitq_env/bin/activate
```

### 3. Install Dependencies
```bash
pip install -r requirements.txt
```

### 4. Download Dataset (Optional)
```bash
# Create data directory
mkdir data

# Place your fruit images in:
# data/
#   ├── Apple_Good/
#   ├── Apple_Bad/
#   ├── Banana_Good/
#   ├── Banana_Bad/
#   ├── Guava_Good/
#   ├── Guava_Bad/
#   ├── Orange_Good/
#   └── Orange_Bad/
```

### 5. Verify Installation
```bash
python -c "import tensorflow as tf; print('TensorFlow version:', tf.__version__)"
```

---

## 🚀 Usage

### Running the Streamlit Application

```bash
# Launch the web interface
streamlit run app.py
```

### Training the Model

```bash
# Train from scratch
python train_model.py

# Resume training from checkpoint
python train_model.py --resume --checkpoint model_checkpoint.h5
```

### Making Predictions

```python
from fruit_classifier import FruitClassifier

# Initialize model
classifier = FruitClassifier('models/best_model.h5')

# Predict single image
result = classifier.predict_image('path/to/fruit_image.jpg')
print(f"Fruit: {result['fruit']} ({result['fruit_confidence']:.2%})")
print(f"Quality: {result['quality']} ({result['quality_confidence']:.2%})")

# Get Grad-CAM visualization
heatmap = classifier.generate_gradcam('path/to/fruit_image.jpg')
```

### Web Interface Features
1. **📤 Upload Images**: Drag & drop or browse for fruit images
2. **📹 Live Camera**: Real-time webcam capture and prediction
3. **🎯 Predictions**: View fruit type and quality classifications
4. **📊 Confidence Scores**: Probability distributions for all classes
5. **🔍 Grad-CAM Heatmaps**: Visual explanations of model decisions
6. **📈 Batch Processing**: Upload multiple images for bulk analysis

### Example Output
```
📤 Input: apple_sample.jpg
🍎 Predicted Fruit: Apple (Confidence: 94.2%)
❌ Predicted Quality: Bad (Confidence: 87.6%)
🔍 Grad-CAM: Highlighting brown spots and texture irregularities
```

---

## 🧪 Model Architecture

### Multi-Head CNN Design
```
Input Layer (224, 224, 3)
    ↓
Conv2D Blocks (Feature Extraction)
    ↓
Global Average Pooling
    ↓
    ├── Fruit Head (Dense → Softmax)
    └── Quality Head (Dense → Sigmoid)
```

### Key Components
- **🏗️ Backbone**: Custom CNN with residual connections
- **🎯 Dual Heads**: Separate classification branches for fruit type and quality
- **🔄 Data Augmentation**: Rotation, zoom, brightness, horizontal flip
- **⚖️ Loss Function**: Combined categorical crossentropy and binary crossentropy
- **📈 Optimizer**: Adam with learning rate scheduling

---

## 🤝 Contributing

We welcome contributions! Here's how you can help:

### 📋 Contribution Guidelines

1. **🍴 Fork the Repository**
   ```bash
   git fork https://github.com/arpanpramanik2003/FruitQ-GradeX.git
   ```

2. **🌿 Create Feature Branch**
   ```bash
   git checkout -b feature/amazing-feature
   ```

3. **💻 Make Changes**
   - Follow PEP 8 style guidelines
   - Add docstrings to functions
   - Include unit tests for new features

4. **✅ Test Your Changes**
   ```bash
   python -m pytest tests/
   ```

5. **📝 Commit and Push**
   ```bash
   git commit -m "Add amazing feature"
   git push origin feature/amazing-feature
   ```

6. **🔄 Create Pull Request**

### 🎯 Areas for Contribution
- 🆕 Adding new fruit categories
- 🔧 Improving model architecture
- 🎨 Enhancing UI/UX design
- 📊 Adding more evaluation metrics
- 📚 Improving documentation
- 🐛 Bug fixes and optimizations

---

## 📄 License

**MIT License**

Copyright (c) 2025 Arpan Pramanik

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

---

## 📞 Contact

**Arpan Pramanik**
- 📧 **Email**: arpanpramanik2003@gmail.com
- 💼 **LinkedIn**: [linkedin.com/in/arpan-pramanik](https://linkedin.com/in/arpan-pramanik)
- 🐱 **GitHub**: [@arpanpramanik2003](https://github.com/arpanpramanik2003)

---

## 🙏 Acknowledgments

- 🎓 **Dataset Provider**: FruitNet Dataset contributors
- 🔬 **Research Inspiration**: Grad-CAM paper by Selvaraju et al.
- 🌟 **Framework**: TensorFlow and Keras communities
- 💡 **UI Framework**: Streamlit development team
- 📚 **Documentation**: GitHub community best practices

---

## 📈 Project Stats

![GitHub Stars](https://img.shields.io/github/stars/arpanpramanik2003/FruitQ-GradeX?style=social)
![GitHub Forks](https://img.shields.io/github/forks/arpanpramanik2003/FruitQ-GradeX?style=social)
![GitHub Issues](https://img.shields.io/github/issues/arpanpramanik2003/FruitQ-GradeX)
![GitHub Pull Requests](https://img.shields.io/github/issues-pr/arpanpramanik2003/FruitQ-GradeX)

---

<div align="center">

**⭐ Star this repository if you found it helpful! ⭐**

*Built with ❤️ by [Arpan Pramanik](https://github.com/arpanpramanik2003)*

</div>
