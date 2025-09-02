# A Comparative Study Using the ModelNet Dataset for Point Cloud Classification Using Different Machine Learning and Deep Learning Models

This repository presents a comparative study of point cloud classification on **ModelNet40**. The pipeline evaluates **Random Forest**, **MLP Classifier**, **Convolutional Neural Networks (CNN)**, and **PointNet**. CAD models in `.off` format are loaded and sampled into point clouds (using **trimesh**) at **512**, **1024**, and **2048** points per object. The study focuses on 10 representative categories: **airplane, bed, bookshelf, bottle, chair, mantel, monitor, sofa, table,** and **toilet**. All terminology and model names follow the notebook and report.

## Repository Contents
- `3Dpointcloud_classification_code.ipynb` — end‑to‑end notebook (data loading, point sampling, model training, evaluation, visualization).

## Environment
Use Python with the libraries used in the notebook:
- `trimesh`, `numpy`, `scikit-learn` (RandomForestClassifier, MLPClassifier)
- `tensorflow` / `keras` (CNN, PointNet)
- plotting utilities (for confusion matrices and accuracy curves)

> A GPU is recommended for training the CNN/PointNet models but the notebook also runs on CPU for smaller configurations.

## Dataset
ModelNet40 in `.off` format. Place the dataset locally and set the dataset root path **inside the notebook** before running. The notebook samples **512/1024/2048** points per object and prepares train/test splits for the 10 selected classes.

## Procedure (Run Order)
1. **Open** `3Dpointcloud_classification_code.ipynb` in Jupyter.
2. **Set dataset path** to your local ModelNet40 directory (contains the `.off` files).
3. **Run data preparation cells** to load meshes with `trimesh`, sample point clouds at the chosen resolution (512/1024/2048), and assemble per‑class datasets.
4. **Train classical baselines**:
   - **Random Forest Classifier** on the prepared point features.
   - **MLP Classifier** using the architecture specified in the notebook.
5. **Train deep models**:
   - **CNN** (as defined in the notebook).
   - **PointNet** (as defined in the notebook).
6. **Evaluate & visualize**:
   - Compute overall accuracy for each model and each point sampling level.
   - Plot confusion matrices to analyze per‑class performance.
7. **Compare results** across models and sampling resolutions. Refer to the report for detailed discussion of trends and observations.

## Notes
- **Sampling resolution** affects performance; results are reported for **512**, **1024**, and **2048** points per object.
- **Reproducibility**: the notebook sets seeds (e.g., `np.random.seed`, `random.seed`) where applicable.
- This README follows the terminology used in the notebook/report: *Random Forest Classifier, MLP Classifier, CNN, PointNet; ModelNet40; trimesh; `.off` meshes; 512/1024/2048 sampled points.*
