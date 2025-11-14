
# Student Dropout Risk Analysis

This project analyzes a simulated academic dataset of students using basic data analysis and a custom risk score.  
The goal is to identify students with a higher risk of dropout based on **absences**, **average grade**, and **attendance**.

The project is part of my Data Science learning journey and is focused on:

- Cleaning and exploring tabular data in Python  
- Creating a simple **risk score** that combines behavior and performance  
- Visualizing relationships between absences, grades, and attendance  
- Interpreting results to suggest possible interventions

---

## 1. Dataset Description

The dataset contains **150 students** and the following columns:

- `StudentID` – unique identifier for each student  
- `Class` – class group (A, B or C)  
- `Absences` – number of recorded absences  
- `AverageGrade` – final average grade (0–10 scale)  
- `Attendance` – overall attendance percentage (0–100%)

> The data is simulated for learning and portfolio purposes.  
> No real student information is used.

---

## 2. Risk Score Definition

To estimate dropout risk, we define a score that gives higher risk to students who:

- have **more absences**, and  
- have **lower grades**.

Steps:

1. Normalize absences to a 0–1 scale:  
   `absences_norm = (Absences - min(Absences)) / (max(Absences) - min(Absences))`

2. Normalize grades and invert (so lower grades mean higher risk):  
   `grade_norm_inv = 1 - (AverageGrade - min(AverageGrade)) / (max(AverageGrade) - min(AverageGrade))`

3. Combine both with equal weight and scale to 0–100:  
   `risk_score = round(100 * (0.5 * absences_norm + 0.5 * grade_norm_inv))`

4. Classify risk levels:  
   - **High** risk: score ≥ 70  
   - **Medium** risk: 40–69  
   - **Low** risk: < 40  

---

## 3. Files in This Repository

- `data/students.csv`  
  Simulated dataset with 150 student records.

- `src/risk_score.py`  
  Helper functions to compute the risk score and risk level.

- `notebooks/analysis.ipynb`  
  Jupyter Notebook with exploratory data analysis, score computation and visualizations.

- `requirements.txt`  
  Python dependencies for running the notebook.

---

## 4. How to Run the Project

1. (Optional) Create and activate a virtual environment.

2. Install the dependencies:

```bash
pip install -r requirements.txt
```

3. Start Jupyter Notebook:

```bash
jupyter notebook
```

4. Open:

```text
notebooks/analysis.ipynb
```

---

## 5. Technologies Used

- Python 3  
- pandas  
- NumPy  
- Matplotlib  
- Jupyter Notebook

---

## 6. Author

**Nathalia Rüesch Neiva**  
Data Science & Behavioral Analysis Student  
Based in Bern, Switzerland
