Hospital Operations, Cost & Patient Flow Intelligence

1. Introduction and Business Problem

Healthcare organisations need reliable information about the costs associated with different types of patient encounters to support effective financial planning and resource allocation. Understanding how healthcare costs vary across encounter classes can help hospital management identify cost patterns and make more informed operational decisions.

However, without analysing historical healthcare data, management may have limited insight into the differences in recorded costs across services such as ambulatory care, outpatient care, emergency care, inpatient care, urgent care and wellness services.

This project analyses historical healthcare encounter data provided by AnalystLab Africa to investigate variations in recorded healthcare costs across different encounter classes. The analysis uses exploratory data analysis, descriptive statistics, data visualisation and statistical modelling to examine these cost differences.

The findings are intended to help hospital management and financial decision-makers better understand recorded encounter cost patterns and support evidence-based financial and operational planning.

The analysis is limited to the information available in the supplied datasets. Therefore, the findings describe recorded costs and statistical associations rather than establish the causes of cost differences.
2. Project Objectives and Research Question

2.1 General Objective

To analyse variations in recorded healthcare encounter costs across different encounter classes using historical healthcare data.

2.2 Specific Objectives

1. To examine the structure and characteristics of the supplied healthcare datasets.
2. To assess the quality and completeness of the encounter data.
3. To calculate and compare descriptive statistics for healthcare costs across different encounter classes.
4. To use data visualisations to identify patterns and variations in recorded encounter costs.
5. To apply appropriate statistical methods to determine whether recorded healthcare costs differ significantly across encounter classes.
6. To provide evidence-based insights that may support hospital financial planning and operational decision-making.

2.3 Research Question

Do recorded healthcare encounter costs differ significantly across different encounter classes?
3. Dataset Description

The project used six healthcare-related CSV datasets supplied by AnalystLab Africa. These datasets contained information about patient encounters, patients, medical procedures, healthcare payers, healthcare organisations and variable definitions.

The datasets consisted of:

Dataset	Number of Records	Number of Variables
Encounters	27,891	14
Patients	974	20
Procedures	47,701	9
Payers	10	7
Organizations	1	8
Data Dictionary	65	3

The encounters dataset was the primary dataset used for the cost analysis. It contained information about encounter dates, encounter classes, encounter descriptions, base encounter costs, total claim costs and payer coverage.

The main variables used in the analysis included:

* ENCOUNTERCLASS: The category of healthcare encounter.
* BASE_ENCOUNTER_COST: The recorded base cost associated with an encounter.
* TOTAL_CLAIM_COST: The recorded total claim cost.
* PATIENT: The identifier used to distinguish individual patients and account for repeated encounters.
* START and STOP: The recorded start and end dates of encounters.

The encounters dataset contained 27,891 records representing 974 unique patients. It provided the primary information required to investigate differences in recorded healthcare costs across encounter classes.
4. Data Preparation and Quality Assessment

The datasets were uploaded into Google Colab and analysed using Python. The Pandas library was used for data loading, manipulation and summarisation, while NumPy supported numerical operations. Matplotlib and Seaborn were used for data visualisation, and SciPy and Statsmodels supported statistical analysis.

The encounters dataset was inspected to understand its structure, variable names, data types and record counts. The analysis focused on the encounter identifier, encounter class, patient identifier, base encounter cost and total claim cost.

Data quality checks were conducted on the key variables used in the analysis. The checks identified no missing values in the encounter identifier, encounter class, base encounter cost or total claim cost. No duplicate encounter identifiers were detected.

The analysis also identified 89 encounters with a recorded total claim cost of zero, representing approximately 0.32% of all encounters. No negative total claim costs were found.
5. Methodology

5.1 Exploratory Data Analysis

Exploratory data analysis was conducted to understand the distribution of healthcare encounters and the characteristics of recorded costs. Encounter frequencies were calculated to identify the most common encounter classes.

Descriptive statistics, including the mean, median, standard deviation, minimum and maximum values, were used to examine the distribution of base encounter costs and total claim costs.

5.2 Data Visualisation

Five visualisations were produced to explore the cost patterns:

1. Histogram showing the distribution of base encounter costs.
2. Histogram showing the distribution of total claim costs.
3. Bar chart comparing average total claim costs across encounter classes.
4. Boxplot comparing total claim costs across encounter classes.
5. Boxplot using a symmetric logarithmic scale to make differences in the highly variable cost distribution easier to examine.

5.3 Statistical Analysis

The Kruskal–Wallis test was initially used to assess whether recorded total claim costs differed across encounter classes. Pairwise Mann–Whitney U tests with Bonferroni adjustment were also conducted as preliminary comparisons.

Further investigation showed that individual patients contributed multiple encounter records. To account for the correlation between repeated encounters belonging to the same patient, a Generalised Estimating Equations (GEE) model was fitted.

The outcome variable, total claim cost, was transformed using the natural logarithm of one plus the recorded cost. Encounter class was included as the explanatory variable, with ambulatory encounters serving as the reference category. An exchangeable working correlation structure and robust standard errors were used.

A sensitivity analysis was also conducted by excluding the ten patients with the highest encounter frequencies. This assessed whether the main findings were substantially influenced by a small group of very frequent patients.

5.4 Statistical Significance

A p-value threshold of 0.05 was used to assess statistical significance. Results were interpreted alongside the estimated coefficients and confidence intervals. The analysis was designed to identify associations between encounter class and recorded costs, rather than establish causation.
The total claim cost variable showed substantial variation, including some exceptionally high recorded values. These observations were retained because the available data did not establish whether they were errors or legitimate high-cost encounters. Their potential influence was considered during the statistical analysis.

