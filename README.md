# oir_flatmount_segmentation

Standalone MONAI bundle-style packaging for the Hartnett Lab OIR flatmount segmentation model (TR, IVNV, AVA).

This folder is designed to be copied as-is into a git repository and prepared for MONAI Model Zoo submission.

## Bundle Contents

- `configs/metadata.json`: model metadata, authorship, dependencies, and I/O schema.
- `configs/inference.json`: inference pipeline contract and runtime variables.
- `configs/train.json`: training contract and required keys for MONAI bundle conventions.
- `docs/README.md`: model card and method summary.
- `docs/data_license.txt`: dataset licensing and usage notes.
- `large_files.yml`: external links for large model files (>25 MB).
- `models/`: placeholder directory for model artifacts (kept empty in source repo).
- `scripts/plot_learning_curves.py`: utility to aggregate fold learning curves.

## Model Name

`oir_flatmount_segmentation`

Display name in MONAI metadata:

`OIR Flatmount Segmentation (Hartnett Lab)`

## Current Training Codebase

The training and inference implementation used to generate model weights is in:

- `../train_with_split.py`
- `../retrain_kfold_v2.py`
- `../infer.py`
- `../model_transformer.py`
- `../dataset.py`

## Pre-Submission Checklist

1. Keep model checkpoints external (GitHub Releases) and reference them in `large_files.yml`.
2. Update `large_files.yml` with permanent public download URLs and SHA256 hashes.
3. Run local MONAI bundle verification:
   - `python -m monai.bundle verify_metadata --meta_file configs/metadata.json`
   - `python -m monai.bundle verify_net_in_out --net_id network_def --meta_file configs/metadata.json --config_file configs/inference.json`
4. Confirm `LICENSE` and `docs/data_license.txt` reflect final legal terms.

