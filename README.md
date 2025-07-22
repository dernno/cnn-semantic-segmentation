This project focuses on semantic segmentation of biomedical images, specifically identifying **glandular structures** at the **pixel level**. Rather than classifying entire images, the models perform **binary segmentation**, labeling each pixel as either **"gland"** or **"non-gland"**.

## Loss Functions

Two different loss functions are implemented and can be used interchangeably:

- `torch.nn.BCEWithLogitsLoss()` – standard binary cross-entropy loss with logits  
- `monai.losses.DiceCELoss` – combined Dice and Cross-Entropy loss from MONAI

## Architectures

Multiple CNN-based architectures are available for experimentation:

- **Base CNN** – a simple convolutional encoder-decoder network for binary pixel-wise classification (sigmoid), using downsampling via max pooling and upsampling via transposed convolutions 
- **U-Net** – with skip connections between encoder and decoder blocks at different levels to preserve spatial information  
- **ResNet-based model** – using residual connections to enable deeper networks and improve gradient flow

These variations allow comparison of performance across different architectural designs.

## Training 

<img width="999" height="410" alt="Image" src="https://github.com/user-attachments/assets/d4f10d19-0ca6-4aec-9425-9884c0be4a7c" />

## Evaluation & Visualization

The segmentation performance is evaluated using **Dice score**. After training, the **best and worst segmentation results** (based on Dice score) from the **last 12 epochs** are visualized.  It is observed that all networks tend to struggle more with **darker images**, leading to lower segmentation accuracy in those cases.

<img width="950" height="350" alt="Image" src="https://github.com/user-attachments/assets/f4c54a3b-1ac1-498c-b273-8099f3976944" />
<img width="950" height="350" alt="Image" src="https://github.com/user-attachments/assets/fa1fa442-ce3d-48ea-8c24-fda9a8f38396" />

## Dataset

This project uses a selected and pre-processed subset of the **Warwick-QU dataset**, originally released as part of the **MICCAI 2015 GlaS (Gland Segmentation) Challenge**. More information and the original dataset can be found at:  
[https://warwick.ac.uk/fac/sci/dcs/research/tia/glascontest/download/](https://warwick.ac.uk/fac/sci/dcs/research/tia/glascontest/download/)
