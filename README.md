# oir_flatmount_segmentation

Hartnett Lab model bundle for segmentation of oxygen-induced retinopathy (OIR) retinal flatmount images.

This model segments three regions:

- Total Retina (TR)
- Intravitreal Neovascularization (IVNV)
- Avascular Area (AVA)

## Repository Contents

- `configs/metadata.json`: model metadata, package requirements, and input/output definitions.
- `configs/inference.json`: MONAI inference config with required bundle keys.
- `configs/train.json`: MONAI training config template and key naming conventions.
- `docs/README.md`: detailed model card (method, intended use, limitations).
- `docs/data_license.txt`: dataset and data-use notes.
- `large_files.yml`: external download links for large checkpoint files.
- `weights/fold_*/thresholds.json`: threshold files used for class binarization.
- `scripts/plot_learning_curves.py`: utility for fold-level learning curve plotting.
- `models/`: placeholder directory for model artifacts.

## Model Weights

Checkpoint files (`.pth`) are not stored directly in this repository because of file size limits.  
They are hosted as release assets and referenced in `large_files.yml`.

Weights for this release are available at:

- [v1.0.0 release assets](https://github.com/hartnettlabteam/oir_flatmount_segmentation/releases/tag/v1.0.0)

## Intended Use

- Research use for preclinical OIR flatmount analysis in mouse and rat datasets.
- Automated support for segmentation and derived TR/IVNV/AVA area metrics.

Not intended for direct clinical diagnosis or treatment decisions.

## MONAI Model Zoo

This repository is structured as a MONAI bundle and is prepared for MONAI Model Zoo submission.  
For full technical details, see `docs/README.md`.

## Citation and Contact

If you use this model, please cite the associated Hartnett Lab manuscript and repository release.

Contact:
- Neal Shah: neals1@stanford.edu
- Aniket Ramshekar: aniket.ramshekar@stanford.edu
- M. Elizabeth Hartnett: me.hartnett@stanford.edu
