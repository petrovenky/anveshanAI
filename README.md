![Logo](https://github.com/user-attachments/assets/49fced5e-1835-44e4-871a-4c5d0b19e6ca)

# 🇮🇳 IndiaAI - ML Hackathon 2025: Mineral Prospectivity Mapping  
**Team: अन्वेषणAI**

This repository contains the complete solution submitted for the **IndiaAI - ML Hackathon 2025**, focused on generating high-confidence mineral prospectivity maps using supervised machine learning models and ensemble techniques.
## 🧠 Problem Formulation

REE prospectivity mapping was framed as a **binary classification** task.  
Model outputs are interpreted as **probability values** indicating the likelihood of mineralization.

---

## 📁 Repository Structure

### `Code/`
Jupyter Notebooks containing:
- Python code for training base models and meta-model
- Raster processing and data extraction using Rasterio
- Probability map generation and uncertainty quantification

### `Datasets/`
Pre-extracted datasets used for training and validation:
- `1km_buffer/`: Six datasets with 1 km buffer around mineralized zones
- `3km_buffer/`: Six datasets with 3 km buffer
  - Each includes:
    - 1 **soil-informed dataset**
    - 5 **randomly sampled negative datasets**

### `1km_rasters/`
Raster outputs (`.tif`) of base model predictions:
- Probability maps generated for each of the 6 datasets with 1 km buffer

### `3km_rasters/`
Raster outputs (`.tif`) of base model predictions:
- Similar outputs as 1 km buffer, but using 3 km buffer datasets

### `Meta_model_raster/`
Final ensemble prediction raster:
- Output of **gradient boosting stacked model** trained on the 3 km soil-informed dataset

### `21_Raster_Stack/`
Raster stack containing 21 input features:
- Used for training models and predicting mineral prospectivity

### `Performance_results/`
Performance metrics of all models:
- ROC-AUC, Accuracy, Precision, Recall, F1-Score, etc.
- Results reported for both 1 km and 3 km buffer experiments

### `Confidence_Target_raster/`
Thresholded ensemble predictions:
- Final target maps based on ensemble probabilities
- Confidence zones derived using standard deviation from 48 model runs

### `Map_images/`
PNG format maps used in the final report:
- Includes probability maps and target zones

### `TEAM_anveshanAI_REPORT.pdf`
Final hackathon submission report:
- Methodology, data sources, modeling workflow, and identified targets

---

## 🧰 Software & Libraries Used

| Package        | Version |
|----------------|---------|
| Python         | 3.12.9  |
| NumPy          | 1.26.4  |
| Pandas         | 2.2.3   |
| Scikit-learn   | 1.6.1   |
| Matplotlib     | 3.10.0  |
| Seaborn        | 0.13.2  |
| Rasterio       | 1.4.3   |
| XGBoost        | 2.1.1   |
| LightGBM       | 4.6.0   |

---

## 🌐 Coordinate Reference System

All raster files and datasets are georeferenced in:  
**EPSG:32643 — WGS 84 / UTM zone 43N**

---

## 📌 Notes

- Ensemble learning was used to reduce individual model bias and improve predictive confidence.
- Multiple negative sample strategies (soil-informed vs random) were evaluated for robustness.
- Uncertainty quantification was incorporated through ensemble variance.

---

For any questions or collaborations, feel free to reach out to **Team अन्वेषणAI**!
