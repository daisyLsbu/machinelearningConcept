# Machine Learning Concept

A collection of Jupyter/Colab notebooks covering core machine learning concepts and algorithms — from basic NumPy/Pandas/Scikit-learn usage through classification, model evaluation, dimensionality reduction, feature selection, SVMs, and PyTorch-based neural networks (CNNs).

## Summary of the Repo

This repo is a set of self-contained tutorial notebooks, most of them built around `scikit-learn` and a few around `PyTorch`. They're organized loosely by topic rather than as a single pipeline — each notebook can generally be run on its own once its required data file is available.

| File | Topic | Key libraries |
|---|---|---|
| `MachineLearningSelf.ipynb` | Intro basics: NumPy, Pandas, Scikit-learn, loading and exploring a dataset (breast cancer dataset) | numpy, pandas, sklearn |
| `MLSelf-Classification.ipynb` | Intro to classification: Logistic Regression, Naive Bayes, Decision Trees, SVC, plotting decision boundaries | sklearn, seaborn, scipy |
| `Tutorial_04.ipynb` | Loading data from CSV; training/evaluating AdaBoost and KNN classifiers | sklearn (AdaBoost, KNN), csv |
| `Tutorial_05.ipynb` | Cross-validation for generalization error estimation (AdaBoost & KNN), stratified K-Folds, choosing K | sklearn (KFold, StratifiedKFold) |
| `Tutorial_09_2223.ipynb` | Custom PyTorch `Dataset`/`DataLoader` and CNN basics on a characters image dataset (`charsdb.pth`) | torch, torchvision, PIL |
| `Tutorial_10_2223.ipynb` | SVM classification vs. a PyTorch CNN on the Viola-Jones face dataset (`viola_jones.npz`); ROC curves, confusion matrices | sklearn (SVC), torch |
| `Tutorial 12_2223.ipynb` | Dimensionality reduction & feature selection on the Olivetti Faces dataset: PCA, SelectKBest (chi2), RFE, Logistic Regression | sklearn (decomposition, feature_selection) |
| `SVM.ipynb` | Support Vector Machine classification on the Viola-Jones dataset; ROC/AUC, confusion matrix | sklearn.svm.SVC |
| `ColabNotebooks/ML-Tutorials1-6.ipynb` | Colab-based tutorials 1–6: Google Drive mounting, KNN, AdaBoost, Logistic Regression, K-Fold/Stratified K-Fold cross-validation, precision/recall/F1/ROC-AUC metrics | sklearn, google.colab |
| `ColabNotebooks/ML-Tutorials7.ipynb` | Colab tutorial 7: feature selection (SelectKBest, chi2, mutual information, sequential feature selection), Logistic Regression | sklearn.feature_selection |
| `ColabNotebooks/ML-Tutorials8.ipynb` | Colab tutorial 8: PyTorch `Dataset`/`DataLoader`, image loading with PIL, CNN-style modeling | torch, torchvision, PIL |
| `ColabNotebooks/ADNI_Tadpole_data_tutorial.xlsx` | Supporting dataset (ADNI/TADPOLE) used by one of the Colab tutorials | — |
| `ColabNotebooks/Tutorial_3_data.csv` | Supporting CSV dataset used by the Colab tutorials | — |
| `data/charscnn_jitter.pth` | Pre-trained/saved PyTorch model weights (character CNN) used by `Tutorial_09_2223.ipynb` | — |
| `requirements.txt` | Full pinned dependency list (pip freeze) for the local venv these notebooks were developed with | — |

## How to Start

### Prerequisites
- Python 3.x
- An IDE/editor — VS Code with the **Jupyter** extension (Microsoft) is recommended, but any IDE that supports `.ipynb` files works
- Some notebooks (the `ColabNotebooks/` ones) assume a **Google Colab** environment (they mount Google Drive) rather than a local run

### Get the code
Clone the whole project:
```bash
git clone https://github.com/daisyLsbu/machinelearningConcept.git
cd machinelearningConcept
```
Or download just the individual notebook you want to use from the file list above.

### Set up a virtual environment (optional but recommended)
```bash
python -m venv venv
venv\Scripts\activate        # Windows
# source venv/bin/activate   # macOS/Linux
pip install ipykernel jupyter
python -m pip install --upgrade pip
```

### Install dependencies
`requirements.txt` contains the full set of packages used across these notebooks:
```bash
pip install -r requirements.txt
```

### Data
The `data/` folders contain the data files (`.csv`, `.xlsx`, `.pth`, `.npz`) referenced by the notebooks. Some notebooks (e.g. `Tutorial_10_2223.ipynb`, `SVM.ipynb`) load a `viola_jones.npz` file and `Tutorial_09_2223.ipynb` loads `charsdb.pth` — make sure these are present in the working directory the notebook expects before running.

### Running a notebook
Open the `.ipynb` file in VS Code or Jupyter and either:
- Run cells one at a time (`Shift+Enter`), or
- Use **Run All** to execute the entire notebook

