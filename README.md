# Robotic Failure Prediction  
*Predictive analytics project using regression and decision‑tree modeling to identify early indicators of robotic system failure.*

This project investigates whether robotic failure—measured by the **protective stops** variable—can be predicted using operational parameters such as electrical currents, temperatures, and joint speeds. The analysis uses SAS Enterprise Miner to build, compare, and evaluate predictive models.

---

## 📊 Dataset Overview
The dataset comes from the **UCI Machine Learning Repository** and contains:

- **23 multivariate time‑series variables**  
- Operational parameters from a UR3 collaborative robot (temperatures, currents, joint speeds, protective stops)  
- 7,355 non‑missing observations and **54 missing values per variable**  
  > “All the variables have the same number of missing values… 7355 non‑missing variables which is a great sample size.”  

The **timestamp** variable was excluded, and all other variables were used as inputs.

---

## 🧠 Business Question
**Can robotic failure be predicted using electrical currents, temperatures, and joint speeds?**

### Hypotheses  
- **H0:** These variables are *not* statistically relevant for predicting protective stops  
- **HA:** These variables *are* statistically relevant and produce a model better than random guessing  

---

## 🧹 Data Preparation
- Missing values were imputed using SAS Enterprise Miner’s **Impute** node  
- Outlier investigation showed that **Variable 23** appeared unusual, but was simply a binary variable and retained  
  > “Variable 23 could be considered an outlier… it was just a binary variable, thus it was not filtered out.”  

- Histograms confirmed most variables were normally distributed with no extreme distortions

---

## 🔧 Modeling Approach

### **1️⃣ Regression Model**
The regression model was used to identify which variables most strongly predict protective stops.

**Key results:**
- Lift remained **above 2 for 40% of the data**  
  > “The lift maintains above 2 for 40% of the data… the model is 2 times better at predicting protective stops than random guessing.”  
- Validation ASE: **0.035393**  
- Training and validation ASE were similar → **no overfitting**

### **2️⃣ Decision Tree Model**
A decision‑tree model was built to compare performance and interpretability.

**Key results:**
- Lift also remained **above 2 for ~40% of the data**  
- Higher lift than regression for the **top 10%** of cases  
- Important variables included:  
  - **Variable 8:** joint temperature  
  - **Variable 15:** joint speed  
  - **Variable 5:** electrical current  
  > “Variable 8 is the temperature… variable 15 is the speed… variable 5 is the current.”  
- Validation ASE: **0.037364** (slightly higher than regression)

### **3️⃣ Model Comparison**
A model comparison node was used to evaluate both models side‑by‑side.

**Findings:**
- Regression had slightly lower ASE  
- Decision tree had stronger lift for the top decile  
- Both models significantly outperformed random guessing

---

## ✅ Final Conclusion
Both models demonstrated statistically significant predictive power.

> “Both models prove to show that for 40% of the data, the model is 2 times a better predictor than random guessing… the Null Hypothesis can be rejected.”

**Conclusion:**  
Electrical currents, temperatures, and joint speeds **are meaningful predictors** of robotic failure, and the protective stop variable can be modeled with strong accuracy.

---

## 📚 Lessons Learned
- Importance of handling missing data and outliers  
- How regression and decision‑tree models differ in interpretability and performance  
- How lift charts and ASE guide model selection  
- Opportunities for future improvement:  
  - Neural networks  
  - Gradient boosting  
  - Partial least squares  
  - Ensemble modeling  
  > “Next steps… could include neural networks, boosting, or using a node that uses all the models’ superpositions.”  

---

## 🛠️ Tools & Technologies
- SAS Enterprise Miner  
- Regression modeling  
- Decision trees  
- Lift charts & fit statistics  
- UCI Machine Learning Repository dataset  

---

## 📁 Project Files
- `roboticFailurePredictionPortfolioProject.docx` — full analysis report  
- `RoboticFailurePrediction.sas` — SAS modeling code  
- Dataset from UCI ML Repository  

