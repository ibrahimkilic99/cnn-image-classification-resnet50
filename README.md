# cnn-image-classification-resnet50
Deep learning image classification using ResNet-50 CNN architecture on Intel Image dataset. Achieved 87% accuracy classifying landscape images into 6 categories using PyTorch.

# CNN Image Classification with ResNet-50

## Project Overview

Deep learning image classification project using ResNet-50 Convolutional Neural Network architecture to classify landscape images into 6 categories: buildings, forest, glacier, mountain, sea, and street. Achieved **87.2% validation accuracy** using PyTorch and transfer learning.

## Key Results

### Model Performance
- **Training Accuracy:** 87.2% (final epoch)
- **Validation Accuracy:** 87.2%
- **Training Loss:** 0.1317 (final epoch)
- **Validation Loss:** 0.3922
- **Architecture:** ResNet-50 (pretrained on ImageNet)
- **Training Time:** 10 epochs (~3.6-3.7 sec/epoch)

### Dataset
- **Source:** Intel Image Classification Dataset
- **Total Images:** 25,000+
- **Classes:** 6 (buildings, forest, glacier, mountain, sea, street)
- **Image Size:** 224x224 pixels (resized)
- **Split:** Training set + Validation set

### Classification Performance by Class
- **Forest:** Highest accuracy (389/400 correct)
- **Street:** Strong performance (383/400 correct)
- **Sea:** Good performance (364/400 correct)
- **Mountain:** Moderate performance (336/400 correct)
- **Buildings:** Some confusion with street scenes (272/400 correct)
- **Glacier:** Confusion with mountain/sea (221/400 correct)

## Tools & Technologies

- **Deep Learning Framework:** PyTorch
- **Model Architecture:** ResNet-50 (Residual Neural Network)
- **Libraries:** 
  - torch, torchvision
  - matplotlib, tqdm
- **Techniques:**
  - Transfer Learning (pretrained weights)
  - Data Augmentation
  - Cross-Entropy Loss
  - Adam Optimizer
  - ReLU Activation

## Project Structure

├── presentation.pdf              # Project presentation slides
├── image_classification.ipynb    # Training notebook 
└── README.md                     # Project documentation

## Model Architecture: ResNet-50

### Why ResNet-50?
ResNet-50 is a deep CNN architecture that:
- Uses **residual connections** to solve vanishing gradient problem
- Enables training of very deep networks (50+ layers)
- Pretrained on ImageNet (1.2M images, 1000 classes)
- Industry standard for image classification tasks

### Key Components
1. **Convolutional Layers:** Feature extraction
2. **Residual Blocks:** Skip connections for gradient flow
3. **Batch Normalization:** Training stability
4. **ReLU Activation:** Non-linearity
5. **Fully Connected Layer:** Final classification (6 classes)

## Training Process

### Configuration
- **Epochs:** 10
- **Batch Size:** 32
- **Learning Rate:** 0.001
- **Optimizer:** Adam
- **Loss Function:** CrossEntropyLoss

### Training Progression
| Epoch | Train Loss | Val Loss | Val Accuracy |
|-------|------------|----------|--------------|
| 1 | 0.1270 | 0.3720 | 87.9% |
| 2 | 0.1342 | 0.4020 | 86.8% |
| 5 | 0.1380 | 0.3970 | 87.4% |
| 10 | 0.1317 | 0.3922 | **87.2%** |

### Observations
- Model converged quickly due to transfer learning
- Validation loss slightly higher than training (expected)
- Stable performance across epochs
- Some overfitting after epoch 5 (minor)

## Error Analysis

### Common Misclassifications
1. **Buildings ↔ Street:** Architectural similarity in urban scenes
2. **Glacier ↔ Mountain:** Snow-covered peaks look similar
3. **Sea ↔ Glacier:** White/blue color similarity in certain lighting

### Example Misclassifications
- Prediction: sea, True: buildings (riverside building)
- Prediction: street, True: buildings (night shot of buildings)
- Prediction: street, True: buildings (upward angle of tall buildings)

These errors are understandable given visual similarity in edge cases.

## Technical Highlights

### Transfer Learning Benefits
- **Faster convergence:** Leveraged pretrained ImageNet weights
- **Better accuracy:** Pre-learned features for general image recognition
- **Less data needed:** Effective even without millions of training images

### Data Preprocessing
- Image resizing to 224×224 (ResNet standard input)
- Normalization using ImageNet mean/std
- Random augmentation (if applied)

### Automatic Differentiation
- PyTorch autograd for backpropagation
- Efficient gradient computation through computational graph
- Automatic parameter updates via optimizer

## Confusion Matrix Insights

The confusion matrix reveals:
- **Diagonal dominance:** Most predictions are correct
- **Forest class:** Best performance (most clearly distinguished)
- **Glacier class:** Most challenging (visual similarity with mountain/sea)
- **Urban scenes:** Some confusion between buildings and streets (expected)

## Potential Improvements

1. **Data augmentation:** Rotation, flipping, color jittering
2. **Longer training:** 20-30 epochs with learning rate scheduling
3. **Fine-tuning:** Unfreeze earlier ResNet layers
4. **Ensemble methods:** Combine multiple models
5. **Class balancing:** Address any dataset imbalances

## Key Learnings

1. **Transfer learning is powerful:** Achieved 87%+ accuracy with minimal training
2. **ResNet architecture solves deep learning challenges:** Residual connections enable deep networks
3. **Visual similarity drives errors:** Understandable misclassifications in edge cases
4. **Pretrained models accelerate development:** Hours instead of days of training

---

*Dataset: Intel Image Classification Dataset*  
*Model: ResNet-50 (He et al., 2015)*
