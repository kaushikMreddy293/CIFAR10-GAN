# ConvGAN-CIFAR10: Exploring Noise Vector Control in Image Synthesis with Generative Adversarial Network

## 📌 Overview

This project investigates the impact of convolutional architectures and noise vector dimensions in Generative Adversarial Networks (GANs) for image synthesis. Using the "Horse" class from the CIFAR-10 dataset, the research demonstrates how different latent space configurations affect the quality and diversity of generated images.

## 🎯 Project Objectives

- Enhance GAN architecture by implementing convolutional and transposed convolutional layers
- Generate realistic images specifically from the CIFAR-10 "Horse" class
- Analyze the effects of different noise vector dimensions on image quality and generation stability
- Compare visual results across multiple latent dimension configurations

## 🔧 Model Architecture

### Generator
- **Input**: Random noise vector (variable latent dimensions tested)
- **Architecture**: Multiple ConvTranspose2d layers with increasing feature maps
- **Normalization**: Batch normalization between layers
- **Activations**: ReLU for hidden layers, Tanh for output layer
- **Output**: 3×32×32 RGB image normalized to [-1, 1] range

### Discriminator
- **Input**: 3×32×32 RGB image (real or generated)
- **Architecture**: Multiple Conv2d layers with decreasing feature maps
- **Normalization**: Batch normalization between layers
- **Activations**: LeakyReLU for hidden layers, Sigmoid for final classification
- **Output**: Binary classification (real vs. fake)

## 📊 Data Preparation

- **Dataset**: CIFAR-10
- **Class Selection**: Filtered to include only class 7 (Horse)
- **Preprocessing**: 
  - Normalization to pixel range [-1, 1]
  - Reshaped to 3×32×32 format
  - Applied data augmentation techniques

## 💻 Implementation Details

- **Loss Function**: Binary Cross Entropy Loss (BCELoss)
- **Optimization**: Adam optimizer
  - Learning rate: 0.0002
  - Betas: (0.5, 0.999)
- **Training Parameters**:
  - Epochs: 100
  - Batch size: 64
  - GPU acceleration where available

## 🔍 Experimental Results

### Noise Vector Analysis

| Latent Dimension | Image Quality | Observations |
|------------------|---------------|--------------|
| 1                | Poor          | No proper images, extremely limited diversity |
| 50               | Excellent     | Best visibility, clear images with good variation |
| 100              | Excellent     | Best visibility, stable and consistent outputs |
| 200              | Good          | Some distortions, slight reduction in clarity |
| 500              | Poor          | Significant distortions, unstable generation |

### Key Findings

- **Optimal Latent Space**: Dimensions between 50-100 provide the best balance of quality and diversity
- **Small Dimensions**: Extremely low dimensions (e.g., 1) cannot capture the complexity of the data distribution
- **Large Dimensions**: Excessively high dimensions (e.g., 500) introduce instability and noise in generation
- **Visual Quality**: Successfully generated recognizable horse images with appropriate architecture and noise dimension

## 📷 Sample Results

Experiment results in pdf in repository

<img width="397" alt="image" src="https://github.com/user-attachments/assets/78de0f78-06af-4d57-adff-8da543313d6e" />


## 🚀 How to Run

1. Download the Python Notebook
2. Run on Google Collab or Jupyter 

## 📚 Requirements

```
torch>=1.7.0
torchvision>=0.8.1
numpy>=1.19.2
matplotlib>=3.3.2
```

## 🔮 Future Work

- Explore conditional GAN architectures to control specific features of horse images
- Implement progressive growing techniques for higher resolution outputs
- Apply style transfer methods to generate horses in different artistic styles
- Investigate techniques to improve training stability at higher latent dimensions
- Experiment on other classes of CIFAR 10

## 👤 Author

- Kaushik Malikireddy

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.
