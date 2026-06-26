Formula 1 Race Outcome Prediction

Decision Support System (DSS) based on the KDD process for predicting top 10 finishes in the Turbo-Hybrid Era.

This project applies the complete Knowledge Discovery in Databases (KDD) process to the domain of Formula 1, integrating historical data from 2014 to 2023 to train an advanced binary classifier (Random Forest). The model is capable of estimating the probability of success (Top 10) of a car relying exclusively on parameters known before the start of the race.

Project Objective

To develop an interactive, strategic pit wall tool (Decision Support System) that helps track engineers quantify risk and probabilities of success before the lights go out, by combining:

Grid Position (Grid)

Scuderia (Constructor)

Circuit (Location)

The global accuracy achieved is approximately 79.9% with perfectly balanced metrics (F1-Score of ~80.2%), positioning itself very close to the physical limit of predictability in a highly stochastic domain such as Formula 1.

KDD Project Structure in 6 Phases

Phase 1: Data Selection

Cascade relational integration of the results.csv, races.csv, and constructors.csv tables (Ergast API via Kaggle).

Temporal scoping: Exclusive selection of the Turbo-Hybrid Era (2014-present) to ensure the technological coherence of the dataset.

Phase 2: Data Pre-processing & Prevention of Data Leakage

Creation of the target binary variable target_points (1 if finishing position ≤ 10, 0 otherwise).

Removal of in-race variables (laps, times, status/retirements) to prevent Data Leakage.

Data cleaning (pit-lane starts indicated by grid=0 and null values represented by \N).

Phase 3: Data Transformation

One-Hot Encoding to handle categorical variables (Scuderie and Circuits) while avoiding the Dummy Variable Trap.

Stratified splitting of the dataset (80% Training, 20% Testing) to keep the class distribution unaltered.

Standardization of the grid feature using StandardScaler.

Phase 4: Data Mining

Training of a Random Forest Classifier (100 estimators, maximum depth limited to 10 to prevent overfitting).

Handling class imbalance using class_weight='balanced'.

Phase 5: Evaluation and Interpretation

Evaluation via a symmetric Confusion Matrix (TN: 351, FP: 93, FN: 87, TP: 365).

Analysis of the impossibility of reaching 100% accuracy due to random on-track events (Safety Cars, weather, mechanical failures).

Phase 6: Deployment & DSS

Development of the optimized simula_gara_veloce() function.

Implementation of an interactive panel in Jupyter Notebook using ipywidgets for real-time inference without computational lag.

Requirements and Installation

To reproduce the project locally and use the interactive DSS, follow these steps:

Clone the repository:

git clone [https://github.com/YourUsername/YourRepositoryName.git](https://github.com/YourUsername/YourRepositoryName.git)
cd YourRepositoryName


Create and activate a Python virtual environment:

python -m venv f1_env
# On Windows (PowerShell):
.\f1_env\Scripts\Activate.ps1
# On Mac/Linux:
source f1_env/bin/activate


Install the required dependencies:

pip install pandas numpy matplotlib seaborn scikit-learn ipywidgets


Start the Notebook:
Open the main .ipynb file in VS Code (or Jupyter Lab), making sure to select the kernel of the newly created virtual environment f1_env.

Author

Your Name - Model Development & KDD Integration