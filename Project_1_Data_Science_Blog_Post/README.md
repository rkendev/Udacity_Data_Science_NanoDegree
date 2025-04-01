# Data Science Blog Post: Analyzing Financial Development and Stability

This project is part of the Udacity Data Science Nanodegree program. In this analysis, we explore the key financial indicators that influence economic performance and stability across countries. We develop a composite measure of financial development, normalize it within income groups, and use advanced machine learning models to uncover the drivers of relative financial system development.

---

## Business Questions Addressed

1. **What are the key financial indicators that influence economic performance and stability?**  
   We examine variables such as:
   - **FDI_2013_log**:  
     *Definition:* The logarithm of foreign direct investment (FDI) as a percentage of GDP in 2013. This transformation reduces skewness and captures external capital inflows.
   - **NPL_2018_log**:  
     *Definition:* The logarithm of bank nonperforming loans (NPL) as a percentage of total loans in 2018, which measures asset quality and credit risk.
   - **PrivCredit_FS_2013_log**: 
     *Definition:* The logarithm of domestic credit provided to the private sector by the financial sector in 2013. This indicator is particularly dominant, suggesting it is a major driver of relative financial system development.
   - **BroadMoney_2005_log**:
     *Definition:* The logarithm of broad money supply as a percentage of GDP in 2005, reflecting overall liquidity in the economy.

2. **How do the impacts of these indicators differ across regions and income groups?**  
   By normalizing Financial_Depth within income groups—creating **Financial_Depth_z**—we isolate the effect of each predictor relative to its peers. The one-hot encoded **Region_Income** dummies capture additional subgroup effects, highlighting that even after income normalization, regional factors (e.g., differences in regulatory environments or institutional quality) persist.

3. **Can we use a composite measure to summarize the financial system’s development effectively?** 
   We developed composite measures such as **Financial_Depth** (and its log-transformed and normalized versions) to capture overall financial development. The normalized target, **Financial_Depth_z**, proves particularly useful for comparing countries on a level playing field across different income groups.

4. **What policy measures could enhance financial development and stability based on these indicators?**  
   Our feature importance analysis and SHAP visualizations indicate that credit measures—especially **PrivCredit_FS_2013_log**—and money supply (**BroadMoney_2005_log**) are strong predictors of relative performance.
   - **Policy Implication:** Strengthening the domestic credit environment and ensuring stable money supply management are likely crucial for improving financial stability.
   - **Additional Insight:** Persistent regional effects suggest that tailored regulatory reforms could benefit regions that underperform relative to their income peers.

---

## Project Structure


- **analysis.ipynb**: The primary Jupyter Notebook with data cleaning, modeling, and interpretation.
- **analysis.html**: An HTML version of the notebook for easy sharing.
- **data/**: Directory containing the datasets used in the analysis.

---

## Methodology

1. **Data Preparation:**  
   - Cleaning and imputation of missing values.
   - Feature engineering to create composite measures (e.g., Financial_Depth) and to encode regional effects (**Region_Income**).
   - Normalization within income groups to produce **Financial_Depth_z**, which is our target variable.

2. **Modeling:**  
   - A baseline linear regression model is used for interpretability.
   - Advanced ensemble models, including Random Forests and XGBoost, are tuned via cross-validation to capture nonlinear relationships.
   - Our best XGBoost model achieved a test R² of 0.92 and an RMSE of 0.28, indicating robust predictive performance.

3. **Interpretation:**  
   - Feature importance and SHAP analyses identify that domestic credit to the private sector (**PrivCredit_FS_2013_log**) and broad money supply (**BroadMoney_2005_log**) are key drivers.
   - Partial dependence and SHAP dependence plots further clarify the effect and interaction of these predictors.
   - The analysis also highlights persistent regional effects through the **Region_Income** variable.

4. **Policy Implications:**  
   - Enhance private credit systems and ensure effective monetary policy.
   - Tailor regulatory reforms to address specific regional challenges.
   
---

## Installation and Usage

1. **Clone the Repository:**
   ```bash
   git clone <repository_url>
   From the Jupyter based web environment go to the file explorer
   From the the explorer open the file analysis.ipyb and run the cells in the Notebook
   ```

## Results & Discussion



**Normalized Financial Depth:**  

The normalized target (Financial_Depth_z) allows us to focus on how much a country deviates from its income-group norm.



**Dominant Role of Credit Measures:**  

The analysis reveals that **PrivCredit_FS_2013_log** is the most influential predictor, with an importance of about 0.41, followed by **BroadMoney_2005_log**.



**Moderate Influence of Other Indicators:**  

**FDI_2013_log** and **NPL_2018_log** provide additional, but less pronounced, insights.



**Persistent Regional Effects:**  

The one-hot encoded **Region_Income** dummies continue to add predictive power, indicating that regional factors play a significant role even after normalizing by income.



**Model Performance:**  

Advanced models, particularly XGBoost, demonstrated strong predictive power, supporting the robustness of our findings.



---



## Conclusion



The analysis demonstrates that a normalized composite measure of financial development can effectively capture the nuanced impacts of various financial indicators. The dominant role of domestic credit to the private sector and the significance of broad money supply suggest that policies aimed at enhancing credit allocation and managing liquidity are key to improving financial stability. Additionally, persistent regional effects underscore the need for tailored reforms that address unique regional challenges. These insights provide actionable guidance for policymakers and lay the groundwork for further exploration and external validation.


