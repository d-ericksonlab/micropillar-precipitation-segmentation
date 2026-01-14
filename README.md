## How to run (end-to-end)
1. Put paired PNG images into `data/raw_images/`
   - C1 brightfield (pillar masking)
   - C2 TL-POL (precipitation quantification)

2. Open `micropillar_full_pipeline.ipynb` in Google Colab or Jupyter.

3. Run all cells.
   - The model checkpoint is downloaded automatically from Box (first cell).
   - Pillar masks are saved to `outputs/pillar_masks/`
   - Precipitation results are saved to `outputs/`
