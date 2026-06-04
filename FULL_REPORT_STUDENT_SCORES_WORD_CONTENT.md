A STATISTICAL ANALYSIS OF STUDENT SCORES:
GENDER AND PARENTAL EDUCATION EFFECTS

BY
[YOUR FULL NAME]
Applicant for the Master’s Program in Data Science
June 03, 2026


(Title Page ends here — insert a Page Break)
----------------------------------------------------------------

TABLE OF CONTENTS
(Insert automatic TOC here in Word: References → Table of Contents)

(Insert a Page Break)
----------------------------------------------------------------

LIST OF FIGURES
(After adding captions in Word, insert automatically: References → Insert Table of Figures)

Figure 1: Boxplots of Mathematics and Language Scores by Gender and Parental Education .......... [auto]

(Insert a Page Break)
----------------------------------------------------------------

LIST OF TABLES
(After adding captions to tables, insert automatically: References → Insert Table of Figures → label “Table”)

Table 1: Dataset Description ........................................................................................................... [auto]
Table 2: Overall Descriptive Statistics ............................................................................................ [auto]
Table 3: Descriptive Statistics by Gender ....................................................................................... [auto]
Table 4: Descriptive Statistics by Parental Education ................................................................... [auto]
Table 5: Assumption Checks (Shapiro–Wilk, Levene) ..................................................................... [auto]
Table 6: Hypothesis Test Results (Gender & Parental Education) ................................................ [auto]
Table 7: Post-hoc Comparisons (Mathematics by Parental Education) ......................................... [auto]
Table 8: Post-hoc Comparisons (Language by Parental Education) ............................................. [auto]

(Insert a Page Break)
----------------------------------------------------------------


1. INTRODUCTION
Educational assessment data are widely used to understand achievement gaps, evaluate interventions, and inform educational policy. Two factors frequently discussed in educational research are (i) gender differences in academic performance and (ii) the socioeconomic and cultural resources associated with family background. In many contexts, parental education is used as a proxy for such background characteristics and is often associated with students’ access to learning opportunities.

This analysis investigates student test performance in two subjects—Mathematics and Language—and evaluates whether scores differ systematically by gender and by parental education level. The analysis combines descriptive statistics, graphical exploration, and inferential hypothesis tests to answer the research questions.

Main results (preview):
1) Mathematics scores differ significantly by gender: males score higher on average (Welch t-test, p = 0.0002; small effect).
2) Language scores differ significantly by gender: females score higher on average (Welch t-test, p < 0.0001; medium effect).
3) Both Mathematics and Language scores differ significantly across parental education levels (one-way ANOVA, p = 0.0004 and p < 0.0001, respectively), with higher parental education associated with higher mean scores.

At the end of this report, implications and limitations are discussed, emphasizing that statistical significance does not necessarily imply large practical importance, which is why effect sizes are reported.


2. DETAILED DESCRIPTION OF THE PROBLEM AND DATA

2.1 Research Questions
This report addresses the following questions:

(1) Gender differences
- Is there a statistically significant difference in Mathematics scores between female and male students?
- Is there a statistically significant difference in Language scores between female and male students?

(2) Parental education differences
- Is there a statistically significant difference in Mathematics scores across parental education levels?
- Is there a statistically significant difference in Language scores across parental education levels?
- If differences exist, which parental education groups differ from each other?

2.2 Dataset Description
The dataset contains performance data for N = 486 students with variables for Mathematics score, Language score, Gender, and ParentalEducation.

Table 1. Dataset Description

| Variable            | Type        | Scale              | Description                                                   |
|---------------------|-------------|-------------------|---------------------------------------------------------------|
| Mathematics         | Numeric     | Interval/Scale     | Mathematics score (0–100)                                     |
| Language            | Numeric     | Interval/Scale     | Language score (0–100)                                        |
| Gender              | Categorical | Nominal            | female / male                                                 |
| ParentalEducation   | Categorical | Ordinal            | High School < Associate’s < Bachelor’s < Master’s              |

Data quality summary (as provided):
- Missing values: 0
- Out-of-range values (scores outside 0–100): 0
- Duplicates: 0
- Score ranges: Mathematics 19.5–100.0; Language 20.0–100.0

Group sizes:
- Gender: Female 245 (50.4%), Male 241 (49.6%)
- Parental education:
  High School 156 (32.1%),
  Associate’s Degree 177 (36.4%),
  Bachelor’s Degree 94 (19.3%),
  Master’s Degree 59 (12.1%)


