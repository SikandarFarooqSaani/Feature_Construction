# Feature_Construction
# 🧠 Feature Construction Using Existing Features  
**AI Generated README — Created for Educational Clarity and Documentation Ease**

---

## 📘 Overview
This project demonstrates **feature construction (feature engineering)** using the **Titanic dataset**, where we generate new, meaningful variables from existing features to improve model performance.  

The process highlights how combining and transforming features like `SibSp`, `Parch`, and `Name` can lead to improved predictive accuracy.

---

## ⚙️ Steps and Process

### **1. Dataset Overview**
- Dataset: **Titanic Dataset** (included in repository).  
- Columns of interest: `SibSp`, `Parch`, and `Name`.  
- Initial cleaning: Removed all null rows.  

---

### **2. Baseline Model**
- Model used: **Logistic Regression**  
- Cross-validation score before feature construction: **0.69**  

---

(Added `1` to include the passenger themselves.)

- This represents **the total number of people in a family** traveling together.

---

### **4. Deriving Family Type Feature**
Defined a function to categorize family sizes:
```python
if family_size == 1 → 0 (Alone)
if 2 ≤ family_size ≤ 4 → 1 (Small Family)
if family_size > 4 → 2 (Large Family)
```
Applied the function to the new FamilySize column.

Created a new feature named FamilyType with values 0, 1, 2.

Dropped old columns: SibSp, Parch, and FamilySize.

### 5. Model After Feature Construction

Applied Logistic Regression again.

Cross-validation score improved to 0.700.
✅ Improvement in accuracy shows that feature construction added valuable information.

### 6. Feature Extraction from Name

Next, we used the Name column for advanced feature engineering.

Step 1: Extract Title

Used str.split() on the Name column to extract titles (e.g., Mr., Mrs., Miss., Master.).

Stored results in a new column Title.

Step 2: Analyze Titles

Used value_counts() to check the frequency of each title.

Grouped passengers by title to analyze survival trends.

For example: Mrs. had a higher survival rate than Mr..

Step 3: Derive “Married” Feature

Created a new binary column Married:

Married = 1 if Title == 'Mrs' else 0


This feature helps capture social and demographic patterns from the dataset.

### 📊 Results Summary
Step	Feature Added	Cross-Val Score	Improvement
Initial Model	None	0.690	—
After FamilyType	✅ FamilyType	0.700	+0.010
📎 Attachments

(Visualizations can include correlation heatmap, title frequency chart, and feature importance plot — not shown here.)

### 🧩 Key Insights

Feature construction from existing attributes can improve model performance even without adding new data.

Creating interpretable features (like FamilyType and Married) helps algorithms capture social context.

Using domain knowledge (like titles implying gender/marital status) is essential for real-world modeling.

⚠️ This README is AI-generated based on a structured prompt to help learners and readers clearly understand the process of feature construction and its impact on model accuracy.
