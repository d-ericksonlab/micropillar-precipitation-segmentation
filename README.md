# Micropillar Dual-Mode Image Analysis Pipeline

This repository contains a reproducible Jupyter/Colab workflow for dual-mode microscopy analysis of micropillar devices. The pipeline:
- segments micropillars from **C1** images using a trained U-Net
- quantifies birefringent CaCO₃ signal in **C2** images restricted to the **non-pillar** region
- generates mask outputs and storyboard figures for quality control

## Repository structure

- `micropillar_full_pipeline.ipynb` — main notebook (end-to-end pipeline)
- `test_images/` — example paired input images (C1/C2)
- `model/` — U-Net model weights (user-provided; not stored in this repo)
- `results/` — outputs written by the notebook (masks, indices, storyboards)

## Input naming convention

Inputs are expected to follow the dot-delimited format:

`<channel_id>.<section>.<diameter>.<trial>.<modality>.png`

Example:
- `t2.1.8.c.c1.png`
- `t2.1.8.c.c2.png`

Parsed attributes:
- **channel_id**: channel identifier (e.g., `t1`, `t2`, `s1`, `s2`)
- **section**: `1` = 0.35 porosity, `2` = 0.45 porosity
- **diameter**: integer `5–10` representing **0.5–1.0 mm** (e.g., `5` = 0.5 mm)
- **trial**: replicate identifier (e.g., `a`, `b`, `c`)
- **modality**: `c1` (pillar structure channel) or `c2` (CaCO₃ channel)

## Quickstart (Google Colab recommended)

1. Open `micropillar_full_pipeline.ipynb` in Google Colab.

2. Run the installation and cloning cells.

3. Download the trained model weights from Box and upload them when prompted:
   - Box link: https://cornell.box.com/s/4dyu78bhtpabm98jgz40gdp5wmoe71xn
   - The notebook will place the uploaded file at: `model/pillar_unet.pt`

4. Place paired images in `test_images/` using the naming convention above.

5. Run the remaining notebook cells to:
   - generate pillar masks for all C1 images
   - quantify C2 signal in the non-pillar region
   - produce per-image storyboard outputs

## Outputs

All outputs are written to `results/`, including:
- `results/pillar_masks/` — saved pillar masks corresponding to each C1 image
- `results/mask_index.csv` — index mapping C1 → C2 → mask, plus parsed metadata
- storyboard visualizations for verification (C1, mask, C2 raw, processed C2, composite)

## Notes

- Model weights are not committed to this repository. They must be downloaded from Box and uploaded into the runtime.
- The notebook is designed to run on CPU-only environments, but will automatically use GPU if available.
