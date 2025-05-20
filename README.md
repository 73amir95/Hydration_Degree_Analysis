# Hydration Degree Analysis for Cement Pastes

## Overview
This project contains a Python script for analyzing and visualizing the hydration degree (Hydratationsgrad) of cement pastes under different temperature conditions (-20°C, 20°C, and 60°C). The script uses `pandas` for data manipulation, `seaborn` and `matplotlib` for visualization, and `numpy` for numerical operations. It generates bar plots, line plots, and summary statistics to compare hydration degrees across various conditions and temperatures, as well as calculates percentage differences for mean and standard deviation data.

## Prerequisites
To run the script, ensure you have the following Python libraries installed:
- `pandas`
- `numpy`
- `matplotlib`
- `seaborn`

You can install these dependencies using pip:
```bash
pip install pandas numpy matplotlib seaborn
```

## Usage
1. Save the Python script (e.g., `hydration_analysis.py`) in a working directory.
2. Run the script in an environment that supports Jupyter Notebook or a Python interpreter with the required libraries.
   ```bash
   python hydration_analysis.py
   ```
3. The script will generate several plots and save them as PNG files in the working directory.

## Script Description
The script performs the following tasks:
1. **Data Loading**:
   - Defines three datasets (`data_20c`, `data_60`, `data_minus_20`) as dictionaries containing hydration degree data for different conditions (REF, PCS_SA15, PCS_EVA15, PCS_SBR15) at temperatures 20°C, 60°C, and -20°C, respectively.
   - Converts the dictionaries into pandas DataFrames (`df_20`, `df_60`, `df_minus_20`).
2. **Data Exploration**:
   - Displays the first few rows of each DataFrame (`df_20.head()`, `df_60.head()`, `df_minus_20.head()`).
   - Generates summary statistics for each DataFrame (`df_20.describe()`, `df_60.describe()`, `df_minus_20.describe()`).
3. **Visualizations**:
   - Creates bar plots for hydration degrees at each temperature (20°C, 60°C, -20°C) using `seaborn.barplot`, with conditions differentiated by hue:
     - Saved as `Hydratationsgrade der PCC (20°C).png`, `Hydratationsgrade der PCC (60°C).png`, and `Hydratationsgrade der PCC (-20°C).png`.
   - Generates a line plot comparing hydration degrees across all conditions and temperatures, saved as `Hydratationsgrade der Zementleime.png`.
   - Creates an interpolated version of the line plot for `df_60` and `df_minus_20` (using `df.interpolate()` to handle missing values), saved as `Hydratationsgrade der Zementleime(interpolated).png`.
4. **Data Combination**:
   - Combines the melted DataFrames (`df_melted_minus_20`, `df_melted_20`, `df_melted_60`) into a single DataFrame (`df_combined`) for unified analysis.
   - Concatenates the original DataFrames (`df_minus_20`, `df_20`, `df_60`) into `df_combined_2`.
5. **Mean and Standard Deviation Analysis**:
   - Defines DataFrames (`df_mean` and `df_std`) containing mean and standard deviation of hydration degrees for each condition at the three temperatures.
   - Defines a function (`add_percentage_diff_columns`) to calculate percentage differences between consecutive rows for each column in `df_mean` and `df_std`.
   - Applies the function to add percentage difference columns to `df_mean` and `df_std`.

## Output Files
The script generates the following output files in the working directory:
- `Hydratationsgrade der PCC (20°C).png`: Bar plot of hydration degrees at 20°C for different conditions.
- `Hydratationsgrade der PCC (60°C).png`: Bar plot of hydration degrees at 60°C for different conditions.
- `Hydratationsgrade der PCC (-20°C).png`: Bar plot of hydration degrees at -20°C for different conditions.
- `Hydratationsgrade der Zementleime.png`: Line plot comparing hydration degrees across all conditions and temperatures.
- `Hydratationsgrade der Zementleime(interpolated).png`: Line plot with interpolated data for 60°C and -20°C datasets.

## Notes
- The script assumes the data is provided in the specified dictionary format. If using external data sources, ensure column names and structure match the provided datasets.
- The `%matplotlib inline` command is included for Jupyter Notebook compatibility. If running in a different environment, you may need to adjust the plotting backend.
- Missing values in `df_60` and `df_minus_20` are handled via interpolation for the final line plot. Ensure this is appropriate for your analysis, as interpolation may affect data interpretation.
- The percentage difference calculations in `df_mean` and `df_std` append `None` for the last row to maintain consistent DataFrame lengths.

## License
This project is unlicensed and provided as-is for research purposes.