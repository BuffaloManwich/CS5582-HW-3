# CS5582 — HW2_2 Report (LoG Scale-Space & SIFT Comparison)

**Author:** manny-buff  
**Date:** 2025-10-06 11:31  
**Repo:** `CS5582-HW-3` (cv-hw3)  
**Environment:** Python 3.11.9 • NumPy 2.2.1 • OpenCV 4.12.0 • SciPy 1.16.1 • Matplotlib 3.10.6

## Data & Setup
- Dataset: NWPU-RESISC45 (15 classes used in probes), root: `/home/manny-buff/projects/cv-hw1/data/NWPU-RESISC45`
- Image preprocessing: gray, resize 256×256, float32 [0,1]
- LoG pyramid: σ²-normalized; typical params `σ₀=0.8, k=1.20, n≈22`
- Refinement: local polynomial fit with concavity check (`p″(σ*)<0`), spatial & cross-scale NMS, endpoint σ* dropped
- SIFT: OpenCV `cv2.SIFT_create()` defaults

## Results Summary (batch)
- Images evaluated (LoG vs SIFT): **20**
- Total keypoints: **LoG=4111**, **SIFT=10142**
- Mean per-image scale/size: **σ*≈2.46**, **size≈3.49**

**Qualitative:**  
LoG emphasizes blob-like extrema (aircraft bodies, runway markers); SIFT is denser on corners/edge junctions. LoG counts drop and σ* increases in low-texture scenes (e.g., beaches), consistent with the scale-selection behavior.

## Representative Visuals
- LoG preview (`notebooks/artifacts/log_kp_preview.png`):  
![LoG preview](notebooks/artifacts/log_kp_preview.png)

- LoG vs SIFT overlays (sample):  
![LoG overlay](notebooks/artifacts/log_vs_sift/basketball_court/basketball_court_004_log.png)
![SIFT overlay](notebooks/artifacts/log_vs_sift/basketball_court/basketball_court_004_sift.png)

## Notes on Parameter Sensitivity
- Densifying scales (e.g., `k≈1.15`) and/or expanding σ-range reduces endpoint attraction.
- Lowering percentile (e.g., 99.0) increases LoG recall in texture-poor regions.
- Combining LoG + SIFT may improve downstream matching coverage.

## Repro Steps
Open `notebooks/CS5582_HW2_2.ipynb` and run cells in order.  
Artifacts are written under `notebooks/artifacts/`. Consolidated CSV: `notebooks/artifacts/log_vs_sift_summary.csv`.
