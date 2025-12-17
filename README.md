# Understanding Spatial Autocorrelation in the HDB Flat Size–Price Relationship in Singapore #

<ins>Authors</ins>
* Liying Choo 
* Lim Kay Yee, Rachel


Course: ST5226, Spatial Statistics<br/>
Institution: National University of Singapore<br/>
Submission Date: 20 Nov 2025

-----

📌 <ins>Project Overview</ins>

This project investigates spatial patterns in HDB resale prices across Singapore using methods taught in ST5226. In particular, we study whether the strength of the flat size–price relationship varies spatially across planning areas, whether such variation is spatially clustered, and whether local amenities explain this heterogeneity. The final report and reproducible analysis code are provided in the files referenced below.

The PDF should be read for conceptual understanding and results, while the Rmd serves as the computational backbone of the project.

-----

🔍 <ins>Research Questions</ins>

The project addresses three main research questions:

```text
1.  Is the strength of the relationship between HDB flat size and resale prices spatially clustered across Singapore’s planning areas?
	•	Statistical Method**: Global Moran's I on area-specific size–price regression coefficients

2.  Which planning areas show stronger or weaker links between flat size and resale price, compared to their neighbouring planning areas?
	•	Statistical  Method**: Local Moran's I for on area-specific size–price regression coefficients

3.  Which specific amenity features (amongst MRT, school, retail, park, and healthcare proximity) are the strongest factors in explaining variation in the marginal willingness to pay for additional floor area (beta_size_price) across Singapore’s planning areas?
	•	Statistical Method**: OLS Regression, SAR Model
```

-----

🗺️ <ins>Data Sources</ins>

Key datasets used include:

	•	`ResaleflatpricesbasedonregistrationdatefromJan2017onwards.csv` to obtain a compilation of HDB resale transactions (2017–2025)
	•	`MasterPlan2019SubzoneBoundaryNoSeaGEOJSON.geojson` to obtain Singapore planning area boundaries
	•	`HDBExistingBuilding.geojson` to obtain existing HDB locations
	•	`LTAMRTStationExitGEOJSON.geojson` to represent public transport amenities
	•	`LTASchoolZone.geojson` to represent public education amenities
	•	`Parks.geojson` to represent recreational park amenities
	•	`NEAMarketandFoodCentre.geojson` to represent markets and food centre amenities
	•	`CHASClinics.geojson` to represent healthcare amenities
  
These datasets were obtained from data.gov.sg as GeoJSON or CSV files containing geospatial geometries and coordinate information. All amenity layers were imported and transformed into the same coordinate reference system (CRS) as the planning‐area polygons in `MasterPlan2019SubzoneBoundaryNoSeaGEOJSON.geojson` to ensure spatial compatibility.

-----

🧠 <ins>Key Methods Used</ins>

	•	Neighbour definitions: Queen contiguity, k-nearest neighbours
	•	Spatial weights: Binary (B-style) and row-standardised (W-style)
	•	Spatial diagnostics: (1) Global Moran’s I and (2) Local Moran’s I (cluster maps)
	•	Regression models: (1) OLS and (2) SAR to correct residual spatial autocorrelation

These methods are discussed and justified in detail in the final report.

-----

📊 <ins>Main Findings (High-Level)</ins>

```text
	•	The flat size–price relationship is not spatially random; strong and weak gradients cluster geographically.
	•	A High–High cluster of strong size–price relationships appears in central and southern Singapore.
	•	School proximity and park proximity are the strongest predictors of variation in size–price gradients across planning areas.
	•	Accounting for spatial dependence via a SAR model improves inference validity.
```

-----

🗂️ <ins>Repository Structure</ins>

```text
ST5226_Project_HousingPrices/
│
├── Final-Group-13.pdf        # Final submitted report: complete write-up including methodology, results, maps, and interpretation  
├── Final-Group-13.Rmd        # Reproducible analysis code: full data processing, modelling, and visualisation code used to generate the report
├── beta_size_price/          # Dataset used in RQ1 & 2
├── Amenities/                # Dataset used in RQ3
└── README.md                 # Project overview (this file)
```

-----

🔁 <ins>Reproducibility Notes</ins>
The workflow is fully reproducible by knitting Final-Group-13.Rmd, assuming required datasets are available. All analyses were conducted in R using packages such as sf, spdep, spatialreg, gstat, and ggplot2. Random seeds were set where applicable (e.g., permutation tests).

⚠️ One large dataset was not tracked directly on GitHub due to size limits. This file, `HDBExistingBuilding.geojson`, can be found at https://data.gov.sg/collections/2033/view.

To reproduce the analysis:
```text
1. Download the dataset from the source above
2. Place it in the `beta_size_price` folder
3. Run the analysis script.

All other data sources can be located in this repository. Their use, and preprocessing, is also documented (to the best effort) in the Final-Group-13.Rmd file.
```
-----

🤖 <ins>AI Use Disclosure</ins>

AI tools (ChatGPT-5 and Claude) were used only for:
	•	Code troubleshooting
	•	Documentation drafting
	•	Refinement of explanations

All modelling decisions, statistical reasoning, and interpretations were independently determined by the authors, as stated in the final report.
