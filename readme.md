# Transfer Learning for Fashion-MNIST

## Objective  
The goal of this task is to **adapt a pretrained CNN model (like ResNet50)** to classify **28×28 grayscale Fashion-MNIST images into 10 categories**. This involves resizing images, adjusting channels, replacing the classification head, and performing fine-tuning.

---

## Implementation Details  

### Data Pipeline:
- **Resize images to 224×224** to match the input size of ResNet50/VGG16.
- **Convert grayscale (1 channel) to 3 channels** using duplication.

### Model Architecture:
- **Load a pretrained ResNet50 model** without its top fully connected (FC) layers.
- **Freeze the convolutional backbone** to use pretrained features.
- **Add a custom classifier head**:  
  - Flatten → FC(2048 → 512) → ReLU → Dropout → FC(512 → 10)
- Train only the new FC head initially and track validation metrics.

### 🔧 Fine-tuning:
- **Unfreeze deeper layers of the backbone**
- Fine-tune with a **lower learning rate**.
- Applied experiments:
  - **Data augmentation**
  - **Learning rate scheduling**
  - **Dropout regularization**
  - **Weight decay**

---

## What I Learned  

Through this assignment, I gained a hands-on understanding of **transfer learning concepts** and how to adapt large pretrained models for smaller, domain-specific tasks. I learned to carefully manage **freezing and unfreezing layers**, implement **custom heads**, and experiment with **regularization, data augmentation, and optimization techniques** to improve model performance.

---

## How to Run Locally  

- Clone the repo in your local environment and run each cell.
- If any errors occur while running locally, it might be because some libraries are preinstalled in Colab but may require manual installation locally.
