# Credit Risk Analysis with PRISM & Decision Trees → DMN

## Overview

This project implements a complete pipeline for **credit risk analysis**, combining:

* Real dataset preprocessing
* Data cleaning and transformation
* Discretization of numerical features
* Rule-based learning using **PRISM**
* Machine learning using **Decision Trees (CART)**
* Export of models into **DMN (Decision Model and Notation)** format

The goal is to create **interpretable decision models** that can be deployed in business rule engines.

---

## Project Structure

```
├── original.csv
├── credit_data.csv
├── credit_dataset_discretized.csv
├── credit_dataset_clean.csv
├── credit_prism_rules.dmn
├── credit_cart_rules.dmn
├── loan_decision_tree.png
├── credit_rules.ipynb
└── README.md
```

---

## Pipeline Steps

### 1. Data Cleaning

* Convert columns to numeric
* Handle missing values using mean
* Fix invalid values (e.g., negative ages)
* Round values for consistency

Output:

```
credit_data.csv
```

---

### 2. Discretization (Categorical Transformation)

Continuous variables are converted into categorical values using quantiles:

* **Age** → young, adult, old
* **Income** → low, medium, high
* **Loan** → small, medium, large

Output:

```
credit_dataset_discretized.csv
```

---

### 3. Dataset Cleaning (Majority Filtering)

* Group by feature combinations
* Keep only the **majority class** per combination
* Remove conflicting records

Output:

```
credit_dataset_clean.csv
```

---

### 4. PRISM Rule Learning

* Extracts IF–THEN rules from categorical data
* Works best with discretized datasets
* Produces human-readable decision rules

---

### 5. PRISM → DMN

The extracted rules are automatically converted into a **DMN decision table**.

Output:

```
credit_prism_rules.dmn
```

---

### 6. Decision Tree (CART)

* Trains a classification model using numerical data
* Limited depth for interpretability
* Produces decision paths

---

### 7. Decision Tree → DMN

* Converts tree paths into rules
* Exports them into DMN format

Output:

```
credit_cart_rules.dmn
```

---

### 8. Visualization

* Decision tree exported as image

Output:

```
loan_decision_tree.png
```

---

## Key Concepts

* **PRISM**: Rule-based classifier for categorical data
* **Discretization**: Converts continuous values into categories
* **CART**: Decision tree algorithm for classification
* **DMN**: Standard for business decision modeling

---

## How to Run

1. Upload dataset (`original.csv`)

2. Run the scripts in order:

   * Cleaning
   * Discretization
   * Majority filtering
   * PRISM
   * CART

3. Outputs will be generated automatically

---

## Output Artifacts

| File                             | Description                |
| -------------------------------- | -------------------------- |
| `credit_data.csv`                | Cleaned numerical dataset  |
| `credit_dataset_discretized.csv` | Categorical dataset        |
| `credit_dataset_clean.csv`       | Conflict-free dataset      |
| `credit_prism_rules.dmn`         | PRISM rules in DMN         |
| `credit_cart_rules.dmn`          | Decision tree rules in DMN |
| `loan_decision_tree.png`         | Tree visualization         |

---

## Notes

* PRISM requires **categorical data**, otherwise rule explosion occurs
* Discretization is critical for interpretability
* Majority filtering reduces contradictions in rules
* DMN enables integration with business rule engines

---
