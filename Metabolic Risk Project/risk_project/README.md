---
title: "README" 
output: html_document
---
Metabolic Risk Drivers in the United States: The Role of Healthcare Access and Geography

Objective: To understand the impacts of healthcare access and geographic
location on the distribution of metabolic syndrome risk factors.

Project Overview: This project analyzes the relationship between metabolic
health indicators (Obesity, Diabetes, Hypertension, and High Cholesterol) and
healthcare access variables (Insurance and Annual Checkups). The study identifies the roles of insurance
coverage, annual checkups, and geographic location in metabolic health. 

Research Question: How do healthcare gaps (insurance and checkup frequency)
explain the geographic distribution of metabolic clusters?
* To what extent do obesity, diabetes, hypertension, and high cholesterol co-occur as a single 'Metabolic Risk Index'?
* How much variance in this risk is explained by insurance coverage vs. routine checkups?
* How much unique variance in metabolic risk is explained by geography (Latitude/Longitude) versus clinical access?


The structure of the code-base

risk.project/
  data/
    us_metabolic_data.Rdata       : Raw CDC PLACES dataset (2020 release) used in analysis
  figs/
    metabolic_risk_fig5.png       : Geographic Distribution of Metabolic Indicators
    metabolic_risk_fig4.png       : National Heatmap of Combined Metabolic Risk 
    metabolic_risk_fig3.png       : Variation Partitioning Plot (Insurance + Annual Checkup + Geography)
    metabolic_risk_fig2.png.      : RDA Biplot (Clinical Access vs. Metabolic Health)
    metabolic_risk_fig1.png.      : Metabolic Cluster Correlation Matrix
  script/
    risk_project_script.Rmd.      : File for code and analysis
  README.md                       : Project documentation

* Software: RStudio
* Libraries:
  * CDCPLACES: for initial API data retrieval
  * vegan: for PCA, RDA, and Variation Partitioning
  * tidyverse: For data manipulation, coordinate cleaning, and reshaping of datasets

Installing
* Download the risk_project folder to your local machine.
* Ensure the raw data file us_metabolic_data.Rdata is located in the data file.
* No modifications to the internal folder structure are needed if using file provided.


Structure of the Data & Metadata
Input: data/us_metabolic_data.Rdata

OBESITY: % of adults with BMI greater than or equal to 30 (numeric).
DIABETES: % of adults diagnosed with diabetes (numeric).
BPHIGH: % of adults with high blood pressure (numeric).
HIGHCHOL: % of adults with high cholesterol (numeric).
ACCESS2: % of adults without health insurance 
insured_perc: % of adults with health insurance (transformed from ACCESS2).
CHECKUP: % of adults with a routine checkup in the past year (numeric).
geolocation: Raw coordinate string (e.g., c(type = "Point", coordinates = "-86.49001, 32.477).
lat / lon: Numeric coordinates (extracted from geolocation)



Instructions on How to Recreate Results
1. Download risk_project folder
2. Open risk_project in RStudio to set the working directory automatically.
3. Open the analysis script: script/risk_project_script.Rmd.
4. Run the setup and data loading chunks to set the environment.
5. Run the geolocation tidying chunk to process the coordinate strings and reshape the data.
6. Run the multivariate modeling and associated figure exports chunks to generate PCA and RDA results and PNGs of each to the figs/ folder.
7. Run the mapping chunks to create static and interactive maps
6. Outputs Generated: 
    * Fig 1: A correlation matrix showing how diseases move together in a metabolic cluster
    * Fig 2: An RDA biplot showing clinical access variables vs. metabolic health
    * Fig 3: A variation partitioning plot showing the overlap of insurance, checkups, and geography variances in explaining metabolic health variables 
    * Fig 4: A map showing combined metabolic risk across the continental US using the metabolic risk index I created
    * Fig 5: A figure stacking 4 maps, each representing a variable within the metabolic risk index, set on one scale for easy comparison
    * 2 leaflet interactive maps of the Southeastern US showing metabolic risk at census tract and county levels

Help:
If lat and lon columns are empty, check that the geolocation string format in your dataset matches the regex pattern in the str_replace_all function.

Acknowledgements
* Developed for the BIOL 470 Statistical Programming Course.
* Data Source: CDC PLACES (2020 Release).
* Thanks to Dr. Dan McGlinn for his mentorship. 