For the Colab-specific notebooks (`ColabNotebooks/ML-Tutorials1-6.ipynb`, `7`, `8`), open them in [Google Colab](https://colab.research.google.com) instead of running locally, since they mount Google Drive and expect a Colab runtime.

## Note: update code to use cuda instead of cpu if you have the GPU available

## Notebook Details

- **MachineLearningSelf.ipynb** — Foundational walkthrough of NumPy arrays, Pandas DataFrames, and loading a dataset into Scikit-learn.
- **MLSelf-Classification.ipynb** — Compares classification algorithms (Logistic Regression, Naive Bayes, Decision Tree, SVC) with visualization via Seaborn/Matplotlib.
- **Tutorial_04.ipynb** — AdaBoost and KNN classifiers trained on CSV data, evaluated with accuracy/precision/recall/F1.
- **Tutorial_05.ipynb** — Extends Tutorial 4 with K-Fold and Stratified K-Fold cross-validation to estimate generalization error and its variance, including tuning K for KNN.
- **Tutorial_09_2223.ipynb** — Builds a custom PyTorch `Dataset` and `DataLoader` for an image classification task using a character image dataset, visualizes training samples.
- **Tutorial_10_2223.ipynb** — Compares an SVM classifier against a PyTorch CNN on face-detection data (Viola-Jones), with ROC curves and confusion matrices for both approaches.
- **Tutorial 12_2223.ipynb** — Applies PCA, `SelectKBest` (chi²), and Recursive Feature Elimination (RFE) for dimensionality reduction/feature selection on the Olivetti Faces dataset, then classifies with Logistic Regression.
- **SVM.ipynb** — Focused SVM classification example on the Viola-Jones dataset with ROC/AUC and confusion matrix evaluation.
- **ColabNotebooks/ML-Tutorials1-6.ipynb** — Six combined tutorials covering Colab setup (Drive mounting), KNN, AdaBoost, Logistic Regression, and cross-validation metrics.
- **ColabNotebooks/ML-Tutorials7.ipynb** — Feature selection techniques: `SelectKBest`, chi², mutual information, and sequential feature selection.
- **ColabNotebooks/ML-Tutorials8.ipynb** — PyTorch-based image dataset loading and CNN modeling in a Colab environment.
- | `Tutorial_03.ipynb` | Reading a CSV file "manually" using Python's built-in `csv` module (rather than Pandas), parsing headers/rows into plain lists, and basic plotting | `csv`, `matplotlib.pyplot` |
| `Tutorial_06.ipynb` | Loading the ADNI/TADPOLE Excel dataset directly with `pandas.read_excel`, then training a Logistic Regression classifier to predict beta-amyloid (`Amyloid status`) from patient features (`PTID` and `SUVR` dropped as identifiers/leakage columns) | `pandas`, `sklearn.linear_model.LogisticRegression`, `sklearn.model_selection` (KFold, train_test_split), `sklearn.metrics` (precision/recall/F1/accuracy, confusion matrix, ROC/AUC) |
| `PropertyInvestmentAnalysis_Final.ipynb` | A full end-to-end housing price analysis/prediction project (Ames-style housing data): data cleaning and missing-value imputation (numerical and categorical), exploratory data analysis, correlation heatmaps, feature selection (`SelectKBest`, mutual information), dimensionality reduction and clustering (PCA, t-SNE, KMeans, Agglomerative Clustering), and regression modeling (Linear Regression, SGDRegressor, Random Forest, Decision Tree) with interactive Plotly visualizations alongside Matplotlib/Seaborn | `pandas`, `numpy`, `matplotlib`, `seaborn`, `plotly`, `scipy.cluster.hierarchy`, `sklearn` (preprocessing, imputation, feature_selection, decomposition, cluster, linear_model, ensemble, tree, manifold, metrics, model_selection) |
| `ML-Tutorials7.ipynb` | Root-level copy of the Colab feature-selection tutorial (`SelectKBest` with chi², mutual information, and `f_classif`; sequential feature selection; Logistic Regression) — same content as `ColabNotebooks/ML-Tutorials7.ipynb`, kept here for local (non-Colab) use | `sklearn.feature_selection`, `sklearn.linear_model.LogisticRegression`, `sklearn.metrics`, `sklearn.preprocessing.MinMaxScaler` |

## Repo Structure
```
machinelearningConcept/
├── README.md
├── requirements.txt
├── MachineLearningSelf.ipynb
├── MLSelf-Classification.ipynb
├── SVM.ipynb
├── Tutorial_04.ipynb
├── Tutorial_05.ipynb
├── Tutorial_09_2223.ipynb
├── Tutorial_10_2223.ipynb
├── Tutorial 12_2223.ipynb
├── Tutorial 11.ipynb         
├── data/
│   └── charscnn_jitter.pth
└── ColabNotebooks/
    ├── ML-Tutorials1-6.ipynb
    ├── ML-Tutorials7.ipynb
    ├── ML-Tutorials8.ipynb
    ├── ADNI_Tadpole_data_tutorial.xlsx
    └── Tutorial_3_data.csv
```