3. METHODOLOGY

3.1 Descriptive Statistics
Let X = (x1, …, xn) be a sample of size n. The sample mean and sample standard deviation are defined as

x̄ = (1/n) * Σ_{i=1..n} xi,
s = sqrt( (1/(n-1)) * Σ_{i=1..n} (xi - x̄)^2 ).

In addition to mean and standard deviation, median and interquartile range (IQR) are used to describe central tendency and dispersion robustly, especially when distributions may deviate from normality or contain outliers.

3.2 Visualization (Boxplots)
Boxplots summarize distributions using the median, quartiles, and potential outliers. They are used here to compare score distributions across gender and parental education levels and to provide an intuitive view of group differences before formal inference.

3.3 Assumption Checks
3.3.1 Normality: Shapiro–Wilk Test
The Shapiro–Wilk test evaluates:
H0: The sample is drawn from a normally distributed population.
H1: The sample is not drawn from a normally distributed population.

The test is sensitive in large samples; therefore statistical results are interpreted in combination with practical considerations.

3.3.2 Homogeneity of variances: Levene’s Test
Levene’s test evaluates:
H0: The variances are equal across groups.
H1: At least one group variance differs.

3.3.3 Independence
Independence cannot be tested directly from the dataset. It is assumed based on the data generation process: each student is a separate observational unit.

3.4 Hypothesis Tests
3.4.1 Gender comparisons: Welch Two-Sample t-test
For each outcome Y ∈ {Mathematics, Language}, the Welch t-test compares two independent means. Hypotheses:

H0: μ_female = μ_male
H1: μ_female ≠ μ_male

Welch’s t-test is robust to unequal variances and is generally preferred to Student’s t-test when variances may differ.

3.4.2 Parental education comparisons: One-way ANOVA
For parental education with k = 4 groups, one-way ANOVA evaluates whether at least one group mean differs:

H0: μ1 = μ2 = … = μk
H1: At least one μj differs

3.5 Effect Sizes
- For gender comparisons, Cohen’s d summarizes the standardized mean difference:
  d = (x̄1 - x̄2) / s_pooled (with a pooled/appropriate standardizer).
- For ANOVA, η² (eta-squared) measures the proportion of variance explained by the factor:
  η² = SS_between / SS_total.

3.6 Post-hoc Comparisons and Multiple Testing
If an overall ANOVA is significant, pairwise comparisons are conducted. To control the familywise error rate, Bonferroni correction is applied:

α* = α / m,

where m is the number of pairwise comparisons (here m = 6).


4. RESULTS

4.1 Descriptive Statistics

Table 2. Overall Descriptive Statistics (N = 486)

| Metric     | Mathematics | Language |
|-----------|------------:|---------:|
| Mean      | 65.70       | 69.38    |
| Std. Dev. | 17.55       | 16.31    |
| Median    | 66.00       | 71.00    |
| Min       | 19.50       | 20.00    |
| Max       | 100.00      | 100.00   |

Table 3. Descriptive Statistics by Gender

| Gender | n   | Mathematics Mean (SD) | Language Mean (SD) |
|--------|-----|------------------------|--------------------|
| Female | 245 | 63.86 (17.87)          | 73.00 (15.16)      |
| Male   | 241 | 68.95 (16.71)          | 64.93 (16.83)      |

Table 4. Descriptive Statistics by Parental Education

| Parental Education  | n   | Mathematics Mean (SD) | Language Mean (SD) |
|---------------------|-----|------------------------|--------------------|
| High School         | 156 | 62.24 (18.42)          | 63.53 (17.42)      |
| Associate’s Degree  | 177 | 67.81 (16.98)          | 70.02 (15.41)      |
| Bachelor’s Degree   | 94  | 68.44 (16.91)          | 72.06 (14.74)      |
| Master’s Degree     | 59  | 69.75 (16.22)          | 75.53 (14.94)      |

Key descriptive patterns:
- Gender: males show higher Mathematics means, while females show higher Language means.
- Parental education: both subjects show higher means with higher parental education, with a stronger gradient in Language.

4.2 Visualization

[INSERT IMAGE HERE: scores_boxplots.png or the provided boxplot figure]

