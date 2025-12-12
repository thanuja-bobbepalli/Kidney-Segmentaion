# Kidney Segmentation using U-Net (MONAI)

This repository contains a complete training and inference pipeline for **kidney segmentation** from CT images using the **U-Net** architecture built with the **MONAI medical imaging framework**.  
The project includes two notebooks:
- **U-Net Kidney Segmentation.ipynb** — full training pipeline  
- **U-Net Kidney Inference.ipynb** — model loading and prediction on unseen CT images

  
##  Live HuggingFace Demo
Try the model in your browser:  
**https://huggingface.co/spaces/Thanuja-Bobbepalli/Kidney-segmentation-monai**


## Project Description

Kidney segmentation plays a crucial role in medical diagnostics, surgical planning, and automated kidney structure analysis.  
This project uses:

- **Medical-optimized preprocessing (MONAI transforms)**
- **U-Net architecture** for pixel-wise segmentation
- **PyTorch**
- **Training, validation, and inference workflows**

The goal is to provide a clear, modular pipeline that can easily be extended or used as a starting point for research.


##  Dataset Information

This project uses the **KITS19 PNG Dataset**, available at:

**Dataset Link:**  
https://www.kaggle.com/datasets/orvile/kits19-png-zipped

### **Dataset Description**
- The dataset contains pre-extracted **2D PNG slices** from the original KITS19 CT volumes.  
- Each slice has a corresponding **segmentation mask** indicating:
  - Kidney region  
  - Tumor region (if present)

### **Dataset Statistics (Used in This Project)**

| Metric | Count |
|--------|-------|
| **Total Slices** |  45,424 |
| **Positive Slices (Non-Empty Masks)** |  16,336 |
| **Negative Slices (Empty Masks)** | 29,088 |

**Positive slices** = slices where mask contains kidney pixels  
**Negative slices** = slices where mask is completely empty  


##  Loss Function and Metrics Used

- **Loss Function:** Dice+bce
- **Evaluation Metric:** DiceMetric , HD95( from MONAI)



