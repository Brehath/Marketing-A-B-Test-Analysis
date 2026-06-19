# Marketing-A-B-Test-Analysis
A/B testing analysis of marketing campaigns using hypothesis testing, effect size estimation, bootstrap validation, and exploratory segmentation in Python.
## Project Overview



This project analyzes the effectiveness of two marketing campaigns—**Ads** and **Public Service Announcements (PSA)**—using A/B testing techniques. The objective is to determine whether the advertisement campaign generated a statistically significant improvement in conversion performance and to identify potential behavioral patterns across different time segments.



The analysis goes beyond descriptive statistics by incorporating hypothesis testing, confidence intervals, effect size estimation, bootstrap validation, and exploratory segmentation analyses to derive actionable business insights.



---



## Business Problem



A company tested two campaign variants:



* **Treatment Group:** Users exposed to advertisements (`ad`)

* **Control Group:** Users exposed to public service announcements (`psa`)



The key question was:



> Did the advertisement campaign significantly improve conversion rates compared to the PSA campaign, and what insights can be derived for future campaign optimization?



---



## Dataset



The dataset contains user-level experimental data, including:



* Test group assignment (`ad` or `psa`)

* Conversion outcome

* Hour of exposure

* Day of exposure



**Dataset:** `marketing_AB.csv`



---



## Objectives



* Compare conversion rates between Ads and PSA groups.

* Determine statistical significance of the observed uplift.

* Estimate practical significance using effect size measures.

* Validate findings using bootstrap resampling.

* Explore behavioral patterns by hour and day.

* Generate business recommendations based on experimental evidence.



---



## Methodology



### 1. Data Preparation



* Data loading and quality checks

* Missing value analysis

* Duplicate checks

* Exploratory data analysis (EDA)



### 2. Conversion Rate Analysis



* Conversion rates by experiment group

* Absolute and relative uplift calculations



### 3. Statistical Testing



* Two-Proportion Z-Test

* Confidence Intervals

* P-value interpretation



### 4. Practical Significance



* Cohen's h Effect Size

* Business interpretation of uplift magnitude



### 5. Validation



* Bootstrap resampling to assess robustness of conversion differences



### 6. Exploratory Segmentation



* Conversion patterns by:



  * Hour of exposure

  * Day of exposure

  * Experiment groups within time segments



---



## Tools & Libraries



* Python

* Pandas

* NumPy

* Matplotlib

* Seaborn

* SciPy

* Statsmodels



---



## Key Findings



### Experiment Performance



* The ad group achieved a **2.55% conversion rate** vs **1.79%** for the PSA group — a **42.5% relative uplift** (absolute lift: 0.76pp).

* Two-Proportion Z-Test: **Z = 7.37, p < 0.001** — the difference is highly statistically significant.

* Bootstrap validation (10,000 resamples) confirmed the result independently: **95% CI of 0.59pp–0.94pp**, entirely above zero, with 0% of resamples showing a difference ≤ 0..



### Business Interpretation



* Despite the strong statistical significance (p < 0.001), the per-user effect

  size was small (Cohen's h = 0.053), well below conventional thresholds for

  even a "small" effect. This highlights a common phenomenon in large-sample

  experiments: statistical significance is relatively easy to achieve, whereas

  practical significance must be evaluated separately.

* Although the per-user uplift is modest, an experiment involving nearly

  588k users means that even small improvements can translate into a

  meaningful number of incremental conversions at scale. However, determining

  whether the observed uplift justifies broader implementation would require

  additional information on campaign costs, customer lifetime value (CLV), and

  return on investment (ROI), which are not available in this dataset.



### Behavioural Insights



* Conversion rates varied by day and hour of exposure, with Monday–Tuesday afternoons (14:00–17:00) showing the strongest performance and Thursday showing negligible incremental lift.

* These patterns may help inform future campaign scheduling and targeting strategies.



---



## Caveats & Limitations



1. **Group imbalance (96:4):** The dataset shows 564,577 ad-group users vs 23,524 PSA-group users. The dataset does not document an intended allocation ratio, so a formal Sample Ratio Mismatch (SRM) test against a known baseline was not possible. The imbalance was treated as a potential threat to randomization integrity and addressed through stratified bootstrap resampling rather than relying on the Z-test alone.



2. **Exploratory segmentation:** Subgroup analyses by hour and day were conducted *after* the main experiment (post-hoc), not pre-specified. These patterns are useful for generating hypotheses but are susceptible to multiple-comparison effects — testing many time segments increases the chance of finding a "significant" pattern by chance alone. These findings should be validated through a dedicated follow-up experiment before being used to inform budget or scheduling decisions.



3. **No cost or revenue data:** The dataset includes conversion outcomes only. Any recommendation to scale or reallocate ad spend would need to be evaluated against campaign cost and revenue-per-conversion data not available here.



---



## Repository Structure



```text

Marketing-AB-Test-Analysis/

│

├── AB_Test_Analysis.ipynb

├── marketing_AB.csv

├── README.md/



```



---



## Future Improvements



* Conduct experiments with more balanced group allocations.

* Incorporate additional customer attributes for deeper segmentation.

* Perform follow-up experiments to validate subgroup findings.

* Evaluate campaign performance from a cost-benefit and ROI perspective.



---



## Author



**Brehath Subramaniam**



MSc Business Analytics | Data Analytics & Business Intelligence Enthusiast
