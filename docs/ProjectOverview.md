# Project Overview

This project demonstrates a deep learning-based workflow for analysing the microstructures of Ti-6Al-4V (Grade 5 titanium alloy), focusing on the automated assessment of grain size, volume fraction, and porosity. The aim is to replace time-intensive, manual techniques with a scalable, high-precision pipeline using modern computer vision tools.

---

## Methodology and Pipeline

The full workflow consists of the following key stages:

### 1. Data Sourcing and Preparation
- A curated dataset of over 1,000 microstructure images was assembled from academic sources, research databases, and published studies.
- Images included a range of grain morphologies and porosity levels across three microstructure types: equiaxed, lamellar, and martensitic.
- Each image was standardised to a resolution of 640×640px and 32-bit depth.
- Class balancing, resizing, and annotation (e.g. bounding boxes around grains and pores) were performed using Roboflow.

### 2. Microstructure Classification (CNN)
- A convolutional neural network (CNN) was trained to categorise each image as equiaxed, lamellar, or martensitic.
- This classification stage enabled conditional processing, where only equiaxed structures progressed to the grain detection pipeline.
- The CNN model was trained on a balanced 80/20 train-test split using stochastic gradient descent.

### 3. Grain Detection and Quantification (YOLOv8n)
- YOLOv8n was selected for its real-time object detection capabilities and anchor-free architecture.
- The model was trained to detect individual alpha grains in equiaxed microstructures.
- Post-processing included:
  - Calculation of average grain size using bounding box statistics
  - Volume fraction analysis by pixel-area ratio of detected grains to total image area

### 4. Porosity Analysis (OpenCV)
- Custom image processing scripts were developed to analyse pores:
  - Grayscale conversion, Gaussian blur, and median filtering
  - Binary thresholding and inversion to segment pore regions
  - Component labelling and shape classification (circular vs elliptical)
  - Surface roughness mapped in 3D from brightness gradients
- Outputs included pore count, eccentricity, area, and perimeter, with results expressed as a % of total image area.

### 5. Model Training and Evaluation
- YOLOv8n was trained on 200 annotated images (80% train, 10% test, 10% validation).
- Evaluation metrics included:
  - **CNN classifier**: mAP = 86.9%, F1 = 85.7%
  - **YOLOv8n grain detector**: mAP = 90.8%, F1 = 86.9%, Precision = 92.5%, Recall = 82.0%
- Analysis of false positives and under-detected grains was conducted to adjust detection thresholds.

### 6. Result Reporting and Visualisation
- Output images show labelled grains and pores with class confidence levels
- Quantitative summaries include:
  - Grain count, average grain size, and volume fraction
  - Pore classification (by shape), total area, and surface roughness
- Results are exported for visual inspection and benchmarking

---

## Summary

This project serves as a proof of concept for applying deep learning to automate microstructural analysis in materials science. By combining CNNs, YOLO-based detection, and traditional image processing, the pipeline enables faster, more consistent evaluation of alloy quality. While demonstrated on Ti-6Al-4V, the approach is generalisable to other materials with appropriate training data.

---

Developed by Ronan Banerji  
Dissertation submitted to Swansea University, 2024
