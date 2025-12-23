# Tree Count
# Urban Tree Counting using Density Map Regression 🌳

This project presents a **research-grade approach** for estimating and analyzing urban tree populations from high-resolution satellite imagery using **density map regression** and **spatial analysis**.

Unlike object detection methods (YOLO, Faster R-CNN), this system treats tree counting as a **density estimation problem**, making it robust in **dense, cluttered urban environments** where individual tree detection is unreliable.

---

## 📌 Key Features

- Density map–based tree counting (not bounding boxes)
- Encoder–Decoder CNN (U-Net style) implemented in **PyTorch**
- Robust to dense canopies and partial occlusions
- Converts density maps into tree locations using **peak detection**
- Object-level evaluation with precision, recall, F1-score
- Web deployment using **Gradio**
- GIS-compatible outputs for further spatial analysis

---

## 🧠 Methodology Overview

1. **Data Preparation**
   - High-resolution satellite images of Bangalore
   - Tree locations manually annotated as point features in QGIS
   - CSV annotations converted into Gaussian density maps

2. **Model Architecture**
   - U-Net–style Encoder–Decoder CNN
   - Input: RGB image (256 × 256)
   - Output: Single-channel density map
   - Loss function: Mean Squared Error (MSE)

3. **Training Strategy**
   - Density regression instead of classification
   - Count preservation enforced via density integration
   - Data augmentation for robustness

4. **Inference & Post-Processing**
   - Density map prediction
   - Negative values clamped to zero
   - Adaptive thresholding
   - Peak detection to extract tree locations

5. **Evaluation**
   - Count-based metrics: MAE, RMSE, R²
   - Object-level detection metrics
   - Confusion matrix (TP, FP, FN)
   - Visual and quantitative validation

---

## 📊 Evaluation Metrics

### Count-Based Metrics
- **Mean Absolute Error (MAE)**
- **Root Mean Square Error (RMSE)**
- **R² Score**

### Object-Level Detection Metrics
- Precision
- Recall
- F1-score
- Accuracy (object-level)

> Note: Pixel-level confusion matrices are not used due to extreme background class imbalance. Evaluation is performed at the **object (tree) level**, which is standard for density-based counting methods.

---

## 🗂 Project Structure

