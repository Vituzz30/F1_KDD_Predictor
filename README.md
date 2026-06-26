F1RaceOutcomePredictor

Knowledge Discovery in Databases (KDD) project for Formula 1 race outcome classification using Machine Learning.

Formula 1 Race Outcome Prediction via Knowledge Discovery in Databases (KDD)

Project Overview

This repository contains a structured data science project that applies the complete Knowledge Discovery in Databases (KDD) process to historical Formula 1 race data. The objective is to develop a predictive model capable of classifying whether a driver will finish in the top 10 (points-scoring positions), serving as a framework for a Race Decision Support System (DSS).

The system implements a regularized Random Forest Classifier to extract competitive patterns from pre-race attributes (such as grid starting position, constructor competitiveness, and circuit specificities), prioritizing strategic reliability and real-time interpretability on the pit wall.

The KDD Process Workflow

The project architecture strictly follows the standard KDD methodology, divided into six sequential phases:

Data Selection: Targeting and integrating the required results, races, and constructor records from the Ergast API database to establish a stable baseline representing the modern Turbo-Hybrid Era (2014-present).

Data Pre-processing: Mitigating data leakage by removing in-race parameters, cleaning missing values, and executing exploratory boxplot analysis to isolate the statistical signal of starting grid positions.

Data Transformation: Data preparation via One-Hot Encoding for categorical variables (scuderias and circuits), stratified splitting into training (80%) and testing (20%) partitions to preserve class balance, and Z-score standardization for the starting grid feature.

Data Mining: Algorithmic extraction of competitive patterns using an ensemble Random Forest Classifier with maximum tree depth restrictions to control model complexity and prevent overfitting.

Evaluation and Interpretation: Performance evaluation prioritizing the F1-Score (80.22%) and balanced Precision/Recall over global accuracy to prevent directional bias. Interpretation is supported by analyzing the physical limits of predictability under highly stochastic race conditions.

Use of Discovered Knowledge: Operational deployment in a low-latency Decision Support System (DSS) using interactive widgets with continuous update protection to simulate real-time pit wall decision-making.

Repository Structure

The project is organized into the following essential files:

progetto_f1.ipynb - The primary Jupyter Notebook containing the segmented KDD phases and executable Python code.

fase_6_ottimizzata.py - The optimized Python script implementing the interactive DSS simulator.

README.md - Project documentation and deployment instructions.

.gitignore - Git exclusion rules for virtual environments, raw CSV datasets, and Python cache files.

Dataset Attributes

The machine learning model processes the following features extracted from the historical dataset:

grid - Starting position of the car on the grid (1 to 20).

name_constructor - The official name of the constructor/scuderia.

circuitId - The unique identifier of the race track.

target_points - Diagnostic target representing the race outcome (1 = finished in the Top 10; 0 = finished outside the points).

Installation and Setup

Prerequisites

Ensure you have Python 3.8 or a later version installed on your operating system.

Environment Configuration

To prevent dependency conflicts, it is recommended to deploy the project within an isolated virtual environment. Follow these steps in order:

Clone or download this repository to your local machine.

Open your terminal or command prompt inside the project directory.

Execute the following commands to set up and activate the virtual environment:

# Create a virtual environment named 'f1_env'
python -m venv f1_env

# Activate the environment (Windows Command Prompt / PowerShell)
f1_env\Scripts\activate

# Activate the environment (macOS / Linux)
source f1_env/bin/activate


Install all the required Python libraries and dependencies:

pip install pandas numpy matplotlib seaborn scikit-learn ipywidgets


Launch VS Code or Jupyter Notebook, select the f1_env kernel, and run the cells in progetto_f1.ipynb to explore the project.