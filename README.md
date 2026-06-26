# Formula 1 Race Outcome Prediction

> **Knowledge Discovery in Databases (KDD) project for race outcome prediction using Machine Learning.**

![Project Status](https://img.shields.io/badge/Status-Completed-success)
![Python Version](https://img.shields.io/badge/Python-3.8%2B-blue)
![Scikit-Learn](https://img.shields.io/badge/Library-Scikit--Learn-orange)
![License](https://img.shields.io/badge/License-MIT-green)

## Project Overview
This repository contains a structured data science project that applies the complete Knowledge Discovery in Databases (KDD) process to Formula 1 historical telemetry and race data. The objective is to develop a predictive model capable of classifying whether a car will finish in the points (Top 10) or not, serving as a framework for a Decision Support System (DSS) for race engineers.

The system implements a regularized Random Forest Classifier to extract patterns from pre-race variables (such as grid position, constructor, and circuit), prioritizing strategic reliability and interpretability in the highly stochastic environment of the modern Turbo-Hybrid Era (2014-Present).

---

## The KDD Process Workflow
The project architecture strictly follows the standard KDD methodology:

1. **Data Selection:** Targeting and extracting the required historical race records, constructor metadata, and circuit details from the Ergast Developer API to define the baseline dataset.
2. **Data Pre-processing:** Assessment of data quality, checking for missing values, and conducting exploratory distribution analysis. Strict removal of in-race variables (laps, times, status) was enforced to prevent Data Leakage.
3. **Data Transformation:** Data preparation via One-Hot Encoding for nominal categorical variables (Constructors and Circuits), dataset partitioning into training (80%) and testing (20%) subsets, and Z-score standardization for continuous variables (Grid).
4. **Data Mining:** Algorithmic extraction of predictive patterns using an ensemble Random Forest Classifier with controlled tree depth (max_depth=10) and balanced class weights to mitigate overfitting.
5. **Evaluation and Interpretation:** Performance evaluation prioritizing a balanced F1-Score (80.22%) and Recall. Interpretation is conducted via Feature Importance ranking and Confusion Matrix analysis.
6. **Use of Discovered Knowledge:** Operational deployment simulated through an interactive Python script that intercepts out-of-distribution inputs before executing the probabilistic predictive pipeline.

---

## Repository Structure
* `main.ipynb`: The primary Jupyter Notebook containing the segmented KDD phases and executable Python code.
* `results.csv`, `races.csv`, `constructors.csv`: The targeted datasets containing historical race records.
* `requirements.txt`: The list of required Python libraries and dependencies.
* `README.md`: Project documentation.

---

## Dataset Attributes
The model processes the following features extracted from the historical dataset prior to the race start:
* `grid`: Starting position of the car on the starting grid (1 to 20).
* `name_constructor`: Official name of the racing team (e.g., Ferrari, Mercedes, Red Bull).
* `circuitId`: Numerical identifier corresponding to the specific race track.
* `target_points`: Target binary variable (1 = Top 10 finish; 0 = Outside Top 10 or DNF).

---

## Installation and Setup

### Prerequisites
Ensure you have Python 3.8 or a later version installed on your operating system.

### Environment Configuration
To prevent dependency conflicts, it is recommended to deploy the project within an isolated virtual environment.

1. Clone or download this repository to your local machine.
2. Open the terminal or command prompt inside the project directory and execute the following commands:

```bash
# Create a virtual environment named 'f1_env'
python -m venv f1_env

# Activate the environment (Windows Command Prompt / PowerShell)
.\f1_env\Scripts\activate

# Activate the environment (macOS / Linux)
source f1_env/bin/activate