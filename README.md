# CFD–ANN Surrogate Modelling for Fixing-Angle Optimisation of a Darrieus VAWT

This repository contains the Artificial Neural Network (ANN) surrogate model code accompanying the paper:

> **CFD and ANN surrogate modelling for fixing angle optimisation of a Darrieus vertical axis wind turbine**
> A. Tamaddon, Ma Mohin, Y. I. Mogul, J. D. Quadros, M. Ndiaye
> *Engineering Applications of Computational Fluid Mechanics*, 2026, 20(1), 2654918.
> DOI: [10.1080/19942060.2026.2654918](https://doi.org/10.1080/19942060.2026.2654918)

## 📄 Read the paper

- **Download the PDF:** [paper.pdf](paper.pdf) (open access, CC BY 4.0)
- **Publisher / DOI:** https://doi.org/10.1080/19942060.2026.2654918

## Overview

The notebook trains a feed-forward neural network that predicts the power coefficient (C_P) of a
three-bladed Darrieus VAWT from two inputs — Tip-Speed Ratio (TSR) and blade Fixing Angle (FA).
Trained on URANS-based CFD data, the surrogate maps the TSR–FA design space at negligible
computational cost and locates the optimum configuration (FA = +1.5°, TSR ≈ 2.0).

## Repository contents

| File | Description |
|------|-------------|
| `paper.pdf` | The published open-access article (CC BY 4.0) |
| `ANN_surrogate_model.ipynb` | Jupyter notebook: data loading, preprocessing, ANN training, evaluation, and prediction plots |
| `VAWT.csv` | CFD dataset used to train the model (TSR, FA, C_P) — *see note below* |
| `requirements.txt` | Python package dependencies |

## Method summary

- **Inputs:** TSR (0.5–3.0), FA (−1.5° to +1.5°)
- **Output:** Power coefficient C_P
- **Dataset:** 42 CFD operating points, 80/20 train/test split, fixed random seed (42)
- **Preprocessing:** feature normalisation with `StandardScaler`
- **Architecture:** 2 fully connected hidden layers (ReLU) + 1 linear output neuron
- **Training:** Adam optimiser, MSE loss, early stopping (patience 200), up to 4000 epochs, batch size 8
- **Metrics:** R², MAE, MSE

## How to run

1. Install the dependencies:
```bash
   pip install -r requirements.txt
```
2. Make sure `VAWT.csv` is in the same folder as the notebook.
3. Open and run the notebook:
```bash
   jupyter notebook ANN_surrogate_model.ipynb
```

## Data availability

Per the paper, the full CFD simulation results and ANN training data are available from the
corresponding author upon request. If you do not include `VAWT.csv` in this repository, please
remove that row from the table above and note here how the data can be obtained.

## Citation

If you use this code, please cite the paper:

```bibtex
@article{tamaddon2026cfdann,
  title   = {CFD and ANN surrogate modelling for fixing angle optimisation of a Darrieus vertical axis wind turbine},
  author  = {Tamaddon, Amir and Mohin, Ma and Mogul, Yakub Iqbal and Quadros, Jaimon Dennis and Ndiaye, Mamadou},
  journal = {Engineering Applications of Computational Fluid Mechanics},
  volume  = {20},
  number  = {1},
  pages   = {2654918},
  year    = {2026},
  doi     = {10.1080/19942060.2026.2654918}
}
```
## ▶️ View / run the notebook

[![View in nbviewer](https://img.shields.io/badge/view-nbviewer-orange)](https://nbviewer.org/github/TMDN-NEW/CFD-and-ANN-for-fixing-angle-optimisation-of-a-Darrieus-vertical-axis-wind-turbi/blob/main/ANN_surrogate_model.ipynb)
[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/TMDN-NEW/CFD-and-ANN-for-fixing-angle-optimisation-of-a-Darrieus-vertical-axis-wind-turbi/blob/main/ANN_surrogate_model.ipynb)

## License

Released under the MIT License (or another license of your choice).
## 💾 Cite the code / data

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.20479467.svg)](https://doi.org/10.5281/zenodo.20479467)

This repository is archived on Zenodo. If you use the code or dataset, please cite both the paper (above) and this DOI: **10.5281/zenodo.20479467**
