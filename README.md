# Predictive Churn Analysis in Telecom

![Project Status: Completed](https://img.shields.io/badge/status-completed-brightgreen)

## 📄 Project Description

This project aims to develop a Machine Learning model capable of predicting the likelihood of a telecom company's customer canceling their service (a phenomenon known as *churn*). The proactive identification of customers with a high propensity to churn allows the company to take targeted retention measures, optimizing resources and reducing revenue loss.

The `TelecomX_part2_v3.ipynb` notebook documents the entire process, from data cleaning to the final evaluation and selection of a classification model based on a strategic analysis of business metrics.

## 🚀 Methodology and Steps Taken

The project was structured following a robust Data Science pipeline, ensuring the quality and reproducibility of the results. The main stages were:

### 1. Data Loading and Cleaning
- **Data Source:** The project uses the `telecom_churn.csv` dataset.
- **Cleaning:** An initial analysis was performed to identify and handle missing values. Rows with a null target variable (`churn`) were removed to ensure the integrity of the training and evaluation processes.
- **Exploration:** Verification of data types and variable distributions.

### 2. Preprocessing and Feature Engineering
- **Categorical Variable Transformation:** Columns with textual data (e.g., `contract`, `payment_method`) were transformed into a numerical format using the **One-Hot Encoding** technique.
- **Target Variable Transformation:** The `churn` variable (with 'Yes'/'No' values) was converted to a binary format (1/0) using the `LabelEncoder`.

### 3. Handling Class Imbalance
- **Diagnosis:** A significant class imbalance was identified in the target variable (approximately 73% 'No Churn' vs. 27% 'Churn').
- **Solution:** The **SMOTE (Synthetic Minority Over-sampling TEchnique)** was applied to create synthetic samples of the minority class.
- **Best Practices:** SMOTE was applied **after** the data split and **only** on the training set, an essential practice to prevent *data leakage* and ensure a realistic model evaluation.

### 4. Modeling and Feature Selection
- **Experimentation:** Multiple algorithms were trained and evaluated:
    - `DummyClassifier` (as a baseline)
    - `DecisionTreeClassifier`
    - `LogisticRegression`
    - `OLS` (Ordinary Least Squares) from `statsmodels`
- **Feature Selection:** The OLS model was used as a statistical analysis tool to interpret the importance (`p-value`) of each variable. Based on this analysis, simplified versions of the dataset were created by removing features with low statistical significance, resulting in simpler and more efficient models.

### 5. Evaluation and Final Model Selection
- **Evaluation Metrics:** The models' performance was compared using the `Classification Report`, which includes **Precision**, **Recall**, and **F1-Score**.
- **Strategic Analysis:** The final model choice was not based solely on accuracy but on an analysis of the Precision vs. Recall trade-off, considering the business impact.
- **Champion Model:** The **`Logistic Regression 3`** model was selected. The analysis concluded that although its Recall is low (30%), its high Precision (70%) enables the creation of a highly efficient retention campaign with minimal wasted resources.

### 6. Model Persistence
- **Saving the Pipeline:** The final model, along with all necessary preprocessing objects (like the `OneHotEncoder` and `StandardScaler`), were saved using the `pickle` and `joblib` libraries.
- **Real-World Usage Simulation:** A script was created to load the saved objects and perform predictions on a new CSV file with hypothetical customer profiles, demonstrating the model's practical application.

## 🛠️ Technologies Used
- **Language:** Python 3
- **Core Libraries:**
    - `Pandas`: For data manipulation and analysis.
    - `Scikit-learn`: For preprocessing, modeling, and Machine Learning evaluation.
    - `Imbalanced-learn`: For the SMOTE resampling technique.
    - `Statsmodels`: For statistical analysis with the OLS model.
    - `Joblib` & `Pickle`: For saving and loading trained models.
    - `PrettyTable`: For creating the final results table.

## 🚀 How to Run the Project

1. **Clone the repository:**
   ```bash
   git clone [YOUR-REPOSITORY-URL]
   ```
2. **Install the dependencies:**
   ```bash
   pip install pandas scikit-learn imbalanced-learn statsmodels prettytable
   ```
3. **Run the Notebook:**
   - Open and run the `TelecomX_part2_v3.ipynb` file in a Jupyter environment (like Jupyter Notebook, Jupyter Lab, or Google Colab) to see the entire analysis and training process.

4. **Test the Prediction (Optional):**
   - Run the final scripts to save and load the models and make predictions on new data.

## 📈 Conclusion

The project resulted in a Logistic Regression model capable of identifying churning customers with 70% precision, providing the business with a valuable tool to strategically target its retention campaigns for a high return on investment.
