# Microstructural Analysis Automation Tool

This project uses deep learning to analyse micrographs of Ti-6Al-4V (Grade 5 titanium alloy), automating the evaluation of grain size, volume fraction, and porosity.

A convolutional neural network (CNN) is used to classify the microstructure (equiaxed, lamellar, or martensitic), while YOLOv8 detects and measures grains. Porosity is assessed through image processing techniques. Together, the tools reduce manual workload and improve speed and consistency over traditional methods.

## Features
- Classifies alloy microstructure types
- Detects and measures grain features
- Calculates porosity and surface roughness
- Outputs geometric and statistical summaries

## Why It Matters
Grain characteristics and porosity are critical to the strength, durability, and performance of alloys. Automating this analysis supports efficient, scalable quality control in industrial and research settings.

## Tools
- Python
- YOLOv8 (Ultralytics)
- TensorFlow / Keras
- OpenCV
- Jupyter Notebooks

## Performance
| Model             | mAP   | F1 Score | Precision | Recall |
|------------------|-------|----------|-----------|--------|
| CNN (classifier) | 86.9% | 85.7%    | 97.2%     | 76.6%  |
| YOLOv8n (grains) | 90.8% | 86.9%    | 92.5%     | 82.0%  |

---

Developed by Ronan Banerji. Dissertation submitted to Swansea University, 2024.
