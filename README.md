# MSc Thesis: Disease Progression in Multiple Sclerosis  

This repository contains scripts developed for my MSc thesis project, which focuses on creating a multistep machine learning pipeline to enhance the prediction of disease progression in multiple sclerosis (MS). The project is divided into two main parts: **Dimensionality Reduction Exploration** and **Machine Learning Exploration**.  

## **Project Overview**  

### **Part 1: Dimensionality Reduction Exploration**  
In this phase, dimensionality reduction techniques were explored using cleaned and preprocessed data. The included techniques are Principal Component Analysis (PCA), t-distributed Stochastic Neighbor Embedding (t-SNE), Uniform Manifold Approximation and Projection (UMAP), and Temporal Potential of Heat Diffusion for Affinity-based Transition Embedding (TPHATE).  

#### **Steps**:  
1. **Data Preprocessing**:  
   - Use the `Data_Preprocessing_Dimensionality_Reduction.ipynb` notebook to:  
     - Clean and combine datasets.  
     - Perform train-test splits.  
     - Impute missing values with the 3 possible methods.  
     - Oversample using SMOTE.  
     - Split the dataset by session for use in dimensionality reduction scripts.  
   - The dataset includes diffusion magnetic resonance imaging (MRI), diffusion MRI, structural MRI, and clinical and demographic data from the MS cohort (as described in the "participants" methodology of the paper).  

2. **Dimensionality Reduction Exploration**:  
   - **PCA**:  
     - Use the `PCA_Dimensionality_Reduction.ipynb` notebook to:  
       - Tune PCA hyperparameters with a cross-validation scheme for each data split.  
       - Perform a final run using the test set with tuned hyperparameters.  
       - Record evaluation scores for the results section.  
   - **t-SNE, UMAP, and TPHATE**:  
     - Use the respective notebooks (`tSNE_Dimensionality_Reduction.ipynb`, `UMAP_Dimensionality_Reduction.ipynb`, and `TPHATE_Dimensionality_Reduction.ipynb`) to:  
       - Tune hyperparameters for t-SNE, UMAP, and TPHATE.  
       - Evaluate and record results similar to the PCA workflow.
       - 
### **Part 2: Machine Learning Exploration**  
This phase involves implementing a nested cross-validation pipeline to train machine learning models for predicting disease progression.  

#### **Steps**:  
1. **Nested Cross-Validation Pipeline**:  
   - Use the `NestedCV_Pipeline_MLA.ipynb` and `NestedCV_Pipeline_LSTM.ipynb` notebooks to:  
     - Clean and combine datasets.  
     - Split participants across outer and inner folds.  
     - Impute missing values.  
     - Oversample using SMOTE.  
     - Tune machine learning algorithm hyperparameters in the inner loop.  
     - Use the best-performing hyperparameters for the current outer split.  

2. **Machine Learning Algorithms**:  
   - **Traditional ML Algorithms**:  
     - The `NestedCV_Pipeline_MLA.ipynb` notebook includes scripts for:  
       - Logistic Regression (LogR) 
       - Linear Regression (LR)  
       - Support Vector Machine (SVM)
       - Random Forest (RF)
       - Extreme Gradient Boosting (XGB)
   - **Long Short Term Memory (LSTM) Network**:  
     - The `NestedCV_Pipeline_LSTM.ipynb` notebook contains scripts for implementing and evaluating the LSTM network.  

3. **Performance Metrics**:  
   - Best models from the outer loops are saved alongside recorded performance metrics.  
   - This process is repeated for each of the 10 dependent variables across all machine learning algorithms.  

## **Repository Structure**  
```
MSc_Thesis_MS_Disease_Progression/
│
├── Data_Preprocessing_Dimensionality_Reduction.ipynb  # Preprocessing scripts for Dimensionality Reduction
├── PCA_Dimensionality_Reduction.ipynb                # PCA tuning and evaluation
├── tSNE_Dimensionality_Reduction.ipynb               # t-SNE tuning and evaluation
├── UMAP_Dimensionality_Reduction.ipynb               # UMAP tuning and evaluation
├── TPHATE_Dimensionality_Reduction.ipynb             # TPHATE tuning and evaluation
│
├── NestedCV_Pipeline_MLA.ipynb                       # Nested CV pipeline for ML algorithms
├── NestedCV_Pipeline_LSTM.ipynb                      # Nested CV pipeline for LSTM network
│
└── README.md                                         # Project documentation
```

## **Getting Started**  
To use the code in this repository:  
1. Clone the repository:  
   ```bash
   git clone https://github.com/your-username/MSc_Thesis_MS_Disease_Progression.git
   cd MSc_Thesis_MS_Disease_Progression
   ```
   
3. Install required dependencies:  
   - Use a package manager like `pip` to install dependencies.  
   - Example:  
     ```bash
     pip install -r requirements.txt
     ```
     
4. Run the desired notebooks in Jupyter Notebook or JupyterLab.  

## **Data**  
The dataset includes multimodal MRI (diffusion, structural, and functional), clinical, and demographic data from the MS cohort. The data preparation steps are detailed in the preprocessing notebooks.  

## **Acknowledgments**  
I sincerely thank my supervisors, Ismail Koubiyr and Mar Barrantes Cepas, and the Amsterdam UMC Anatomy & Neurosciences Department for their invaluable support and resources.
