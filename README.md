# Analyzing Air Quality Index (AQI) Data

## Goal

The goal of this project is to study the affects of wildfire smoke on Asthma cases and deaths in Philadelphia, PA and be able to get valuable insights during the process. First, we begin with understand how the wildfire has been historically and then try to compare it with AQI values to see if there is any connection. We also try to create a smoke estimate and try to predict how much the estimate is going to be in the next 20 years. Using asthma hospitalizations and death data, we try to explain the impact of wildfire smoke on asthma.
## License

### Data Related License:

1. Wildland Fires data is provided by the USGS. The data is available under the [USGS Data Policy](https://www2.usgs.gov/datamanagement/dmpolicy.php).
2. AQI data is accessed through the EPA API. This lies in the public domain and is not subject to domestic copyright protection.
3. Asthma deaths data is available from the CDC. This data is available under the [CDC Data Policy](https://www.cdc.gov/other/privacy.html).
4. Asthma hospitalizations data is from the PHC4. This data is available under the [PHC4 Data Policy](https://www.phc4.org/data/policies.htm). A tool named [EDDIE](https://www.phaim1.health.pa.gov/EDD/WebForms/HospitalDischargeCntySt.aspx) was used to access the data.
   Notice: "These data were provided by the Pennsylvania Department of Health. The Department specifically disclaims responsibility for any analyses, interpretations or conclusions."

### Code Related License:

Code has been used from the example notebook developed by Dr. David W. McDonald for use in DATA 512, a course in the UW MS Data Science degree program. This code is provided under the Creative Commons CC-BY license.

This project is licensed under the [MIT License](LICENSE).

## Code Organization

The code for this project is organized into the following notebooks:

1. **getting_wildlife_data.ipynb**: This notebook retrieves and processes wildlife data, saving it to a JSON file for further analysis.
2. **getting_aqi_data.ipynb**: This notebook retrieves and processes AQI data, saving it to a JSON file for further analysis.
3. **cleaning_visualizaton_and_modelling.ipynb**: This notebook performs data cleaning and visualization of the AQI data. It includes steps to filter, aggregate, and visualize the data.
4. **4-cleaning_asthma_data.ipynb**: This notebook performs data cleaning and visualization of the Asthma data(both death and hospitalization). It includes steps to filter, aggregate, and visualize the data.
5. **5-modelling_and_forecasting_heath_data.ipynb**: This notebook performs modelling and forecasting of the Asthma data. It includes steps to fit SARIMAX model and forecast the hospitalizatiojns and deaths.

## Generated Files

### Input files:

1. The input file is around 2gb whihc is higher than allwed in github. The file can be downloaded from the following link: [Wildland Fires Data](https://www.sciencebase.gov/catalog/item/61aa537dd34eb622f699df81). I have used the GeoJson data.
2. **initial data files/all disease deaths 1999-2020.txt** -> This file contains the data for all respiratory disease deaths in Pennsylvania from 1999 to 2020. It is used in the 4-cleaning_asthma_data.ipynb notebook. It comes from the CDC.
3. **initial data files/Asthma_deaths_cdc.txt** -> This file contains the data for asthma deaths in Pennsylvania from 1999 to 2020. It is used in the 4-cleaning_asthma_data.ipynb notebook. It comes from the CDC.
4. **initial data files/death asthma by. age.txt** -> This file contains the data for asthma deaths in Pennsylvania by age group from 1999 to 2020. It is used in the 4-cleaning_asthma_data.ipynb notebook. It comes from the CDC.
5. **initial data files/hospitalization Discharges Asthma kids per 100,000.csv** -> This file contains the data for asthma hospitalizations in Pennsylvania from 1999 to 2020 for kids less than 18 years of age. It is used in the 4-cleaning_asthma_data.ipynb notebook. It comes from the PHC4.

### Intermediary files generated:

- `fire_distance_data.json`: Contains the processed wildlife data.

Schema:

```
{
    "values":
    [
        {
            "OBJECTID": 1,
            "USGS_Assigned_ID": 1,
            "Assigned_Fire_Type": "Wildfire",
            "Fire_Year": 1860,
            "Fire_Polygon_Tier": 1,
            "Fire_Attribute_Tiers": "1 (1)",
            "GIS_Acres": 3940.20708940724,
            "GIS_Hectares": 1594.5452365353703,
            "Source_Datasets": "Comb_National_NIFC_Interagency_Fire_Perimeter_History (1)",
            "Listed_Fire_Types": "Wildfire (1)", "Listed_Fire_Names": "Big Quilcene River (1)",
            "Listed_Fire_Codes": "No code provided (1)", "Listed_Fire_IDs": "",
            "Listed_Fire_IRWIN_IDs": "",
            "Listed_Fire_Dates": "Listed Other Fire Date(s): 2006-11-02 - NIFC DATE_CUR field (1)", "Listed_Fire_Causes": "",
            "Listed_Fire_Cause_Class": "Undetermined (1)",
            "Listed_Rx_Reported_Acres": null,
            "Listed_Map_Digitize_Methods": "Other (1)",
            "Wildfire_and_Rx_Flag": null,
            "Overlap_Within_1_or_2_Flag": null,
            "Circleness_Scale": 0.04758958417643999,
            "Circle_Flag": null,
            "Exclude_From_Summary_Rasters": "No",
            "Shape_Length": 64888.449849380544,
            "Shape_Area": 15945452.365353702,
            "shortest_dist": [2409.963449983856, [47.84027067710629, -123.02441580365677]],
            "avg_dist": 2412.263442630418
            },
            ...
    ]
}

```

Final files generated after the analysis are:

- `gaseous_aqi.json`: Contains all gaseous AQI data retrieved from API
- `particulate_aqi.json`: Contains all particulate AQI data retrieved from API

Both have same Schema:

```
[
    {
        "state_code": "42",
        "county_code": "101",
        "site_number": "0002",
        "parameter_code": "42401",
        "poc": 4,
        "latitude": 39.957513,
        "longitude": -75.1735,
        "datum": "WGS84",
        "parameter": "Sulfur dioxide",
        "sample_duration_code": "1",
        "sample_duration": "1 HOUR",
        "pollutant_standard": "SO2 1-hour 2010",
        "date_local": "1962-05-01",
        "units_of_measure": "Parts per billion",
        "event_type": "No Events",
        "observation_count": 24,
        "observation_percent": 100.0,
        "validity_indicator": "Y",
        "arithmetic_mean": 17.083333,
        "first_max_value": 30.0,
        "first_max_hour": 1,
        "aqi": 43,
        "method_code": "013",
        "method": "INSTRUMENTAL - CONDUCTIMETRIC",
        "local_site_name": null,
        "site_address": "22ND ST & PARKWAY  PHILA  PA",
        "state": "Pennsylvania", "county": "Philadelphia",
        "city": "Philadelphia",
        "cbsa_code": "37980",
        "cbsa": "Philadelphia-Camden-Wilmington, PA-NJ-DE-MD",
        "date_of_last_change": "2013-06-11"
    },
    .....
]

```

Note: The above intermediary files are not available in github due to their large size. They can be generated by running the respective notebooks.

- **training_data_model.csv**:

  - This file contains the training data used to build the predictive model. It includes various features and target variables necessary for training the model to predict asthma-related deaths.
  - **Columns**:
    - `Year`: The year of the data record.
    - `smoke_metric`: The smoke metric value for the corresponding year.
    - `Deaths per million`: The number of deaths per million people for the corresponding year.

- **test_data_model.csv**:

  - This file contains the test data used to evaluate the performance of the predictive model. It includes similar features and target variables as the training data but is used to validate the model's accuracy and generalization.
  - **Columns**:
    - `Year`: The year of the data record.
    - `smoke_metric`: The smoke metric value for the corresponding year.
    - `Deaths per million`: The number of deaths per million people for the corresponding year.

- **shifted_training_data.csv**:

  - This file contains the training data with shifted time series features. Shifting is often used in time series analysis to create lagged features that help the model understand temporal dependencies. Contains hospitalization data.
  - **Columns**:
    - `Year`: The year of the data record.
    - `smoke_metric`: The smoke metric value for the corresponding year.
    - `smoke_metric_lag1`: The smoke metric value shifted by one year.
    - `Deaths per million`: The number of deaths per million people for the corresponding year.

- **future_smoke_data.csv**:

  - This file contains future projections of smoke data, which is used to predict the impact of smoke on asthma-related health outcomes. It includes forecasted values of smoke metrics that are used as input features in the predictive model.
  - **Columns**:
    - `Year`: The year of the data record.
    - `smoke_metric`: The forecasted smoke metric value for the corresponding year.

- **asthma_kids_discharges_100000.csv**:
  - This file contains data on asthma discharges for kids under 18 years of age in Philadelphia county, normalized per 100,000 people. It is used to analyze trends and patterns in asthma-related hospitalizations among children.
  - **Columns**:
    - `Year`: The year of the data record.
    - `Count`: The number of asthma discharges.
    - `Population`: The population count for the corresponding year.
- **forecasted_smoke_impact.csv**:

  - This file contains the forecasted impact of smoke on air quality for future years.
  - **Columns**:
    - `predicted_mean`: The predicted mean smoke impact.
    - `Year`: The year of the forecast.

- **smoke_metric_historical.csv**:

  - This file contains historical smoke metric data.
  - **Columns**:
    - `Fire_Year`: The year of the fire.
    - `smoke_metric`: The smoke metric value for the corresponding year.

- **all disease deaths 1999-2020.txt**:
  - This file contains data on all respiratory disease deaths in Pennsylvania from 1999 to 2020.
  - **Columns**:
    - `Year`: The year of the data record.
    - `Deaths`: The number of deaths.
    - `Population`: The population count for the corresponding year.
    - `Deaths per 100000`: The number of deaths per 100,000 people for the corresponding year.

### Output files generated:

- 'visulization-1.png' - a histogram showing the number of fires occurring every 50 mile distance from Philedelphia for all fires ranging up to 1800 miles away from Philedelphia.
- 'visulization-2.png' - a time series graph of total acres burned per year for the fires occurring in the specified distance from Philedelphia.
- 'visulization-3.png' - a time series graph containing your fire smoke estimates Philedelphia and the AQI estimates for Philedelphia.

## Packages Used:
- pandas: A powerful data manipulation and analysis library for Python.
- numpy: A fundamental package for scientific computing with Python, providing support for arrays and matrices.
- polars: A fast DataFrame library for Rust and Python, designed for performance and ease of use.
- matplotlib.pyplot: A plotting library for creating static, animated, and interactive visualizations in Python.
- seaborn: A statistical data visualization library based on matplotlib, providing a high-level interface for drawing attractive and informative statistical graphics.
- statsmodels.tsa.statespace.varmax.VARMAX: A module for estimating vector autoregressive moving average models with exogenous regressors.
- statsmodels.tools.eval_measures.rmse: A function to calculate the root mean square error, a measure of the differences between predicted and observed values.
- warnings: A built-in Python module for issuing warning messages.
- sklearn.preprocessing.StandardScaler: A module for standardizing features by removing the mean and scaling to unit variance.
- scipy.stats.pearsonr: A function to calculate the Pearson correlation coefficient and p-value for testing non-correlation.
- scipy.stats.kendalltau: A function to calculate Kendall's tau, a measure of correlation between two variables.
- scipy.stats: A module that contains a large number of probability distributions as well as a growing library of statistical functions.
- statsmodels.tsa.statespace.sarimax.SARIMAX: A module for estimating seasonal autoregressive integrated moving average models with exogenous regressors.

## Issues Faced / Special Considerations

- Some records in the AQI data had missing values. These records were filtered out during the cleaning process.
- Duplicate records were found in the AQI data. The first occurrence of each duplicate was retained, and the rest were removed.
- The JSON files need to be placed in the appropriate paths for the notebooks to run successfully. This has been mentioned in each notebook.
- The data is quite large and may take some time to process. It is recommended to run the notebooks on a machine with sufficient memory and processing power. Colab runs quickly.
- The asthma data miight not be very accurate because of potential loss of trends while aggregating the data.

## Research Implications

The analysis of AQI data can provide insights into air quality trends and help identify areas with poor air quality. The asthma data analysis combined with the smoke estimates can help understand the impact of air quality on respiratory health outcomes. This information can be used to inform policy decisions and public health initiatives.

## Code Attribution

1. Some of the code used in this notebook was developed by Dr. David W. McDonald for use in DATA 512, a course in the UW MS Data Science degree program.
2. A method for getting the AQI data has been adapted from work by Raagul Nagendran, a student in the same program.
3. The model for ARIMAX has been adapted from the work of Navya Eedula, a student in the same program.

Appropriate attributions have been made in the code where necessary.

References and API Documentation:

1. AQS API: https://aqs.epa.gov/aqsweb/documents/data_api.html
2. USGS Wildland Fires Data: https://www.sciencebase.gov/catalog/item/61aa537dd34eb622f699df81
3. GeoJSON: https://geojson.org/
4. AQI calculation: https://www.airnow.gov/aqi/aqi-basics/
<<<<<<< HEAD
5. CDC Data: https://www.cdc.gov/nchs/nvss/mortality_public_use_data.htm
6. PHC4 Data: https://www.phc4.org/data/policies.htm
7. EDDIE: https://www.phaim1.health.pa.gov/EDD/WebForms/HospitalDischargeCntySt.aspx
=======
>>>>>>> 155cae37d30dbb3d753e9da0d09cf678cbab0df8
