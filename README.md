# R Markdown Scripts for the Analysis  
### *Mortality Risk of COVID-19 Pandemic and Human Development*

This repository contains the R Markdown files used to generate the analyses for the study *Mortality risk of COVID-19 pandemic and human development*.  
All `.Rmd` files in `src/` include both explanatory text and executable code. The scripts reproduce the full analytical workflow, and accompanying notes describe data sources and preprocessing steps.

The analysis can be executed on a single CPU core; however, use of multiple cores is recommended (default: 30 cores).

Preprocessed data products are available via the Open Science Framework (OSF):  
https://osf.io/gekzp/overview?view_only=9d602f0d3fad45c1829b2f60c4d4c6f0

---

## Input Data  
Input data files are available on OSF in the folder **`Input_data`**.  
To run the scripts, either:

1. Copy the `Input_data` folder into the cloned repository, or  
2. Follow the instructions in the individual `.Rmd` files to download the data manually.

---

## Markdown Scripts

### **01_DimensionReduction.Rmd**  
Performs Ensemble Isomap (e-Isomap) dimension reduction using the World Development Indicators dataset.

**Main outputs:**  
- Consolidated WDI dataset  
- Ten e-Isomap dimensions  
- Output file: `wdi_data_cons_df`

*Note:* The processed dataset (`01_wdi_data_cons_df_250.csv`) is also available on OSF.

---

### **02_Predictive_performance.Rmd**  
Evaluates predictive performance across different data-compression approaches, including:  
- Complete-case analysis  
- Gap-filled raw data  
- PCA  
- Isomap  
- e-Isomap  

**Main output:**  
- Summary statistics comparing all compression states

---

### **03_Model_components.Rmd**  
Combines model components to construct the integrated model used in the publication.

**Main output:**  
- Final model summary statistics  
- Output file: `03_XX_Xgboost_E_iso10_models.RDS`

---

### **04_plot_outline.Rmd**  
Produces the figures included in the publication and additional visualizations relevant to supplementary analyses.

---

For additional information or clarification, please feel free to inquire.

_______ 
# Abstract

**Background:** During the global COVID-19 pandemic (2020–2021), excess mortality varied substantially across countries. Notably, upper-middle-income countries experienced greater variability in excess mortality than both low- and high-income countries, despite reporting fewer COVID-19 cases. This disconnect between case numbers and mortality suggests more complex structural vulnerabilities. Socioeconomic conditions and healthcare system performance, collectively referred to as National Framework Conditions (*NFCs*), are likely key determinants of pandemic outcomes. However, the specific relationship between these factors and excess mortality remains poorly understood.

**Methods::** We constructed a predictive model of excess mortality using reported COVID-19 case counts and a wide array of *NFCs* derived from the World Development Indicators (WDI), employing a tree-based machine learning method (XGBoost). To reduce dimensionality, we applied a non-linear method (e-Isomap), extracting latent components called compressed National Framework Conditions (*cNFCs*). We applied SHapley Additive exPlanations (SHAP) to estimate the feature importance and quantify the contribution of each *cNFC*.

**Results:** Our machine learning model explained nearly half of the global variance in excess mortality (*R^2*: median 49.7; IQR: 10.9). SHAP analysis revealed that *cNFCs* contributed most strongly to model predictions of excess mortality (Median: 8.1, IQR: 1.2), followed by *pandemic indicators*, such as reported COVID-19 cases (Median: 6.4, IQR: 0.7). Using explainable AI, we further identified how interconnected socioeconomic conditions, including labor force participation age and health spending, shaped mortality outcomes.


**Conclusion** Our findings demonstrate that *cNFCs* outperform conventional epidemiological or preparedness metrics. By capturing latent socioeconomic structures, the *cNFC* framework reveals systemic vulnerabilities that reported COVID-19 cases and other indicators fail to detect. This approach offers a new perspective on
