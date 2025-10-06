# CS5582-HW-3 — LoG Keypoints & SIFT Comparison

This repo contains HW2_2 work: σ²-normalized Laplacian-of-Gaussian (LoG) scale-space, sub-scale extrema via polynomial fitting, LoG keypoint extraction with NMS, and a comparison to SIFT.

## Quick Start

```bash
# activate your course env
source ~/venvs/core-rag/bin/activate

# (optional) install deps locally for this repo
pip install -r requirements.txt

# open the notebook
cd notebooks
jupyter lab  # or jupyter notebook
'''

Data

NWPU-RESISC45 at /home/manny-buff/projects/cv-hw1/data/NWPU-RESISC45

This notebook uses the first 15 classes for probes; adjust in Cell 1.

Notebook

CS5582_HW2_2.ipynb

Cell 1: Environment & dataset probe

Cell 2–3: LoG pyramid + robust σ* refinement (cubic/quad fit) and batch probe

Cell 4: LoG keypoint detector (spatial & cross-scale NMS; concavity)

Cell 5: LoG vs SIFT batch comparison + histograms

Cell 6: Checklist + repo files generation (this cell)

Artifacts

notebooks/artifacts/log_kp_preview.png

notebooks/artifacts/log_vs_sift/… (per-image overlays)

notebooks/artifacts/log_vs_sift_summary.csv

Notes

OpenCV 4.12.0 exposes cv2.SIFT_create().

Tune LoG with percentile, k, and n_scales for different scenes.
