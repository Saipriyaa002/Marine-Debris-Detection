# Marine Debris Detection Using U-Net and Attention U-Net

## Overview

Marine debris, particularly plastic waste floating on oceans and coastal waters, poses a significant threat to marine ecosystems and biodiversity. Traditional monitoring approaches are costly, time-consuming, and limited in spatial coverage.

This project presents a deep learning-based framework for detecting marine debris from Sentinel-2 multispectral satellite imagery using semantic segmentation. The framework combines spectral feature engineering with U-Net and Attention U-Net architectures to accurately identify and localize marine debris in remote sensing images.

The project utilizes the MARIDA (Marine Debris Archive) dataset and integrates remote sensing indices such as NDVI, NDWI, and FDI to enhance debris detection performance.

---

## Objectives

* Detect marine debris from Sentinel-2 multispectral imagery.
* Improve feature representation using spectral indices.
* Perform pixel-level segmentation of debris regions.
* Compare the performance of U-Net and Attention U-Net architectures.
* Handle severe class imbalance in marine debris datasets.
* Generate image-level debris classification from segmentation outputs.

---

## Dataset

### MARIDA Dataset

The project uses the MARIDA (Marine Debris Archive) dataset, a benchmark dataset designed for marine debris detection using Sentinel-2 satellite imagery.

### Dataset Features

* Sentinel-2 multispectral image patches
* Pixel-level debris annotations
* Real-world marine environments
* Various environmental and weather conditions
* Marine debris and non-debris samples

---

## Technologies Used

| Category                | Tools & Libraries |
| ----------------------- | ----------------- |
| Programming Language    | Python            |
| Deep Learning           | TensorFlow, Keras |
| Remote Sensing          | Rasterio          |
| Numerical Computing     | NumPy             |
| Visualization           | Matplotlib        |
| Evaluation              | Scikit-learn      |
| Development Environment | Google Colab      |
| Dataset                 | MARIDA            |
| Satellite Data          | Sentinel-2        |

---

## Methodology

### 1. Data Preprocessing

* Loaded Sentinel-2 image patches using Rasterio.
* Extracted corresponding segmentation masks.
* Converted MARIDA annotations into binary debris masks.
* Performed train-validation splitting (70:30).
* Applied oversampling to debris-containing patches to reduce class imbalance.

---

### 2. Spectral Feature Engineering

The following spectral indices were computed:

#### NDVI (Normalized Difference Vegetation Index)

Used to distinguish vegetation from other land and water surfaces.

#### NDWI (Normalized Difference Water Index)

Used to enhance water body detection.

#### FDI (Floating Debris Index)

Designed specifically for identifying floating marine debris.

The final input feature stack consists of:

* Red Band
* Green Band
* Blue Band
* Near Infrared (NIR)
* NDVI
* NDWI
* FDI

Resulting in a 7-channel feature representation.

---

### 3. U-Net Architecture

The baseline segmentation model uses:

* Encoder-Decoder architecture
* Convolutional layers
* Max Pooling
* Skip Connections
* Pixel-wise prediction

#### Advantages

* Lightweight architecture
* Effective for small datasets
* Strong segmentation baseline

---

### 4. Attention U-Net Architecture

An enhanced version of U-Net incorporating Attention Gates.

#### Key Features

* Attention Mechanisms
* Improved Feature Localization
* Suppression of Irrelevant Background Regions
* Better Focus on Debris Areas

#### Benefits

* Improved segmentation accuracy
* Reduced false positives
* Enhanced debris localization

---

### 5. Hybrid Loss Function

To address extreme class imbalance, a custom loss function was implemented:

Loss = Weighted Binary Cross Entropy + Dice Loss + Focal Loss

#### Components

* Weighted Binary Cross Entropy (WBCE)
* Dice Loss
* Focal Loss

This combination improves learning on minority debris pixels while maintaining segmentation quality.

---

## Evaluation Metrics

Performance was evaluated using:

* Intersection over Union (IoU)
* Dice Coefficient
* Precision
* Recall
* F1 Score
* Classification Accuracy

---

# Results

## U-Net Performance

| Metric                  | Score |
| ----------------------- | ----- |
| IoU                     | 0.612 |
| Dice Score              | 0.627 |
| Precision               | 0.638 |
| Recall                  | 0.942 |
| F1 Score                | 0.686 |
| Classification Accuracy | 75%   |

---

## Attention U-Net Performance

| Metric                  | Score |
| ----------------------- | ----- |
| IoU                     | 0.753 |
| Dice Score              | 0.764 |
| Precision               | 0.833 |
| Recall                  | 0.885 |
| F1 Score                | 0.793 |
| Classification Accuracy | 80%   |

---

## Comparative Analysis

| Metric     | U-Net | Attention U-Net |
| ---------- | ----- | --------------- |
| IoU        | 0.612 | 0.753           |
| Dice Score | 0.627 | 0.764           |
| Precision  | 0.638 | 0.833           |
| Recall     | 0.942 | 0.885           |
| F1 Score   | 0.686 | 0.793           |
| Accuracy   | 75%   | 80%             |

### Key Findings

* Attention U-Net achieved superior segmentation performance.
* Spectral feature fusion improved marine debris discrimination.
* Attention mechanisms enhanced localization capability.
* Hybrid loss functions effectively addressed class imbalance.
* Attention U-Net produced fewer false positives compared to baseline U-Net.

---

## Project Structure

```text
Marine-Debris-Detection/
│
├── notebooks/
│   ├── UNET_Segmentation.ipynb
│   ├── UNET_Classification.ipynb
│   ├── Attention_UNET_Segmentation.ipynb
│   └── Attention_UNET_Classification.ipynb
│
├── results/
│   ├── IoU_Curve.png
│   ├── Loss_Curve.png
│   ├── Heatmaps.png
│   ├── Predictions.png
│   └── Confusion_Matrix.png
│
├── README.md
├── requirements.txt
└── Dataset_Link.txt
```

---

## How to Run

### Clone Repository

```bash
git clone https://github.com/yourusername/Marine-Debris-Detection.git
cd Marine-Debris-Detection
```

### Install Dependencies

```bash
pip install -r requirements.txt
```

### Open Google Colab

Upload and run:

* UNET_Segmentation.ipynb
* UNET_Classification.ipynb
* Attention_UNET_Segmentation.ipynb
* Attention_UNET_Classification.ipynb

### Configure Dataset Path

Update:

```python
BASE_PATH = "/content/drive/MyDrive/MARIDA"
```

to match your Google Drive dataset location.

---

## Future Work

* Transformer-Based Segmentation Models
* Swin U-Net Integration
* Real-Time Marine Debris Monitoring
* Explainable AI (XAI)
* Multi-Class Marine Object Detection
* Deployment as a Web Application

---

## 👨‍💻 Author

**Sai Priyaa M, J Cindrelaa** 

Computer Science and Engineering Student

Deep Learning | Computer Vision | Remote Sensing | Artificial Intelligence

---

## License

This project is intended for academic and research purposes.

Please cite the MARIDA dataset and related references when using this work.

---

If you find this project useful, please consider giving this repository a star.
