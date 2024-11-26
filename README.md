# Blood Cell Multiclass Classification Challenge

## Competition Performance
- **Rank**: 11th out of 200+ teams
- **Final Test Set Accuracy**: 0.95

## Overview
This project is a comprehensive deep learning solution for multiclass blood cell image classification, developed as part of the 2024-2025 Artificial Neural Networks and Deep Learning course. The challenge was hosted on Codabench, an external deep learning challenges platform, requiring participants to develop a robust machine learning model for accurate blood cell classification.

## Team
- **Members**:
  - Francesco Palma
  - Francesco Pellegrini
  - Luigi Raggi

## Problem Statement
### Dataset Characteristics
- **Type**: Blood cell image dataset
- **Challenges**:
  - Class imbalance
  - Presence of outlier images
  - Limited dataset size
  - High similarity between classes
  - Modified test dataset

### Initial Data Analysis
- Conducted thorough exploratory data analysis
- Identified and removed outlier images
- Visualized class distribution and pixel brightness

## Methodology

### Model Architecture
#### Backbone Model: EfficientNetV2L
- **Selection Rationale**:
  - Optimized training speed
  - Parameter efficiency
  - Advanced feature extraction capabilities
  - Particularly suitable for medical image tasks
  - Incorporates Squeeze-and-Excitation (SE) layers for adaptive feature emphasis

#### Model Structure
- **Feature Extraction Phase**:
  - Frozen model layers
  - Trained only the model head
- **Fine-Tuning Phase**:
  - Gradually unfroze selected layers
  - Carefully selected number of layers to unfreeze for optimal performance

### Advanced Techniques

#### Data Augmentation
- **Approach**: Online random augmentation
- **Technique**: RandAugment from keras-cv library
  - Randomly selects and applies three different transformations
  - Ensures maximum diversity in training data
- **Benefits**:
  - Improved model generalization
  - Increased robustness to variations in input images

#### Optimization Strategies
- **Optimizer**: AdamW
  - Improved generalization performance
  - Enhanced regularization

- **Loss Function**: Focal Loss
  - Addressed class imbalance
  - Down-weighted loss for well-classified examples
  - Improved learning for minority classes

#### Learning Rate Management
- **Feature Extraction Phase**:
  - Fixed learning rate: 1e-4
  - ReduceLROnPlateau callback to adjust learning rate
- **Fine-Tuning Phase**:
  - Cosine decay scheduler with restarts
  - Initial learning rate: 1e-5
  - Prevented catastrophic forgetting of learned features

## Performance Evaluation

### Model Accuracy Progression
| Model | Test Accuracy |
|-------|---------------|
| VGG19 | 0.55 |
| ConvNeXtLarge | 0.77 |
| EfficientNetV2L | 0.95 |

### Detailed Performance Metrics
- **Competition Dataset Accuracy**: 0.95
- **Local Test Set Accuracy**: 0.9833
- **Ranking**: 11th out of 200 competing teams

### Confusion Matrix Insights
- Most misclassifications occurred between classes 3 and 6
- Highlighted areas for potential future improvement

## Technical Challenges and Solutions
1. **Class Imbalance**
   - Addressed using Focal Loss
   - Carefully designed data augmentation

2. **Model Selection**
   - Systematically evaluated multiple backbones
   - Chose EfficientNetV2L for optimal performance and efficiency

3. **Fine-Tuning Strategy**
   - Developed a nuanced approach to layer unfreezing
   - Identified optimal depth for model adaptation

## Technologies and Libraries
- TensorFlow
- Keras
- Keras-CV
- NumPy
- AdamW Optimizer
- Focal Loss Implementation

## Future Work
- Improve classification between problematic classes
- Explore more advanced augmentation techniques
- Investigate ensemble methods
- Develop more sophisticated regularization strategies

## Key Learnings
- Importance of backbone model selection
- Impact of sophisticated data augmentation
- Critical role of fine-tuning strategies
- Addressing class imbalance through advanced loss functions

## Acknowledgments
Special thanks to the course instructors and the Codabench platform for providing this challenging and educational machine learning competition.

---

*Artificial Neural Networks and Deep Learning Course Project*
*November 2024*
