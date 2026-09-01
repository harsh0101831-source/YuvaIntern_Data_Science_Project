# YuvaIntern Data Science Internship Project

## 📌 Overview

This repository contains the complete set of tasks completed as part of the **YuvaIntern Data Science Internship**.

The project follows an end-to-end Data Science workflow using a real-world **Air Quality dataset**. The same cleaned dataset is progressively used across the tasks to demonstrate how raw data can be transformed into meaningful insights, machine learning models, clustering analysis, deep learning models, and finally an integrated capstone solution.

The project covers:

- Data Acquisition
- Data Cleaning and Preprocessing
- Exploratory Data Analysis
- Data Visualization
- Unsupervised Learning
- Supervised Machine Learning
- Deep Learning
- Model Evaluation
- Feature Engineering
- Integrated Capstone Analysis

---

# 📂 Project Structure

```text
YuvaIntern_Data_Science_Project/
│
├── task1_air_quality/
│   ├── notebooks/
│   │   └── task1_data_cleaning.ipynb
│   └── outputs/
│       └── air_quality_cleaned.csv
│
├── task2_eda/
│   ├── notebooks/
│   │   └── task2_eda_visualization.ipynb
│   └── outputs/
│       └── figures/
│
├── task3_clustering/
│   ├── notebooks/
│   │   └── task3_clustering.ipynb
│   └── outputs/
│       └── figures/
│
├── task4_supervised_learning/
│   ├── notebooks/
│   │   └── task4_supervised_learning.ipynb
│   └── outputs/
│       └── figures/
│
├── task5_deep_learning/
│   ├── notebooks/
│   │   └── task5_deep_learning.ipynb
│   └── outputs/
│       └── figures/
│
├── task6_capstone/
│   ├── notebooks/
│   │   └── task6_capstone.ipynb
│   ├── outputs/
│   │   └── figures/

📊 Dataset

The project uses the Air Quality dataset, containing hourly measurements of air pollutants and environmental variables.

Important variables include:

CO(GT) – Carbon Monoxide concentration
NMHC(GT) – Non-Methane Hydrocarbons
C6H6(GT) – Benzene concentration
NOx(GT) – Nitrogen Oxides
NO2(GT) – Nitrogen Dioxide
PT08.S1(CO) – CO sensor response
PT08.S2(NMHC) – NMHC sensor response
PT08.S3(NOx) – NOx sensor response
PT08.S4(NO2) – NO2 sensor response
PT08.S5(O3) – Ozone sensor response
T – Temperature
RH – Relative Humidity
AH – Absolute Humidity

The original dataset contains 9,471 rows and 17 columns.

The source CSV uses:

; as the column separator
, as the decimal separator
-200 as a placeholder for unavailable measurements
🧹 Task 1 – Data Acquisition, Cleaning & Preprocessing
Objective

The objective of Task 1 was to inspect the raw Air Quality dataset, identify data-quality issues, clean the data, handle missing values, preprocess date-time information, and produce a reliable dataset for subsequent analysis and machine learning.

Key Steps
1. Data Loading

The dataset was loaded using Pandas with the appropriate separator and decimal notation.

df = pd.read_csv(
    file_path,
    sep=";",
    decimal=","
)
2. Structural Inspection

The raw dataset was examined using:

shape
info()
describe()
column inspection
data-type inspection
empty-row detection
empty-column detection
duplicate analysis
3. Empty Rows and Columns

The raw dataset contained:

9,471 rows
17 columns
2 completely empty columns
114 completely empty rows

The empty structural elements were removed.

4. Missing-Value Handling

The dataset uses -200 as a missing-value marker.

The frequency of this marker was analyzed before replacing it with standard missing values.

The NMHC(GT) feature contained approximately 89–90% missing values, making it unsuitable for reliable modeling, so it was removed.

The remaining numerical missing values were handled using median imputation.

5. Date-Time Processing

The separate date and time information was combined into a unified Datetime column.

This allowed later tasks to perform:

hourly analysis
daily analysis
monthly analysis
time-based feature engineering
6. Final Dataset

After cleaning and preprocessing, the resulting dataset contained approximately:

9,357 rows × 13 columns

The cleaned dataset was exported for reuse in the following tasks.

Output
task1_air_quality/outputs/air_quality_cleaned.csv
📈 Task 2 – Exploratory Data Analysis & Visualization
Objective

Task 2 focused on understanding the cleaned dataset through statistical analysis and visualization.

The objective was to identify:

distributions
relationships between variables
pollutant patterns
temporal trends
unusual observations
correlations between sensor measurements
Analysis Performed
1. Descriptive Statistics

Statistical summaries were generated for numerical variables using:

df.describe()

This helped understand:

mean
standard deviation
minimum
maximum
quartiles
2. Distribution Analysis

Distribution plots were created for important pollutant and environmental variables.

These visualizations helped identify:

skewed distributions
concentration ranges
extreme observations
variability
3. Boxplots

Boxplots were used to inspect the spread of pollutant measurements and identify potential outliers.

4. Correlation Analysis

A Pearson correlation matrix was calculated and visualized using a heatmap.

Important observed relationships included:

C6H6(GT) and PT08.S2(NMHC) showed a very strong positive correlation of approximately 0.98
PT08.S1(CO) and PT08.S5(O3) showed a strong positive relationship of approximately 0.90
PT08.S3(NOx) showed strong negative relationships with several pollutant sensor variables
Temperature and relative humidity showed a negative relationship
Temperature and absolute humidity showed a positive relationship

These relationships represent statistical associations and should not automatically be interpreted as causal relationships.

5. Hourly Pollution Analysis

Time-based features were extracted from Datetime.

Hourly averages of:

CO(GT)
NOx(GT)
NO2(GT)

were calculated.

The analysis showed clear daily variation, including pronounced morning and evening increases in several pollutants.

Key Insight

EDA demonstrated that pollution measurements are influenced by both relationships among sensor variables and temporal patterns.

The results provided a foundation for feature engineering and predictive modeling.

🔵 Task 3 – Unsupervised Learning & Clustering
Objective

Task 3 applied unsupervised learning to identify groups of observations with similar air-quality characteristics.

The main technique used was:

K-Means Clustering

Principal Component Analysis (PCA) was also used for dimensionality reduction and visualization.

Methodology
1. Feature Preparation

Numerical air-quality and environmental variables were selected for clustering.

2. Feature Scaling

The features were standardized using:

StandardScaler()

Scaling was important because the variables have different numerical ranges.

3. K-Means Clustering

Multiple values of k were evaluated.

The clustering process used:

KMeans(
    n_clusters=k,
    n_init=10,
    random_state=42
)
4. Silhouette Analysis

Silhouette scores were calculated for different cluster counts.

This provided a quantitative method for comparing clustering configurations.

5. PCA Visualization

PCA was applied to reduce the feature space to two principal components.

The clusters were then visualized in a two-dimensional space.

6. Cluster Profiling

Cluster-level averages were analyzed for important variables including:

CO(GT)
NOx(GT)
NO2(GT)
C6H6(GT)
Temperature
Relative Humidity
Absolute Humidity
Outcome

The clustering workflow demonstrated how observations can be grouped based on their overall air-quality and environmental characteristics without using a predefined target variable.

🤖 Task 4 – Supervised Machine Learning
Objective

Task 4 transformed the problem into a supervised regression task.

The target variable was:

CO(GT)

The objective was to predict carbon monoxide concentration using the available air-quality measurements.

Models Used

Two regression models were implemented:

Linear Regression
Random Forest Regressor
Linear Regression

Linear Regression was used as a baseline model.

Results
Metric	Linear Regression
MAE	0.3799
RMSE	0.5590
R²	0.8334
Random Forest Regressor

A Random Forest model was trained to capture nonlinear relationships between the air-quality variables and the target.

Results
Metric	Random Forest
MAE	0.2530
RMSE	0.4098
R²	0.9105
Model Comparison

Random Forest performed better than Linear Regression across all three evaluation metrics.

Improvement

Compared with Linear Regression:

MAE decreased by approximately 33.4%
RMSE decreased by approximately 26.7%
R² increased from 0.8334 to 0.9105

The Random Forest model was therefore selected as the stronger supervised learning model for the project.

Evaluation Visualizations

The task included:

Model performance comparison
Actual vs predicted values
Feature importance
Residual analysis
🧠 Task 5 – Deep Learning
Objective

Task 5 extended the regression problem into a deep learning approach.

The objective was to predict:

CO(GT)

using a feed-forward neural network.

Framework

PyTorch

The model was implemented as a fully connected Artificial Neural Network.

Architecture
Input Features
      ↓
Dense Layer – 64 neurons
      ↓
ReLU
      ↓
Dropout (0.20)
      ↓
Dense Layer – 32 neurons
      ↓
ReLU
      ↓
Dense Layer – 16 neurons
      ↓
ReLU
      ↓
Output Layer – 1 neuron
      ↓
Predicted CO(GT)
Training

The model used:

Mean Squared Error (MSE) loss
Adam optimizer
Learning rate of 0.001
Batch size of 64
Weight decay
Early stopping
Training and validation monitoring

The numerical features were standardized before being passed to the neural network.

Evaluation

The deep learning workflow included:

Training & Validation Loss

Training and validation loss were monitored across epochs to evaluate convergence and possible overfitting.

Actual vs Predicted

Predicted CO values were compared with the actual values.

The plot showed a strong positive relationship between actual and predicted values, while some larger errors remained.

Residual Analysis

Residuals were analyzed to identify observations where the neural network struggled to accurately predict CO concentration.

Key Outcome

The neural network successfully learned a nonlinear mapping between the available air-quality/environmental variables and CO(GT).

However, residual analysis also showed that prediction errors remain for some observations, particularly where the underlying measurements are difficult to explain using the available features.

🏆 Task 6 – Integrative Capstone Project
Objective

Task 6 integrates the techniques developed throughout Tasks 1–5 into a single end-to-end Data Science workflow.

The capstone combines:

Raw Data
   ↓
Data Cleaning
   ↓
EDA & Visualization
   ↓
Feature Engineering
   ↓
Supervised Learning
   ↓
Unsupervised Learning
   ↓
Model Evaluation
   ↓
Insights & Recommendations
Feature Engineering

The Datetime column was used to create temporal features:

Hour
Day
Month
DayOfWeek

The final feature set used in the capstone included:

PT08.S1(CO)
C6H6(GT)
PT08.S2(NMHC)
NOx(GT)
PT08.S3(NOx)
NO2(GT)
PT08.S4(NO2)
PT08.S5(O3)
T
RH
AH
Hour
Day
Month
DayOfWeek
Dataset Split

The capstone used:

7,485 training samples
1,872 testing samples
15 features

The data was divided using a reproducible train/test split with:

random_state=42
Supervised Learning

The capstone evaluated:

Linear Regression
Random Forest Regressor

The same results observed in Task 4 were reproduced:

Model	MAE	RMSE	R²
Linear Regression	0.3799	0.5590	0.8334
Random Forest	0.2530	0.4098	0.9105
Best Model

Random Forest Regressor

The Random Forest model achieved the lowest MAE and RMSE and the highest R² among the evaluated supervised models.

Unsupervised Learning

The capstone also applied K-Means clustering to the feature space.

The workflow included:

Feature standardization
Evaluation of multiple cluster counts
Silhouette score comparison
Final K-Means clustering
PCA dimensionality reduction
Two-dimensional cluster visualization
Cluster profiling

This allowed the project to investigate whether observations naturally form groups based on their air-quality and environmental characteristics.

📊 Evaluation Metrics

The project uses appropriate metrics depending on the learning problem.

Regression
MAE

Mean Absolute Error measures the average absolute difference between actual and predicted values.

Lower MAE is better.

RMSE

Root Mean Squared Error penalizes larger prediction errors more strongly.

Lower RMSE is better.

R²

R² measures the proportion of variance in the target explained by the model.

Higher R² is better.

Clustering
Silhouette Score

Silhouette analysis was used to evaluate how well observations fit within their assigned clusters.

Higher silhouette scores generally indicate better-separated and more cohesive clusters.

🛠️ Technologies Used
Programming Language
Python
Data Analysis
Pandas
NumPy
Data Visualization
Matplotlib
Seaborn
Machine Learning
Scikit-learn

Used for:

Linear Regression
Random Forest
K-Means
PCA
StandardScaler
Train/Test Split
Evaluation Metrics
Deep Learning
PyTorch
Development Tools
Jupyter Notebook
PyCharm
Git
GitHub
📁 Outputs

Each task contains its own output directory.

Typical generated outputs include:

Task 1
air_quality_cleaned.csv
Task 2
Correlation heatmap
Distribution plots
Boxplots
Hourly pollution plots
Time-series visualizations
Task 3
Silhouette analysis
K-Means cluster visualization
PCA cluster visualization
Cluster profiles
Task 4
Model comparison
Actual vs predicted plot
Feature importance
Residual analysis
Task 5
Training/validation loss
Actual vs predicted plot
Residual analysis
Neural network model
Prediction results
Task 6
Model comparison
Random Forest predictions
Feature importance
Silhouette scores
K-Means PCA visualization
Clustered dataset
Cluster profiles
🔬 Overall Methodology

The complete project follows a structured Data Science lifecycle.

                 AIR QUALITY DATASET
                         │
                         ▼
              ┌─────────────────────┐
              │ Task 1               │
              │ Data Cleaning        │
              │ & Preprocessing      │
              └──────────┬──────────┘
                         │
                         ▼
              ┌─────────────────────┐
              │ Task 2               │
              │ EDA & Visualization  │
              └──────────┬──────────┘
                         │
              ┌──────────┴──────────┐
              ▼                     ▼
   ┌──────────────────┐   ┌────────────────────┐
   │ Task 3            │   │ Task 4             │
   │ K-Means + PCA     │   │ Regression         │
   │ Clustering        │   │ LR + Random Forest │
   └─────────┬─────────┘   └──────────┬─────────┘
             │                        │
             │                        ▼
             │              ┌───────────────────┐
             │              │ Task 5             │
             │              │ PyTorch Deep       │
             │              │ Learning           │
             │              └─────────┬─────────┘
             │                        │
             └────────────┬───────────┘
                          ▼
              ┌─────────────────────────┐
              │ Task 6                  │
              │ Integrative Capstone    │
              │                         │
              │ End-to-End Evaluation   │
              └─────────────────────────┘
💡 Key Findings

The project demonstrates several important findings from the Air Quality dataset:

The raw dataset required substantial preprocessing before modeling.
The -200 marker represented unavailable measurements and needed to be treated as missing data.
NMHC(GT) contained extremely high missingness and was removed.
Strong correlations exist among several pollutant sensor measurements.
Pollution levels show clear temporal patterns throughout the day.
Different observations can be grouped using unsupervised clustering.
Random Forest substantially outperformed Linear Regression for predicting CO(GT).
The Random Forest model achieved an R² of 0.9105.
A PyTorch neural network was successfully applied to the same regression problem.
Residual analysis shows that even strong models still have difficult observations and prediction errors.
⚠️ Limitations

The project has several limitations:

The dataset contains historical air-quality measurements and may not represent current conditions.
Median imputation can reduce natural variability in the imputed observations.
Removing highly incomplete features can result in loss of potentially useful information.
Correlation does not imply causation.
Extreme observations require domain knowledge before being classified as errors.
Random Forest predictions may not generalize equally well to unseen environmental conditions.
Clustering results depend on feature selection, scaling, and the selected number of clusters.
The neural network requires careful tuning and sufficient training data for optimal performance.
The project does not incorporate external variables such as traffic volume, weather forecasts, geographic information, or industrial activity.
🚀 Future Improvements

Possible future improvements include:

Hyperparameter tuning using GridSearchCV or RandomizedSearchCV
Cross-validation for more robust model evaluation
Additional feature engineering
Time-series forecasting
XGBoost / Gradient Boosting models
More advanced neural-network architectures
Explainable AI techniques such as SHAP
Automated model deployment
REST API integration
Real-time air-quality prediction
Integration with live environmental sensor data
Dashboard development using Streamlit or similar frameworks
▶️ How to Run the Project
1. Clone the Repository
git clone <your-github-repository-url>
cd YuvaIntern_Data_Science_Project
2. Create a Virtual Environment
python -m venv .venv
3. Activate the Environment
Windows PowerShell
.venv\Scripts\Activate.ps1
Windows CMD
.venv\Scripts\activate
4. Install Required Libraries
pip install pandas numpy matplotlib seaborn scikit-learn jupyter torch
5. Open Jupyter Notebook
jupyter notebook

Open the notebooks in the following order:

Task 1
   ↓
Task 2
   ↓
Task 3
   ↓
Task 4
   ↓
Task 5
   ↓
Task 6
📌 Reproducibility

The project uses fixed random seeds where applicable, including:

random_state=42

This helps produce reproducible train/test splits, Random Forest results, and K-Means clustering results.

📚 Learning Outcomes

Through these six tasks, the project demonstrates practical understanding of:

Data acquisition
Data cleaning
Missing-value handling
Duplicate detection
Outlier analysis
Date-time preprocessing
Exploratory data analysis
Data visualization
Correlation analysis
Feature engineering
Feature scaling
Supervised learning
Unsupervised learning
Regression
K-Means clustering
PCA
Model evaluation
Feature importance
Residual analysis
Neural networks
PyTorch
End-to-end Data Science workflow
👨‍💻 Author

Harsh Bilgaiyan

Integrated B.Tech + M.Tech in Information Technology
International Institute of Professional Studies (IIPS), DAVV, Indore
│
├── .gitignore
└── README.md
