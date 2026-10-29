**Country Schools Dataset — Data Science Lab 2
Project Overview
This project completes Data Science Lab 2 using the Country Schools dataset. The assignment requires basic data preprocessing and two unsupervised learning experiments: anomaly detection and cluster analysis. The analysis examines variation in school technology installations across 47 counties.
Objectives
Inspect and preprocess the dataset, including missing values, data types, and consistency checks.
Detect unusual county-level profiles with Isolation Forest.
Group counties with similar characteristics using K-Means clustering.
Visualize and interpret the experimental results.
Dataset
Source: `Country Schools (1).csv` (provided for the assignment).
The raw dataset has 50 rows and 8 columns. It contains 47 county records, one national `TOTAL` summary row, and two blank records. Preprocessing removes the blank records and the national summary row before modeling. The percentage column is converted from percent-formatted strings into numeric values.
Key overall figures across the 47 counties:
Measure	Value
Total schools	21,729
Schools with installations	14,629
Schools pending installation	7,100
Weighted installation completion	67.32%
Tools and Libraries
Python 3
Pandas and NumPy — data cleaning and analysis
Matplotlib and Seaborn — visualizations
Scikit-learn — feature scaling, Isolation Forest, K-Means, and silhouette score
Kaggle Notebooks — execution environment
Methodology
1. Data preprocessing
Load and inspect the CSV dataset.
Examine missing values, duplicates, and data types.
Remove the two blank records and exclude the `TOTAL` aggregate from county-level modeling.
Convert installation percentages into numeric values and validate school counts.
Derive LDDs per installed school and standardize the modeling features with `StandardScaler`.
The three features used for modeling are total schools, percentage installed, and LDDs per installed school.
2. Anomaly detection
Use Isolation Forest with 300 estimators, `contamination=0.10`, and `random_state=42` to identify unusually different county profiles.
Detected anomalies: Kitui, Mandera, Turkana, Marsabit, and Wajir.
These observations are statistically unusual in the selected feature space; an anomaly does not automatically mean that the source data are incorrect.
3. Cluster analysis
Use K-Means with `random_state=42` and `n_init=20`. Compare k = 2 to 6 using the silhouette score to select an appropriate clustering solution.
Clusters (k)	Silhouette score
2	0.4442
3	0.2810
4	0.2978
5	0.2753
6	0.3001
The best tested solution is k = 2:
Cluster	Counties	Mean installation completion
0	41	71.36%
1	6	13.08%
Cluster 1 counties: Turkana, Garissa, Mandera, Wajir, Marsabit, and Samburu. This group has substantially lower average installation completion and may warrant follow-up investigation.
Repository Files
```text
.
├── README.md
├── Country Schools (1).csv
├── Lab 2(1).txt
├── Country_Schools_Lab2_Kaggle.ipynb
├── Country_Schools_Lab2_Executed.ipynb
├── Country_Schools_Lab2_Report.md
└── Lab2_Country_Schools_Analyzed.csv
```
`Country_Schools_Lab2_Kaggle.ipynb` — runnable analysis notebook with code, explanations, and graphs.
`Country_Schools_Lab2_Executed.ipynb` — notebook with saved outputs from execution.
`Country_Schools_Lab2_Report.md` — formal report covering methodology, results, discussion, and conclusion.
`Lab2_Country_Schools_Analyzed.csv` — cleaned and analyzed data with anomaly and cluster information.
Running the Analysis on Kaggle
Open Kaggle and go to Code → New Notebook, or import `Country_Schools_Lab2_Kaggle.ipynb`.
Add `Country Schools (1).csv` as the notebook's input dataset.
Run all cells in order.
Review the tables, figures, anomaly findings, and clustering results.
Save the notebook version with its outputs.
The notebook searches the Kaggle input directory for the CSV file by name, so the dataset can be attached under any Kaggle input folder.
Interpretation and Limitations
Anomaly detection identifies individual unusual counties, whereas clustering identifies groups of similar counties. Four flagged anomalous counties belong to the low-completion cluster, while Kitui is an anomaly in the larger cluster. The results depend on the selected variables, scaling, model parameters, and this 47-county dataset. They support exploratory analysis, not causal conclusions about why installation rates differ.
Conclusion
The assignment demonstrates how preprocessing, Isolation Forest, and K-Means can be combined to examine county-level differences in school installation coverage. The resulting anomaly flags and two-cluster grouping highlight areas for closer examination.
Academic Context
Coursework: Data Science — Lab 2  
Dataset: Country Schools  
Assignment topics: Data preprocessing, anomaly detection, and cluster analysis**
