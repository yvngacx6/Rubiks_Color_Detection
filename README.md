# Rubik's Cube Color Detection (YOLOv8n)

This project fine-tunes a YOLOv8 nano model (`yolov8n.pt`) to detect Rubik's cube sticker colors for edge-oriented deployment (e.g., NUC + ROS2 workflows).

## What This Repo Contains

- `rubiks_yolov8n_finetune.ipynb` - end-to-end notebook for setup, training, evaluation, and custom inference
- `data/data.yaml` - dataset config used by Ultralytics
- `data/README.roboflow.txt` - dataset export metadata from Roboflow

Training outputs (runs, plots, weights) are intentionally ignored via `.gitignore`.

## Classes

The model predicts 6 color classes:

- `b` (blue)
- `g` (green)
- `o` (orange)
- `r` (red)
- `w` (white)
- `y` (yellow)

## Quick Start

1. Install Python dependencies:
   - `ultralytics`
   - `torch` (CUDA build for GPU training)
   - `pyyaml`
2. Open and run `rubiks_yolov8n_finetune.ipynb` cell-by-cell.
3. Ensure dataset paths in `data/data.yaml` use:
   - `train: train/images`
   - `val: valid/images`
   - `test: test/images`

## Inference on Your Own Images

Add images to `data/inference/`, then run the notebook inference cell.

Annotated predictions are saved under:

- `runs/detect/runs/rubiks_inference/`

## Notes

- The project is configured to train on GPU when available.
- Model weight files (`*.pt`) are excluded from git by default to keep the repo lightweight.
