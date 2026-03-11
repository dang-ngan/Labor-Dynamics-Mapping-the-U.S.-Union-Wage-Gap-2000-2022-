# Labor Dynamics: Mapping the U.S. Union Wage Gap (2000–2022)

This project investigates the **"Union Wage Premium"** across the United States over a 20-year period. By combining **Python** for statistical modeling and **Tableau** for interactive visualization, the study explores how union density, geography, and demographics influence the wage advantage union workers hold over their non-union counterparts.

---

## Key Features

* **Statistical Modeling (Python):** Utilized Weighted Least Squares (WLS) regression to calculate adjusted wage premiums, controlling for variables such as age, education, and sector.
* **Interactive Dashboard (Tableau):** * **Geographic Heatmap:** Visualizing state-by-state premium performance.
    * **Performance vs. Density Scatter:** Analyzing the correlation between union market share and wage leverage.
    * **Demographic Longitudinal Trends:** Tracking premium shifts by race and sex from 2000 to 2022.
* **Data Pipeline:** Developed a workflow to clean and transform raw CPS labor data into analysis-ready CSVs.

---

## Repository Structure

| File | Description |
| :--- | :--- |
| [**Analysis Notebook**](./Union_Wage_Premium_Analysis.ipynb) | Full Python workflow: Data cleaning, WLS modeling, and visualization. |
| [**Tableau Workbook**](./union_wage_tableau.twb) | The source `.twb` file for the interactive dashboard. |
| [**Interactive Dashboard**](https://public.tableau.com/views/union_wage/UnionWageDynamicsDashboard?:language=en-US&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link) | **Live Link** to the interactive visualization on Tableau Public. |
| [**Raw Data**](https://drive.google.com/file/d/1698Slt-20ZaMxzCxzrMkwlemHL2idbEb/view?usp=sharing) | Hosted on Google Drive due to GitHub file size constraints. |

---

## Key Finding

The analysis reveals a **positive correlation between union density and wage premiums** at the state level, suggesting that collective bargaining power is most effective in regions with higher market penetration. 

However, longitudinal data shows significant variance across demographic groups. For example, while the national adjusted premium has seen a downward trend from approximately **15% in 2000** to **8% in 2022**, certain groups (such as Black and Hispanic workers) historically maintain higher relative premiums, though these too have faced compression over the last decade.

---

## Methodology: Adjusted Premium Calculation

To move beyond raw averages, which are often skewed by differences in education, age, or location—this study employs a **Weighted Least Squares (WLS)** regression model. This approach "levels the playing field," comparing union and non-union workers with similar demographic profiles.

### The Model

The wage advantage is estimated using a semi-logarithmic equation:

$$\ln(\text{Wage}) = \beta_0 + \beta_1(\text{Union Status}) + \sum \gamma_i(X_i) + \epsilon$$

**Where:**

* **$\ln(\text{Wage})$**: The natural log of hourly earnings.
* **$\beta_1$**: The raw union coefficient.
* **$X_i$**: Control variables (Age, Sex, Race, Education, and Region).
* **Weighting**: The model is weighted by the survey's final weight variable (`wtfinl`).

### Transforming Results

Because the dependent variable is logarithmic, the coefficient $\beta_1$ is transformed to a percentage for the Tableau dashboard:

$$\text{Adjusted Premium} = (e^{\beta_1} - 1) \times 100$$

---

## Technical Challenges Overcome

* **Data Blending:** Established relationships between modeled regression results and raw state metrics to allow for a single global "Year" filter.
* **Dynamic Visualizations:** Implemented custom Dashboard Actions to balance global context and local detail, using Highlight actions to maintain 20-year trend perspectives while filtering for specific states.

---

## Installation & Setup

To run the analysis notebook locally, ensure you have Python 3.x installed along with the following libraries:

```bash
pip install pandas numpy matplotlib seaborn statsmodels
