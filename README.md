# Analyzing Air Quality Index (AQI) Data

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Goal
The goal of this project is to analyze the Air Quality Index (AQI) data to understand the air quality trends over time and across different locations. The analysis involves cleaning, visualizing, and aggregating the AQI data to derive meaningful insights.

## Code Organization
The code for this project is organized into the following notebooks:

1. **1-getting_wildlife_data.ipynb**: This notebook retrieves and processes wildlife data, saving it to a JSON file for further analysis.
2. **3-cleaning_and_visualizaton.ipynb**: This notebook performs data cleaning and visualization of the AQI data. It includes steps to filter, aggregate, and visualize the data.

## Data Processing Steps
### 1. Data Retrieval
- **1-getting_wildlife_data.ipynb**: Retrieves wildlife data and saves it to a JSON file named `fire_distance_data.json`.

### 2. Data Cleaning and Visualization
- **3-cleaning_and_visualizaton.ipynb**: 
    - Loads the AQI data.
    - Filters out unnecessary columns and rows.
    - Aggregates the data by various attributes such as date, site number, and parameter.
    - Visualizes the AQI data over time and across different locations.

## Generated Files
Following are the intermediary files generated during the analysis:

- `fire_distance_data.json`: Contains the processed wildlife data.

Final files generated after the analysis are:

- `aqi_df_unique`: A cleaned and filtered DataFrame containing unique AQI records.

## Issues Faced / Special Considerations
- Some records in the AQI data had missing values. These records were filtered out during the cleaning process.
- Duplicate records were found in the AQI data. The first occurrence of each duplicate was retained, and the rest were removed.
- The CSV files need to be placed in the appropriate paths for the notebooks to run successfully. This has been mentioned in each notebook.

## Research Implications
The analysis of AQI data can provide insights into air quality trends and help identify areas with poor air quality. This information can be used to inform policy decisions and public health initiatives.


## Attribution
1. A lot of code used in this notebook was developed by Dr. David W. McDonald for use in DATA 512, a course in the UW MS Data Science degree program. 
2. Some code for getting the AQI data has been adapted from work by Raagul Nagendran, a student in the same program.
3. The model for ARIMAX has been adapted from the work of Navya Eedula, a student in the same program.

Appropriate attributions have been made in the code where necessary.
