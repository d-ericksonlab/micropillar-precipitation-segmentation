# Micropillar Dual-Mode Image Analysis Pipeline

This repository contains a single reproducible Jupyter notebook used to:
- segment micropillars from C1 images using a trained U-Net
- quantify birefringent CaCO₃ signal in C2 images in the non-pillar region

## Quickstart
1. Install dependencies:
   pip install -r requirements.txt

2. Place paired images in:
   data/images/

3. Run the notebook:
   micropillar_pipeline.ipynb

Outputs are written to:
results/
