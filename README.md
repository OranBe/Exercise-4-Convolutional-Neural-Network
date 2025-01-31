# Exercise 4 - Flower Classification Using CNNs

### GitHub Repository

[GitHub Repository Link](https://github.com/OranBe/Exercise-4-Convolutional-Neural-Network)

## Overview

This project involves using Convolutional Neural Networks (CNNs) to classify flowers into categories based on their images. The models utilized are **YOLOv5** and **VGG19**, both of which leverage **transfer learning** to improve classification accuracy.

## Dataset

The dataset used for training and evaluation is the **Oxford 102 Flowers dataset**:
[Oxford 102 Flowers Dataset](https://www.robots.ox.ac.uk/~vgg/data/flowers/102/)

## Data Preprocessing

1. **Download and organize images**: Images are sorted into folders based on their categories.
2. **Dataset splitting**: The dataset is divided into:
   - **50% Training**
   - **25% Validation**
   - **25% Testing**
     The test set remains consistent across experiments to ensure fair evaluation.
3. **Image Transformations**:
   - Resize images to **224x224** pixels.
   - Convert images to **PyTorch tensors**.
   - Normalize images using ImageNet mean and standard deviation values:
     - Mean: `[0.485, 0.456, 0.406]`
     - Std Dev: `[0.229, 0.224, 0.225]`
4. **Data Loading**:
   - DataLoader objects are created to efficiently load images during training.
   - Training data is shuffled to introduce randomness and prevent overfitting.

## Model Architectures

### **VGG19**

- Uses 19 weight layers (convolutional + fully connected layers).
- The last layer is replaced with a new classifier tailored for the flower classification task:
  - Fully connected layer reducing dimensions from `4096 -> 512`
  - ReLU activation
  - Dropout layer (0.5)
  - Output layer (matching the number of flower categories)

### **YOLOv5**

- The final detection layer is replaced with a classification layer.
- **Pre-trained weights** from YOLOv5 are utilized, and only the classification layers are trained.
- The model is optimized to output class probabilities instead of object detection results.

## Training and Hyperparameter Tuning

### **VGG19 Best Parameters**:

- **Learning Rate**: `0.0001`
- **Batch Size**: `32`
- **Optimizer**: Adam

### **YOLOv5 Best Parameters**:

- **Learning Rate**: `0.001`
- **Batch Size**: `16`
- **Optimizer**: SGD

---

**Contributors:**

- Noy Gabay
- Oran Becker

For further details, refer to the `report4.pdf` file included in the submission.