Overall, the initial quality checks indicated that the key variables were complete and that encounter identifiers were unique. However, these checks do not establish that every field in the datasets is free from errors.
6. Exploratory Data Analysis and Descriptive Findings

6.1 Distribution of Healthcare Encounters

The analysis identified 27,891 healthcare encounters across six encounter classes. Ambulatory encounters were the most frequent, accounting for 12,537 records, followed by outpatient encounters with 6,300 records. Urgent care accounted for 3,666 encounters, emergency care for 2,322, wellness for 1,931 and inpatient care for 1,135.

Encounter Class	Number of Encounters
Ambulatory	12,537
Outpatient	6,300
Urgent care	3,666
Emergency	2,322
Wellness	1,931
Inpatient	1,135
Total	27,891

These results indicate that ambulatory encounters represented the largest proportion of the available records, while inpatient encounters were the least frequent.

6.2 Overall Healthcare Cost Distribution

The descriptive analysis showed that the mean base encounter cost was 116.18, while the median was 136.80. Base encounter costs ranged from 85.55 to 146.18.

For total claim costs, the mean was 3,639.68, compared with a median of 278.58. Recorded total claim costs ranged from zero to 641,882.70.

The substantial difference between the mean and median total claim costs suggests a highly right-skewed distribution. This indicates that a relatively small number of encounters had exceptionally high recorded costs, increasing the overall average.

These findings demonstrate why both mean and median values are important when examining healthcare cost data.

6.3 Comparison of Costs Across Encounter Classes

The descriptive statistics showed differences in average and median total claim costs across the six encounter classes.

Encounter Class	Average Total Claim Cost	Median Total Claim Cost
Ambulatory	2,894.11	573.98
Emergency	4,629.65	146.18
Inpatient	7,761.35	2,355.59
Outpatient	2,237.30	278.58
Urgent care	6,369.16	142.58
Wellness	4,260.71	1,231.44

Inpatient encounters recorded the highest average total claim cost of 7,761.35, followed by urgent care encounters at 6,369.16. Outpatient encounters had the lowest average total claim cost at 2,237.30.

The median results also showed that inpatient encounters had the highest median total claim cost, while urgent care encounters had the lowest.

The differences between average and median costs, particularly for emergency and urgent care encounters, further demonstrate the influence of highly variable and potentially extreme cost observations.

All cost figures are presented in the dataset’s recorded units because the currency was not specified in the supplied data.
7. Statistical Analysis and Findings

7.1 Preliminary Statistical Tests

The Kruskal–Wallis test produced a test statistic of 2025.19 with a p-value below 0.001. This provided preliminary evidence of differences in recorded total claim costs across encounter classes.

Pairwise Mann–Whitney U tests with Bonferroni adjustment identified statistically significant differences in 14 of the 15 encounter-class comparisons. The comparison between ambulatory and emergency encounters was not statistically significant.

However, further investigation revealed that many patients contributed multiple encounter records. Since observations from the same patient may be correlated, the independence assumption required by these preliminary tests may not have been satisfied. Therefore, these results were not treated as the main evidence for the research question.

7.2 Generalised Estimating Equations Model

A Generalised Estimating Equations (GEE) model was used to investigate differences in recorded total claim costs while accounting for repeated encounters from individual patients.

The model included 27,891 encounter observations from 974 patients. Total claim costs were transformed using the natural logarithm of one plus the recorded cost. Ambulatory encounters were used as the reference category.

The model estimated a within-patient working correlation of approximately 0.403, indicating positive correlation between repeated observations from the same patient.

The results were as follows:

Encounter Class	Coefficient	P-value	Statistical Significance
Emergency	0.0006	0.998	No
Inpatient	1.0719	Less than 0.001	Yes
Outpatient	-0.3476	0.003	Yes
Urgent care	-0.3957	0.042	Yes
Wellness	0.9836	Less than 0.001	Yes

Compared with ambulatory encounters, inpatient and wellness encounters had positive model coefficients, indicating higher recorded costs on the transformed outcome scale. Outpatient and urgent care encounters had negative coefficients, indicating lower recorded costs on that scale.

The emergency encounter coefficient was not statistically significant (p = 0.998), suggesting that the model did not detect a statistically significant difference between emergency and ambulatory encounters.

These results provide evidence that recorded healthcare costs vary across encounter classes, even after accounting for repeated observations from individual patients.

7.3 Sensitivity Analysis

A sensitivity analysis was conducted to assess the influence of patients with exceptionally high encounter frequencies. The ten patients above the 99th percentile of encounter frequency were excluded from the analysis.

Although these patients represented approximately 1.03% of the unique patients, they contributed 5,759 encounters, representing approximately 20.65% of all encounter records.

The sensitivity analysis included 22,132 encounters from 964 patients.

The findings showed that:

* Inpatient encounters remained statistically significant (p less than 0.001).
* Outpatient encounters remained statistically significant (p = 0.002).
* Wellness encounters remained statistically significant (p less than 0.001).
* Urgent care encounters were no longer statistically significant (p = 0.142).
* Emergency encounters remained statistically non-significant (p = 0.075).

The urgent care finding was therefore sensitive to the exclusion of high-frequency patients. The emergency coefficient also changed substantially, indicating that its estimated relationship with ambulatory costs was influenced by the excluded observations, even though it remained statistically non-significant.

Overall, the sensitivity analysis suggests that the findings for inpatient, outpatient and wellness encounters were more consistent, while the urgent care and emergency estimates require cautious interpretation.
