# Interpretable Anomaly Detection on AIS Spatial Data using Generative Deep Learning

MSc Research Project, Imperial College London, 2023

## Abstract

This project applies convolutional Variational Autoencoders (VAEs) to detect anomalous vessel behaviour in maritime Automatic Identification System (AIS) data. AIS transmissions are represented as spatial point patterns on 2D grids, and the VAE learns the distribution of normal traffic patterns. Anomalies are detected via reconstruction error: observations that the model reconstructs poorly are flagged as unusual.

The approach is interpretable because the grid-based representation is human-readable, unlike raw latent embeddings. Experiments on US coastal AIS data demonstrate effective discrimination between normal and anomalous vessel behaviour.

**Supervisor:** Dr James Martin

## Repository Structure

```
thesis/          LaTeX source and compiled PDF
notebooks/       Jupyter notebooks (data processing, model training, evaluation)
figures/         Charts and diagrams used in the thesis
```

## Notebooks

| Notebook | Description |
|---|---|
| `milestone-2-pipeline.ipynb` | Complete pipeline: data filtering, grid representation, VAE training, anomaly detection |
| `vae-v10-model.ipynb` | Final VAE model (V10): training on cargo/tanker vessel grids |
| `vae-v10-analysis.ipynb` | V10 model analysis and evaluation |
| `vae-v11-analysis.ipynb` | V11 model: scene-level analysis variant |

## Data

AIS vessel traffic data (~16GB) is not included due to size. Download from [MarineCadastre.gov AIS Data](https://marinecadastre.gov/ais/). The milestone notebook includes a small sample CSV for demonstration.

## Key Dependencies

- TensorFlow/Keras (model was developed with TF 1.x-era Keras)
- NumPy, Pandas, Scikit-learn
- GeoPandas, MovingPandas, Contextily (geospatial analysis)
- PointPats (spatial statistics)
- Matplotlib, Seaborn

## Errata

The published version includes a correction to the Anomaly Metric section (Section 4.3). The original submission described the anomaly score using MSE with a sparsity-adjusted formula that masked out zero cells. The actual implementation computes MAE across all cells, normalised by the count of non-zero cells. The LaTeX source in this repository has been updated to match the code.

## Acknowledgements

Supervised by Dr James Martin, Department of Mathematics, Imperial College London. The LaTeX thesis template (`mldsmsc.cls`) was provided by the department (Dean Bodenham, 2021). AIS data sourced from [MarineCadastre.gov](https://marinecadastre.gov/). All research code and analysis are original work.