Figure 1. Boxplots of Mathematics and Language Scores by Gender and Parental Education.
(Insert the provided image and add this caption in Word via References → Insert Caption.)

4.3 Assumption Checks

Table 5. Assumption Checks (Shapiro–Wilk, Levene)

A) Shapiro–Wilk normality tests (within groups)

| Outcome      | Grouping   | Group               | p-value | Interpretation         |
|-------------|------------|---------------------|--------:|------------------------|
| Mathematics | Gender     | Female              | 0.5010  | Normal                 |
| Mathematics | Gender     | Male                | 0.0505  | Borderline             |
| Language    | Gender     | Female              | 0.0853  | Approximately normal   |
| Language    | Gender     | Male                | 0.1390  | Normal                 |
| Mathematics | ParentEdu  | High School         | 0.3692  | Normal                 |
| Mathematics | ParentEdu  | Associate’s Degree  | 0.0490  | Borderline             |
| Mathematics | ParentEdu  | Bachelor’s Degree   | 0.6086  | Normal                 |
| Mathematics | ParentEdu  | Master’s Degree     | 0.0317  | Borderline             |
| Language    | ParentEdu  | High School         | 0.2232  | Normal                 |
| Language    | ParentEdu  | Associate’s Degree  | 0.1202  | Normal                 |
| Language    | ParentEdu  | Bachelor’s Degree   | 0.4078  | Normal                 |
| Language    | ParentEdu  | Master’s Degree     | 0.5121  | Normal                 |

B) Levene’s tests (homogeneity of variances)

| Comparison                   | F       | p-value | Conclusion        |
|-----------------------------|--------:|--------:|------------------|
| Mathematics by Gender       | 0.0060  | 0.9382  | Variances equal  |
| Language by Gender          | 0.1596  | 0.6897  | Variances equal  |
| Mathematics by Education    | 1.2748  | 0.2824  | Variances equal  |
| Language by Education       | 0.1693  | 0.9171  | Variances equal  |

Conclusion: Homogeneity of variances is supported and normality is mostly acceptable given the sample sizes. Thus, parametric tests are used.

4.4 Hypothesis Tests

Table 6. Hypothesis Test Results (α = 0.05, two-sided)

| Research Question          | Outcome      | Test                 | Statistic         | df | p-value   | Effect size                 |
|---------------------------|--------------|----------------------|------------------:|---:|----------:|-----------------------------|
| Gender difference         | Mathematics  | Welch t-test         | t = -3.7782       | —  | 0.0002    | Cohen’s d = -0.3426 (small) |
| Gender difference         | Language     | Welch t-test         | t = 6.4096        | —  | <0.0001   | Cohen’s d = 0.5814 (medium) |
| ParentEdu difference      | Mathematics  | One-way ANOVA        | F = 6.2229        | —  | 0.0004    | η² = 0.0373 (small)         |
| ParentEdu difference      | Language     | One-way ANOVA        | F = 14.2406       | —  | <0.0001   | η² = 0.0814 (small-medium)  |

Interpretation (gender):
- Mathematics: males score higher by about 5.09 points on average; the effect is small but statistically significant.
- Language: females score higher by about 8.07 points on average; the effect is medium and statistically significant.

Interpretation (parental education):
- Mathematics: significant differences exist across parental education levels, though the explained variance is small.
- Language: significant differences exist with a clearer education gradient and a larger (small-to-medium) effect size.

4.5 Post-hoc Comparisons (Parental Education)
Bonferroni-adjusted threshold: α* = 0.05 / 6 ≈ 0.0083.

Table 7. Post-hoc Comparisons (Mathematics by Parental Education, Bonferroni)

| Group 1             | Group 2            | Mean Diff (G1−G2) | p-value | Significant (α*=0.0083) |
|--------------------|--------------------|------------------:|--------:|--------------------------|
| Associate’s Degree | Bachelor’s Degree  | -0.62             | 0.7481  | No                       |
| Associate’s Degree | High School        | 5.57              | 0.0006  | Yes                      |
| Associate’s Degree | Master’s Degree    | -1.93             | 0.3993  | No                       |
| Bachelor’s Degree  | High School        | 6.19              | 0.0012  | Yes                      |
| Bachelor’s Degree  | Master’s Degree    | -1.31             | 0.6021  | No                       |
| High School        | Master’s Degree    | -7.50             | 0.0007  | Yes                      |

Table 8. Post-hoc Comparisons (Language by Parental Education, Bonferroni)

