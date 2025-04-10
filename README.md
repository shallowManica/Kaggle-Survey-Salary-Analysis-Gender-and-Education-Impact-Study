
This repository presents a thorough analysis of the Kaggle 2022 Survey data to investigate salary disparities among data science professionals. The analysis focuses on two major research questions:

1. **Gender-Based Salary Differences:**  
   Examining how salaries differ between men and women in the data science community.

2. **Education-Level Impact on Salary:**  
   Analyzing the association between the highest level of formal education (Bachelor’s, Master’s, and Doctoral degrees) and the resulting salary levels.

This project uses both traditional hypothesis tests (two-sample t-test and one-way ANOVA) and modern bootstrap sampling techniques to draw robust insights when the underlying data may not meet the assumptions of normality.

---

## Table of Contents

- [Project Overview](#project-overview)
- [Dataset Description](#dataset-description)
- [Methodology](#methodology)
  - [Data Exploration and Visualization](#data-exploration-and-visualization)
  - [Gender-Based Salary Analysis](#gender-based-salary-analysis)
  - [Education-Level Salary Analysis](#education-level-salary-analysis)
- [Results and Findings](#results-and-findings)
- [How to Run the Analysis](#how-to-run-the-analysis)
- [Dependencies and Setup](#dependencies-and-setup)
- [Project Structure](#project-structure)
- [License](#license)

---

## Project Overview

In this project, we use the Kaggle ML & DS Survey 2022 dataset to tell a data story about the data science community. The main objectives are to uncover trends regarding:
- The distribution of data science professionals across different age groups, countries, and education levels.
- Whether significant differences in yearly compensation exist between genders.
- How educational attainment correlates with salary outcomes.

Through a comprehensive exploratory analysis and rigorous statistical tests supported by bootstrap techniques, this work aims to provide evidence for salary disparities and highlight the potential advantages linked to higher education in the field of data science.

---

## Dataset Description

The dataset used in this analysis is a cleaned version of the Kaggle Survey 2022 responses, containing:
- **8,136 rows** (survey responses)
- **297 columns** (survey questions, including demographics, job-related details, and salary information)
- Key fields include:
  - **Age (Q2)**
  - **Country (Q4)**
  - **Education Level (Q8)**
  - **Gender (Q3)**
  - **Yearly Compensation (Q29)**

The dataset, originally sourced from Kaggle's 2022 Survey Challenge, provides rich demographic and salary data that enables a nuanced look at the data science community.

---

## Methodology

### Data Exploration and Visualization

The notebook begins with a comprehensive data exploration:
- **Data Loading:**  
  Reads the CSV file (`clean_kaggle_data.csv`) and examines basic information about the dataset (e.g., head, descriptive statistics, and data types).

- **Initial Visualization:**  
  - A scatter plot examines the relationship between age and salary.
  - A bar chart depicts the distribution of respondents by education level.
  - A boxplot compares salary distributions across different countries.

These visualizations provide an initial understanding of the data structure and key trends.

### Gender-Based Salary Analysis

1. **Data Preparation:**  
   - Filters the dataset to include only "Man" and "Woman" responses.
   - Removes rows with missing salary values and eliminates outliers by retaining only those salaries within the 1st and 99th percentiles.

2. **Statistical Testing:**  
   - **Normality Testing:**  
     Conducts the Shapiro-Wilk test on the salary distributions for both genders.
   - **Two-Sample T-Test:**  
     Tests whether the difference in mean salaries between men and women is statistically significant.
   - **Bootstrap Analysis:**  
     Performs bootstrap sampling (10,000 iterations) on both groups to generate robust sampling distributions of the mean salary. Visualizations include histograms for:
     - Bootstrapped mean salaries for each gender.
     - Differences in means and the normalized difference distribution.

3. **Inference:**  
   The analyses indicate that, although the original salary distributions were not normal, the bootstrap approach confirms statistically significant salary differences, with men earning more on average.

### Education-Level Salary Analysis

1. **Data Preparation:**  
   - Filters the dataset for respondents with Bachelor's, Master's, and Doctoral degrees.
   - Removes outliers using similar percentile thresholds as in the gender analysis.

2. **ANOVA Testing:**  
   - **One-Way ANOVA:**  
     Examines whether there are significant salary differences among the three education groups.
   - **Bootstrap Analysis for Education:**  
     Bootstraps each group’s salary data over 10,000 iterations to estimate robust distributions of mean salaries. Visualizations include:
     - Distributions of bootstrapped mean salaries by education level.
     - Comparisons of pairwise differences (Bachelor’s vs. Master’s, Bachelor’s vs. Doctoral, and Master’s vs. Doctoral).

3. **Inference:**  
   The ANOVA results, supported by bootstrap analysis, reveal that higher levels of education are significantly associated with higher salaries. Based on the non-normality of the data, non-parametric tests (e.g., Kruskal-Wallis) could offer alternative insights.

---

## Results and Findings

- **General Data Trends:**  
  There is a concentrated distribution of respondents in the 20-40 age range. The data also reveals diverse participation across countries, with India and the U.S. leading in respondent counts.

- **Gender Disparities:**  
  Statistical tests (both conventional t-tests and bootstrap-based t-tests) indicate that salary differences between genders are significant, with male respondents earning higher on average than female respondents.

- **Impact of Education:**  
  The analysis shows a clear trend where higher educational attainment correlates with increased average salary. Bootstrapped ANOVA further confirmed statistically significant differences among salary distributions for Bachelor's, Master's, and Doctoral degree holders.

The project underscores the importance of combining traditional statistical methods with bootstrapping techniques, particularly when working with non-normal data distributions.

---

## How to Run the Analysis

1. **Clone the Repository:**
   ```bash
   git clone https://github.com/yourusername/kaggle-survey-salary-analysis.git
   cd kaggle-survey-salary-analysis
   ```

2. **Place the Dataset:**
   Ensure the file `clean_kaggle_data.csv` is in the project root directory.

3. **Install Dependencies:**
   Install the required libraries using pip. A sample command is provided below:
   ```bash
   pip install pandas numpy scipy matplotlib seaborn
   ```
---

## Dependencies and Setup

The analysis is performed using Python 3.x with the following primary libraries:
- **pandas**: Data manipulation and analysis
- **numpy**: Numerical computing
- **scipy**: Statistical tests
- **matplotlib & seaborn**: Data visualization

Make sure you have these libraries installed in your Python environment.

---

## Project Structure

```
kaggle-survey-salary-analysis/
├── clean_kaggle_data.csv          # Dataset used in the analysis
├── data analysis.ipynb   # Jupyter Notebook with the analysis code
├── README.md                      # This README file
```
---

## License

This project is licensed under the [MIT License](LICENSE).

---
