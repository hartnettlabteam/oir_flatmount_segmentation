# OIR Flatmount Segmentation (Hartnett Lab)

### **Authors**
Neal S. Shah*, Aniket Ramshekar*, Bright Asare-Bediako, Morgan P. Tankersley, Heng-Chiao Huang, Shreya Beri, Eric Kunz, Aaron Y. Lee, M. Elizabeth Hartnett, Byers Eye Institute Department of Ophthalmology, Stanford University School of Medicine, Stanford, CA, USA

### **Tags**
Segmentation, Retinal Flatmount, Oxygen-Induced Retinopathy, OIR, Mouse, Rat, Intravitreal Neovascularization, Avascular Area

## **Model Description**
This model performs automated segmentation of oxygen-induced retinopathy (OIR) retinal flatmount images into three regions: total retina (TR), intravitreal neovascularization (IVNV), and avascular area (AVA).  
The architecture is a multi-task Attention U-Net with a ConvNeXt-Tiny encoder and deep supervision (~8.7M trainable parameters).  
For inference, the final release uses an ensemble of 5 cross-validation models, with test-time augmentation and per-class thresholding, to improve robustness across mouse and rat OIR images.

## **Data**
Model development used three datasets:

1. **Rat IVNV pretraining dataset:** 72 rat OIR flatmount images with IVNV-only annotations (used in intermediate Stage 2 training).
2. **Final development dataset:** 345 annotated images total (267 mouse, 78 rat), including:
   - 127 expert human-annotated images (49 mouse, 78 rat)
   - 218 curated open-source mouse images with reviewed masks
3. **Independent test dataset:** 37 images (18 mouse OIR, 19 rat OIR), held out from training/validation/model selection.

For final model development, a modified 5-fold cross-validation strategy was used, with expert-annotated images serving as fold-level validation references and curated open-source mouse images used in training only.

#### **Preprocessing**
Input images are converted to grayscale, resized to 512 x 512, and intensity-normalized before model inference/training.  
Training-time augmentation includes flips, rotations, contrast/brightness changes, and noise injection.

## **Performance**

Dice agreement between model masks and human consensus masks was high for total retina (TR) and AVA, and moderate for IVNV in both species:
- Rat: TR Dice=0.983, AVA Dice=0.924, IVNV Dice=0.612
- Mouse: TR Dice=0.975, AVA Dice=0.912, IVNV Dice=0.601

At the metric level, the deep learning model showed strong correlation with the mean of three graders for rat percent AVA (r=0.979) and rat percent IVNV (r=0.943). In mouse OIR, correlation was strong for percent AVA (r=0.957) but weak for percent IVNV (r=0.265), likely due to high inter-grader variability for mouse IVNV scoring.

(For full analyses, confidence intervals, and subgroup details, refer to manuscript/report tables.)

## **Additional Usage Steps** 
Model checkpoints are hosted externally and linked through `large_files.yml` (not committed directly in the repo due to file size limits).  
