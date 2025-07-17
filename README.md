# Microstructural Analysis Automation Tool

This project uses deep learning to analyse micrographs of Ti-6Al-4V (Grade 5 titanium alloy), automating the evaluation of grain size, volume fraction, and porosity.

A convolutional neural network (CNN) is used to classify the microstructure (equiaxed, lamellar, or martensitic), while YOLOv8 detects and measures grains. Porosity is assessed through image processing techniques. Together, the tools reduce manual workload and improve speed and consistency over traditional methods.

## Why It Matters
Grain characteristics and porosity are critical to the strength, durability, and performance of alloys. Automating this analysis supports efficient, scalable quality control in industrial and research settings.

## Features
- Classifies alloy microstructure types
- Detects and measures grain features
- Calculates porosity and surface roughness
- Outputs geometric and statistical summaries

## Tools
- Python
- YOLOv8 (Ultralytics)
- TensorFlow / Keras
- OpenCV
- Jupyter Notebooks

## Model Architecture

### Microstructure Classification (CNN)
A custom convolutional neural network (CNN) is used to classify microstructure images into one of three categories: equiaxed, lamellar, or martensitic. The architecture includes:
- 8 convolutional layers with 3×3 kernels
- Max pooling layers with 2×2 stride
- ReLU activation throughout
- Softmax activation at the output
- Trained on 64×64 RGB images using SGD (learning rate: 0.01)

### Grain Detection (YOLOv8n)
The YOLOv8n model is used to detect and measure alpha grains in equiaxed microstructures. Key features:
- Anchor-free detection head
- Grid-based detection (s×s cells)
- Bounding box predictions include position, size, and class confidence
- Loss function includes coordinate, size, objectness, and classification terms
- Trained on 640×640 annotated images using 500 epochs

### Porosity Analysis
A custom image processing pipeline is used to segment and analyse pores:
- Grayscale conversion and noise reduction
- Thresholding and component analysis
- Classification of pore shape (circular vs elliptical)
- Surface roughness visualisation via 3D mapping
- Outputs quantitative metrics including pore count, area, perimeter, and porosity percentage

Each model is trained and evaluated independently, then integrated into a single analysis pipeline.

## Performance
| Model             | mAP   | F1 Score | Precision | Recall |
|------------------|-------|----------|-----------|--------|
| CNN (classifier) | 86.9% | 85.7%    | 97.2%     | 76.6%  |
| YOLOv8n (grains) | 90.8% | 86.9%    | 92.5%     | 82.0%  |

---

Developed by Ronan Banerji. Dissertation submitted to Swansea University, 2024.
