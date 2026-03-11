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

| Folder/File | Description |
| :--- | :--- |
| `/data` | Contains the raw and processed CSV datasets [(here)](https://drive.google.com/file/d/1698Slt-20ZaMxzCxzrMkwlemHL2idbEb/view?usp=sharing). |
| `/notebooks` | Python scripts/Jupyter Notebooks used for the WLS regression and data cleaning [(here)](https://colab.research.google.com/drive/1vXaSN6c2rIwf4Nw-Pg-B7ypSAebugzE6?usp=sharing)). |
| `/tableau` | The `.twbx` workbook for the interactive dashboard [(here)](https://public.tableau.com/views/union_wage/UnionWageDynamicsDashboard?:language=en-US&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link). |
| `README.md` | Project summary, methodology, and findings. |

---

## Key Finding

The analysis reveals a **positive correlation between union density and wage premiums** at the state level, suggesting that collective bargaining power is most effective in regions with higher market penetration. 

However, longitudinal data shows significant variance across demographic groups. For example, while the national adjusted premium has seen a downward trend from approximately **15% in 2000** to **8% in 2022**, certain groups (such as Black and Hispanic workers) historically maintain higher relative premiums, though these too have faced compression over the last decade.

---

## Methodology: Adjusted Premium CalculationTo move beyond raw averages—which are often skewed by differences in education, age, or location—this study employs a Weighted Least Squares (WLS) regression model. This approach "levels the playing field," comparing union and non-union workers with similar demographic profiles.The ModelThe wage advantage is estimated using a semi-logarithmic equation:$$\ln(\text{Wage}) = \beta_0 + \beta_1(\text{Union\_Status}) + \sum \gamma_i(X_i) + \epsilon$$Where:$\ln(\text{Wage})$ is the natural log of hourly earnings.$\beta_1$ represents the raw union coefficient.$X_i$ represents control variables: Age, Sex, Race, Education Level, and Geographic Region.The model is weighted by the survey's final weight variable (wtfinl) to ensure national representativeness.Transforming ResultsBecause the dependent variable is logarithmic, the coefficient $\beta_1$ is transformed to a percentage to be easily interpreted on the Tableau dashboard:$$\text{Adjusted Premium \%} = (e^{\beta_1} - 1) \times 100$$

---

## Technical Challenges Overcome

* **Data Blending:** Established relationships between modeled regression results and raw state metrics to allow for a single global "Year" filter.
* **Dynamic Visualizations:** Implemented custom Dashboard Actions to balance global context and local detail, using Highlight actions to maintain 20-year trend perspectives while filtering for specific states.
