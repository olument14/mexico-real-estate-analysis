# Mexico Real Estate Analysis: Size vs Location

Exploratory data analysis of Mexican property listings, built with Python in a Jupyter notebook. The project asks one question:

**Are property prices in Mexico more influenced by property size or by location?**

## Dataset

- Three CSV files of Mexican property listings, cleaned and combined into one dataset
- **1,736 listings** across Mexican states, with 6 columns: `property_type`, `state`, `lat`, `lon`, `area_m2`, `price_usd`
- Source: WorldQuant University

## Tools Used

Python, pandas, NumPy, Matplotlib (pyplot), Seaborn, Jupyter Notebook

## What I Did

**1. Data cleaning and preparation**
- Loaded three separate files and removed missing values
- Converted prices stored as text (`$` signs and commas) into numbers
- Converted Mexican pesos to US dollars so all files used the same currency
- Split combined text columns into separate `lat`, `lon` and `state` columns
- Combined the three files with `pd.concat` and saved a clean master dataset

**2. Descriptive statistics and visualisation**
- Summarised price and area with `describe()`
- Histograms of price and area (both right-skewed)
- Box plots of price by property type and by state
- Scatter plots of area vs price, with and without outliers, plus regression lines using Seaborn
- Removed outliers using quantile cut-offs (1,365 of 1,736 listings kept)

**3. Correlation analysis**
- Pearson correlation between area and price, nationally and by state and property type
- Correlation matrix and heatmap

**4. Price per square metre**
- Created a `price_per_m2` column to separate the effect of location from size
- Compared median price per m² across states and property types
- Compared variation between states with variation within states

## Key Findings

- **Size matters, but only moderately.** The correlation between area and price is 0.59, so size explains roughly a third of the variation in price.
- **Size matters more for houses than apartments.** The area-price correlation is 0.72 for houses and 0.52 for apartments.
- **The size-price relationship changes by location.** For example, it is noticeably weaker in Distrito Federal (r = 0.41) than in the national data.
- **Location has a clear effect on price per m².** Distrito Federal has the highest median price per m² (about $959), well above the next most expensive states (about $700 to $715).
- **Apartments cost more per m² than houses.** The median is about $959 per m² for apartments against about $571 for houses.
- **Conclusion:** Both factors matter. Location shows the clearest effect on price per square metre, but the variance analysis shows a lot of price variation within each state, so location alone does not explain most price differences.

## Limitations

- Pesos were converted at a fixed rate of 19 MXN to 1 USD
- Some states have very few listings, so their correlations and medians are unreliable
- Correlation does not prove causation
- Outlier removal and dropping missing rows reduce the dataset

## How to Run

1. Clone this repository
2. Install the libraries: `pip install pandas numpy matplotlib seaborn jupyter`
3. Keep the three CSV files in the same folder as the notebook
4. Open the notebook: `jupyter notebook Mexico_real_estate.ipynb`

## Author

Clement Batcho | [www.linkedin.com/in/olument14]
