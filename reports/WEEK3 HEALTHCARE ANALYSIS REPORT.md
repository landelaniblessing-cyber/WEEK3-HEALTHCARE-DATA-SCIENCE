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