| Group 1             | Group 2            | Mean Diff (G1−G2) | p-value | Significant (α*=0.0083) |
|--------------------|--------------------|------------------:|--------:|--------------------------|
| Associate’s Degree | Bachelor’s Degree  | -2.04             | 0.2634  | No                       |
| Associate’s Degree | High School        | 6.49              | 0.0000  | Yes                      |
| Associate’s Degree | Master’s Degree    | -5.50             | 0.0098  | No                       |
| Bachelor’s Degree  | High School        | 8.53              | 0.0000  | Yes                      |
| Bachelor’s Degree  | Master’s Degree    | -3.47             | 0.1380  | No                       |
| High School        | Master’s Degree    | -11.99            | 0.0000  | Yes                      |

Post-hoc summary:
- For both Mathematics and Language, students in the High School parental education group score significantly lower than students whose parents have Associate’s, Bachelor’s, or Master’s degrees.
- Differences among Associate’s vs Bachelor’s vs Master’s are generally not significant after Bonferroni correction.


5. CONCLUSION
This analysis examined whether Mathematics and Language scores differ by gender and parental education. Statistically significant differences were found in all four comparisons.

Gender differences were complementary across subjects: males scored higher in Mathematics, whereas females scored higher in Language. The Mathematics gender difference was small in standardized terms, while the Language gender difference was medium.

Parental education was significantly associated with both outcomes, and the pattern suggests that higher parental education levels correspond to higher mean scores. The effect was stronger for Language than for Mathematics, which is consistent with a clearer gradient in the descriptive statistics and a larger η² value.

These results support the interpretation that both gender and parental education are relevant correlates of student performance in this dataset. However, causality cannot be inferred from this observational analysis, and additional covariates (e.g., school context, socioeconomic variables beyond parental education) could further explain these differences.


REFERENCES
1. Agresti, A. (2018). Statistical Methods for the Social Sciences (5th ed.). Pearson.
2. Benjamini, Y., & Hochberg, Y. (1995). Controlling the false discovery rate: A practical and powerful approach to multiple testing. Journal of the Royal Statistical Society: Series B (Methodological), 57(1), 289–300.
3. Cohen, J. (1988). Statistical Power Analysis for the Behavioral Sciences (2nd ed.). Lawrence Erlbaum Associates.
4. Dunn, O. J. (1964). Multiple comparisons using rank sums. Technometrics, 6(3), 241–252.
5. Field, A., Miles, J., & Field, Z. (2012). Discovering Statistics Using R. SAGE Publications.
6. Fisher, R. A. (1925). Statistical Methods for Research Workers. Oliver & Boyd.
7. Games, P. A., & Howell, J. F. (1976). Pairwise multiple comparison procedures with unequal n’s and/or variances. Journal of Educational Statistics, 1(2), 113–125.
8. Hedges, L. V. (1981). Distribution theory for Glass’s estimator of effect size and related estimators. Journal of Educational Statistics, 6(2), 107–128.
9. Holm, S. (1979). A simple sequentially rejective multiple test procedure. Scandinavian Journal of Statistics, 6(2), 65–70.
10. Howell, D. C. (2012). Statistical Methods for Psychology (8th ed.). Cengage Learning.
11. Kruskal, W. H., & Wallis, W. A. (1952). Use of ranks in one-criterion variance analysis. Journal of the American Statistical Association, 47(260), 583–621.
12. Levene, H. (1960). Robust tests for equality of variances. In I. Olkin (Ed.), Contributions to Probability and Statistics: Essays in Honor of Harold Hotelling (pp. 278–292). Stanford University Press.
13. Mann, H. B., & Whitney, D. R. (1947). On a test of whether one of two random variables is stochastically larger than the other. The Annals of Mathematical Statistics, 18(1), 50–60.
14. Ruxton, G. D. (2006). The unequal variance t-test is an underused alternative to Student’s t-test and the Mann–Whitney U test. Behavioral Ecology, 17(4), 688–690.
15. Shapiro, S. S., & Wilk, M. B. (1965). An analysis of variance test for normality (complete samples). Biometrika, 52(3–4), 591–611.
16. Welch, B. L. (1947). The generalization of “Student’s” problem when several different population variances are involved. Biometrika, 34(1–2), 28–35.

APPENDIX (Optional)
- Code, extended tables, or additional plots can be included here if required.