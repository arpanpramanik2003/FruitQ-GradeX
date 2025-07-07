# 🍎🍌🍊 Fruit Type and Quality Classification using CNN + Grad-CAM

## 🚀 Overview  
A deep learning system that classifies fruit images by both **type** (Apple, Banana, Guava, Orange) and **quality** (Good or Bad). Built using a **multi-headed CNN**, the system also integrates **Grad-CAM** for interpretability and features a user-friendly **Streamlit interface** for real-time predictions.  

## 💻 Technical Stack  
- **Framework**: TensorFlow 2.x + Keras  
- **Model Architecture**: Custom Multi-Head CNN  
- **Data Augmentation**: ImageDataGenerator with brightness, shift, zoom, flip, etc.  
- **Explainable AI**: Grad-CAM visualization for both fruit and condition heads  
- **Interface**: Streamlit Web App with OpenCV integration  
- **Data Source**: FruitNet (Indian Fruits Dataset with Quality Labels)

## 📊 Dataset Summary  
The dataset includes 8 categories:  
| Class         | Image Count |
|---------------|-------------|
| Apple_Good    | 1149        |
| Apple_Bad     | 1141        |
| Banana_Good   | 1113        |
| Banana_Bad    | 1087        |
| Guava_Good    | 1152        |
| Guava_Bad     | 1129        |
| Orange_Good   | 1216        |
| Orange_Bad    | 1159        |

📦 **Total Images**: 9146  

---

## 📈 Performance Metrics  

| Metric               | Training | Validation |
|----------------------|----------|------------|
| Fruit Accuracy       | 97.75%   | 97.71%     |
| Condition Accuracy   | 98.21%   | 99.18%     |
| Fruit F1-Score       | 0.98     | 0.98       |
| Condition F1-Score   | 0.99     | 0.99       |
| Combined Loss        | 0.2969   | 0.2435     |

✅ Supports multi-label prediction  
✅ Shows excellent generalization to unseen fruit images  

---

## ✨ Key Features  

- **Dual Prediction**: Classifies both fruit type and quality condition simultaneously  
- **Explainability**: Grad-CAM visual heatmaps highlight important regions for decisions  
- **Real-time Inference**: Predict via webcam or uploaded image using Streamlit  
- **User Interface**: Clean and responsive UI with confidence scores  
- **Custom Data Pipeline**: Class-based folder creation and smart augmentation  

---

## 🧪 Explainability with Grad-CAM  

- Integrated Grad-CAM for both output heads  
- Visual feedback helps understand what parts of the image influenced the prediction  
- Highlights defects or ripeness areas in fruits  

---

## 🌐 Streamlit Interface  

- Upload fruit images or use live webcam capture  
- Displays predicted fruit name and quality label  
- Shows Grad-CAM heatmaps  

📤 **Output Example:**  
- Predicted Fruit: Apple
- Predicted Condition: Bad
- Confidence: [Apple: 92.1%, Bad: 96.4%]

---

Copyright (c) 2025 Arpan Pramanik

Permission is hereby granted, free of charge, to any person obtaining a copy  
of this software and associated documentation files (the "Software"), to deal  
in the Software without restriction, including without limitation the rights  
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell  
copies of the Software, and to permit persons to whom the Software is  
furnished to do so, subject to the following conditions:  

The above copyright notice and this permission notice shall be included in  
all copies or substantial portions of the Software.  

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR  
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,  
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE  
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER  
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,  
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN  
THE SOFTWARE.
