# **Brain Tissue Segmentation Using DenseUNet and SwinUNetR**

## **Overview**
This project focuses on the segmentation of brain tissues into four distinct classes: background, cerebrospinal fluid (CSF), gray matter (GM), and white matter (WM). The segmentation models include the DenseUNet and SwinUNetR architectures. The dataset used is IBSR18, which contains 3D MRI scans of human brains. Evaluation metrics such as Dice Similarity Coefficient (DSC), Hausdorff Distance (HD), and Volumetric Difference (VD) are utilized to assess model performance.

---

## **Folder Structure**
```
Submission/
├── models/                             # Contains model implementation scripts
│   ├── 2DDenseUNet.ipynb               # Notebook implementing 2D DenseUNet for segmentation
│   ├── MONAI.ipynb                     # Notebook leveraging MONAI for medical image segmentation
│
├── Dataset_Final/                      # Dataset directory for segmentation tasks
│   ├── train/                          # Training dataset
│   │   ├── image_1.nii.gz              # Example training image
│   │   ├── image_2.nii.gz              # Example training image
│   │   ├── ...                         # More training images
│   ├── val/                            # Validation dataset
│   │   ├── image_1.nii.gz              # Example validation image
│   │   ├── image_2.nii.gz              # Example validation image
│   │   ├── ...                         # More validation images
│   ├── test/                           # Testing dataset
│   │   ├── image_1.nii.gz              # Example test image
│   │   ├── image_2.nii.gz              # Example test image
│   │   ├── ...                         # More test images
```

---

## **Dataset Description**

### **IBSR18 Dataset**
- **Source**: Internet Brain Segmentation Repository (IBSR18).
- **Description**: 3D T1-weighted MRI scans used for brain tissue segmentation.
- **Segmentation Classes**:
  - **Class 0**: Background.
  - **Class 1**: Cerebrospinal Fluid (CSF).
  - **Class 2**: Gray Matter (GM).
  - **Class 3**: White Matter (WM).

- **Dataset Structure**:
  - **Train Set**: Contains MRI scans with ground truth segmentations.
  - **Validation Set**: Includes MRI scans with ground truth labels for performance evaluation.
  - **Test Set**: Contains MRI scans without ground truth labels (used for external evaluation in competitions).

- **Preprocessing**:
  - Normalization and resizing of images to a consistent resolution.
  - Conversion of 3D MRI volumes into 2D slices for processing.
  - Augmentations such as rotation and flipping applied for model robustness.

---

## **File Descriptions**

### **Models**
1. **`2DDenseUNet.ipynb`**:
   - Implements the DenseUNet architecture for brain tissue segmentation.
   - Uses dense blocks and skip connections for efficient feature extraction.
   - Processes 2D slices derived from the 3D MRI dataset.

2. **`MONAI.ipynb`**:
   - Utilizes the MONAI framework to implement SwinUNetR.
   - Leverages hierarchical transformer-based architecture for improved segmentation accuracy.
   - Applies MONAI's built-in data transformations and evaluation metrics.

### **Dataset_Final**
- **train/**:
  - Contains preprocessed MRI slices and ground truth masks for training.
- **val/**:
  - Contains MRI slices and ground truth masks for validation.
- **test/**:
  - Contains MRI slices for testing (no ground truth provided).

---

## **Evaluation Metrics**

### **Metrics Used**
1. **Dice Similarity Coefficient (DSC)**:
   - Measures the overlap between predicted and ground truth masks.
   - Ranges from 0 (no overlap) to 1 (perfect overlap).

2. **Hausdorff Distance (HD)**:
   - Captures the maximum distance between the boundaries of predicted and ground truth masks.

3. **Volumetric Difference (VD)**:
   - Measures the volume difference between predicted and ground truth regions.

---

## **Results**

### **SwinUNetR (MONAI Framework)**
#### **Validation Set Metrics**:
- **Class 0**:
  - Dice Coefficient: **0.9490**
  - Hausdorff Distance: **19.4543**
  - Volumetric Difference: **0.0205**
- **Class 1**:
  - Dice Coefficient: **0.9019**
  - Hausdorff Distance: **19.6174**
  - Volumetric Difference: **0.0239**
- **Class 2**:
  - Dice Coefficient: **0.9370**
  - Hausdorff Distance: **9.0282**
  - Volumetric Difference: **0.0124**
- **Class 3**:
  - Dice Coefficient: **0.9400**
  - Hausdorff Distance: **7.6924**
  - Volumetric Difference: **0.0220**

### **DenseUNet**
#### **Hyperparameters**:
- Batch size: **64**
- Dropout: **0.40**
- Epochs: **200**

#### **Validation Set Metrics**:
- **Class 0**: Dice Coefficient: **0.9975**
- **Class 1**: Dice Coefficient: **0.8342**
- **Class 2**: Dice Coefficient: **0.9209**
- **Class 3**: Dice Coefficient: **0.8825**

---

## **How to Use**

### **Dataset Preparation**
1. Place the dataset files in the `Dataset_Final/` directory under appropriate subfolders (`train/`, `val/`, `test/`).
2. Ensure the file format is compatible (e.g., `.nii.gz`).

### **Run Models**
1. **DenseUNet**:
   - Open and execute the `2DDenseUNet.ipynb` notebook.
   - Follow the notebook to preprocess data, train the model, and evaluate results.

2. **SwinUNetR**:
   - Open and execute the `MONAI.ipynb` notebook.
   - Utilize MONAI's built-in utilities for training and evaluation.

---

## **Contact**
For questions or feedback, feel free to raise an issue or contact the repository owner.
