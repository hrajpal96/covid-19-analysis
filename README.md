
# COVID-19 Analysis – Summary Report

This markdown summarizes a comprehensive COVID-19 data analysis based on confirmed cases, deaths, and recoveries across global regions from January 2020 to May 2021.

---

## Objective

- Identify peak daily new case counts in Germany, France, and Italy.
- Determine the country with the highest single-day surge.
- Track time-series patterns of confirmed cases in top-affected countries and China.
- Handle missing time-series values effectively.
- Calculate recovery and death rates by country/province.
- Merge datasets and assess monthly progression metrics.

---

## Question 2: Exploratory Analysis and Plotting

### Q2.1 – Dataset Structures:
- **Confirmed Cases:** 276 geographic entries, date-wise cumulative case counts.
- **Deaths and Recoveries:** Similar format; some missing values detected in columns like `4/20/20`.

### Q2.2 – Confirmed Cases Over Time for Top Countries
- Grouped by country and plotted top 10 countries by total confirmed cases.
- Used a bar chart with proper annotations and title.

### Q2.3 – Confirmed Cases Over Time for China
- Filtered for China, summed values per date, grouped by month.
- Used line plot to depict monthly confirmed case growth over 2020–2021.

---

## Question 3: Handling Missing Data

### Q3.1 – Imputation Strategy:
- Found missing values in `4/20/20` for both deaths and recoveries datasets.
- Applied `ffill().bfill()` to conservatively fill gaps.

---

## Question 4: Data Cleaning and Preparation

### Q4.1 – Province Field Cleaning:
- Replaced all NaN values in `Province/State` with `"All Provinces"` across all datasets.

---

## Question 5: Independent Dataset Analysis

### Q5.1 – Peak Daily New Cases: Germany, France, Italy
- Transposed data and calculated `.diff()` per day.
- Found highest surge dates and counts.
- Germany had the highest single-day surge.

### Q5.2 – Recovery Rate Comparison: Canada vs Australia (Dec 31, 2020)
- Computed (Recoveries / Confirmed Cases) * 100
- Australia showed a slightly higher recovery rate, indicating better management.

### Q5.3 – Death Rate Distribution Among Canadian Provinces
- Calculated death rate per province as (Deaths / Confirmed Cases) * 100
- Excluded `inf` and NaN values.
- Identified provinces with highest and lowest death rates.

---

## Question 6: Data Transformation

### Q6.1 – Convert Wide to Long Format
- Used `melt()` to reshape the deaths dataset for time-series operations.

### Q6.2 – Total Deaths by Country
- Extracted final column (`5/29/21`) and sorted descending.

### Q6.3 – Top 5 Countries by Average Daily Deaths
- Used total deaths divided by number of days to get average daily values.

### Q6.4 – Monthly Deaths in the US
- Resampled US death data to monthly.
- Used `diff()` and `resample('ME')` for new deaths.
- Plotted as bar chart for month-wise trend.

---

## Question 7: Data Merging

### Q7.1 – Combined Dataset Creation
- Melted all datasets to long format by date.
- Merged on `Country/Region`, `Date`, `Lat`, `Long`, and `Province/State`.

### Q7.2 – Monthly Aggregation
- Grouped by country and date, resampled to monthly to analyze progression.

### Q7.3 – Country-Specific Monthly Analysis
- Filtered for US, Italy, Brazil; repeated monthly aggregation.

---

## Question 8: Combined Data Analysis

### Q8.1 – Countries with Highest Death Rates in 2020
- Calculated (Deaths / Confirmed Cases) * 100
- Yemen, MS Zaandam, and Mexico showed the highest death ratios.

### Q8.2 – South Africa: Recovery vs Death Outcome
- Compared total recoveries and deaths.
- Computed Recovery-to-Death Ratio.

### Q8.3 – US Monthly Recovery Ratio
- Analyzed ratio (Recoveries / Confirmed Cases) monthly.
- Identified October 2020 as the peak recovery month.

---

📌 This analysis demonstrates detailed exploration, transformation, and visualization of COVID-19 data with insights derived through grouped aggregations, plots, and ratios.
