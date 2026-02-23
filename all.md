### **1\. Statistical Foundations and Data Concepts**

**1.1 Populations, Samples, and Parameters**

* **1.1.1 Population vs sample**  
  A population is the entire group you want to study, and a sample is a smaller part taken from that group to analyze.  
* **1.1.2 Parameters vs statistics**  
  A parameter is a numerical value that describes a population, while a statistic is a numerical value calculated from a sample.  
* **1.1.3 Sampling variability and randomness**  
  Sampling variability is the natural difference between sample results, and randomness means samples are selected in an unpredictable way.

**1.2 Data Types and Structure**

* **1.2.1 Categorical vs numerical data**

	Categorical data represents groups or labels, while numerical data represents measurable numbers.

* **1.2.2 Discrete vs continuous variables**  
  **Discrete variables** are countable whole numbers (e.g., number of students), while **continuous** **variables** are measurements that can take decimals (e.g., height or temperature).  
* **1.2.3 Measurement scales and implications**  
  Measurement scales show how data is measured and include nominal, ordinal, interval, and ratio scales.  
  • Nominal: eye colour, gender  
  • Ordinal: class rank, satisfaction level  
  • Interval: temperature in °C  
  • Ratio: weight, height, age

**1.3 R Foundations**

* **1.3.1** Data creation and sampling using sample()

| \# 1.3 R Foundations\# \-------------------------------------------\# Create data using a vector\# \-------------------------------------------\# c() is used to combine numbers into a vector (basic data structure in R)x \<- c(5, 10, 15, 20)\# \-------------------------------------------\# Generate random sample data\# \-------------------------------------------\# sample() is used to pick random values.\# Here we pick 10 numbers from 1 to 100\.\# replace \= TRUE means numbers can repeat.sample\_data \<- sample(1:100, size \= 10, replace \= TRUE)\# \-------------------------------------------\# Basic summary statistics\# \-------------------------------------------\# summary() gives minimum, median, mean, and maximum values.summary(x)\# \-------------------------------------------\# Simple histogram plot\# \-------------------------------------------\# hist() is used to visualize distribution of numeric data.hist(sample\_data)\# R foundations cover:\# \- Vector data creation\# \- Random sampling\# \- Basic statistical summary\# \- Simple data visualization |
| :---- |

|  |
| :---- |


* **1.3.2** Basic summaries using summary()

| \# 1.3.2 Basic summaries using summary()\# \-------------------------------------------\# summary() function\# \-------------------------------------------\# summary() is used to quickly describe numeric data.\# It gives:\# \- Minimum value\# \- First quartile (25%)\# \- Median (50%)\# \- Mean (average)\# \- Third quartile (75%)\# \- Maximum value\# Example data vectordata \<- c(12, 15, 20, 25, 30, 35, 40)\# Display basic statistical summary of the datasummary(data)\# summary() helps in initial data exploration\# and understanding data distribution. |
| :---- |


  


  


  


  


  


  


  


  


  

* **1.3.3** Initial exploratory plots

| \# 1.3.3 Initial exploratory plots\# \-------------------------------------------\# Exploratory plots are used to understand data visually\# before doing detailed statistical analysis.\# Example numeric datasetdata \<- sample(1:100, size \= 50, replace \= TRUE)\# \-------------------------------------------\# Histogram\# \-------------------------------------------\# Histogram shows how data values are distributed.hist(data)\# \-------------------------------------------\# Boxplot\# \-------------------------------------------\# Boxplot helps detect median, spread, and outliers.boxplot(data)\# Exploratory plots help check:\# \- Data distribution shape\# \- Central tendency\# \- Possible unusual values |
| :---- |


---

### **2\. Descriptive Statistics and Variability**

**2.1 Measures of Location**

* **2.1.1** Mean : **Mean** is the average value of data.  
* **2.1.2** Median : **Median** is the middle value when data is ordered.  
* **2.1.3** Mode : **Mode** is the most frequently occurring value in data.

**2.2 Measures of Spread**

* **2.2.1** Variance   
  **Variance** shows how much the numbers are spread out from the average value.  
* **2.2.2** Standard deviation  
  **Standard deviation** tells the typical distance of data values from the mean.  
* **2.2.3** Sample vs population dispersion   
  **Sample vs population dispersion** means measuring data spread in a small group (sample) or in the whole group (population).

**2.3 Mathematical Structure**

* **2.3.1** Variance as an expectation  
  **Variance as an expectation** means it is just a way to measure how much the data naturally tends to vary around the average.  
* **2.3.2** Degrees of freedom and bias  
  **Degrees of freedom and bias** means we adjust calculations when using sample data so the result represents reality more fairly.

**2.4 R Implementation**

* **2.4.1** mean(), median(), sd(), var()

| \# \-------------------------------------------\# mean(), median(), sd(), var() functions\# \-------------------------------------------\# Example datasetdata \<- c(10, 20, 30, 40, 100)  \# 100 is an outlier\# Mean (average value)mean(data)\# Median (middle value after sorting)median(data)\# Standard deviation (spread of data)sd(data)\# Variance (square of standard deviation)var(data)\# These built-in functions help quickly compute\# basic statistical measures in R. |
| :---- |


* **2.4.2** Implementing estimators from definitions

| \# \-------------------------------------------\# Implementing estimators from definitions\# \-------------------------------------------\# Example datasetdata \<- c(10, 20, 30, 40, 100)\# Number of observationsn \<- length(data)\# Sample mean from definition (sum of values divided by count)mean\_manual \<- sum(data) / n\# Sample variance from definition\# Step 1: Find squared difference from meanvariance\_manual \<- sum((data \- mean\_manual)^2) / (n \- 1)\# Display resultsmean\_manualvariance\_manual\# This shows how statistical estimators are built\# from mathematical definitions. |
| :---- |


* **2.4.3** Robustness and outlier analysis

| \# \-------------------------------------------\# Robustness and outlier analysis\# \-------------------------------------------\# Example dataset with an outlierdata \<- c(10, 20, 30, 40, 100)\# Mean is sensitive to outliersmean(data)\# Median is more robust (less affected by outliers)median(data)\# Compare mean and median to check outlier influence\# Boxplot is used to visually detect outliersboxplot(data)\# Robust statistics are useful when data contains extreme values. |
| :---- |


---

### 

### **3\. Probability Theory and Bayesian Foundations**

**3.1 Probability Axioms and Set Operations**

* **3.1.1** Probability axioms  
  **Probability axioms** are the basic rules that define how probability works. Like Probability is always between 0 to 1\.  
* **3.1.2** Unions, intersections, complements  
  **Union** means the probability of either of two events happening.  
  **Intersection** means the probability of both events happening together.  
  **Complement** means the probability of an event not happening.

**3.2 Conditional Probability**

* **3.2.1** Conditional probability definition  
  **Conditional probability** means finding the probability of an event given that another event has already happened.  
* **3.2.2** Law of total probability  
  It means if a problem has several possible paths, you add the probability of each path to get the total probability.   
  Example: If a student can pass an exam by passing either the theory part or the practical part, you add the probability of passing each part to get the total pass probability.

**3.3 Bayes Theorem**  
Bayes theorem is a method to update probability when new information is added.

* **3.3.1** Bayesian updating logic  
  **Bayesian updating logic** means improving probability estimates as more evidence becomes available.  
* **3.3.2** Interpretation of posterior probabilities  
  **Posterior probability** is the updated probability after considering new data or information.

**3.4 R-Based Simulation**

* **3.4.1** Monte Carlo probability experiments

| \# \-------------------------------------------\# Monte Carlo probability experiments\# \-------------------------------------------\# Monte Carlo simulation is used to estimate probability using random experiments.\# Example: Estimate probability of getting number \> 50 from random sampling\# Set number of simulationsn \<- 10000\# Generate random numbers between 1 and 100sim\_data \<- sample(1:100, size \= n, replace \= TRUE)\# Estimate probability that number is greater than 50prob\_estimate \<- mean(sim\_data \> 50)prob\_estimate\# \-------------------------------------------\# Monte Carlo simulation helps approximate probability\# when theoretical calculation is difficult. |
| :---- |


* **3.4.2** Empirical validation of Bayes Theorem

| \# \-------------------------------------------\# 3.4.2 Empirical validation of Bayes Theorem\# \-------------------------------------------\# Goal: Understand conditional probability using simulation.\# We will NOT directly use the formula first.\# We will create data and calculate probabilities step by step.\# \------------------------------------------------------------\# Step 1: Create many random numbers (this is our "experiment")\# \------------------------------------------------------------set.seed(123)  \# set.seed() makes results reproducible\# If someone else runs this code, they get the same random numbersdata \<- sample(1:100, size \= 10000, replace \= TRUE)\# We randomly generate 10,000 numbers between 1 and 100\# replace \= TRUE means numbers can repeat\# Think of this as running 10,000 experiments\# \------------------------------------------------------------\# Step 2: Define two events\# \------------------------------------------------------------A \<- data \> 50\# Event A: number is greater than 50\# This creates TRUE or FALSE for each valueB \<- data %% 2 \== 0\# Event B: number is even\# %% means remainder after division by 2\# If remainder is 0 → number is even\# \------------------------------------------------------------\# Step 3: Calculate basic probabilities\# \------------------------------------------------------------P\_A \<- mean(A)\# mean(TRUE/FALSE) works because:\# TRUE \= 1, FALSE \= 0\# So mean(A) gives proportion of TRUE values\# This is probability of AP\_B \<- mean(B)\# Probability that number is evenP\_A\_and\_B \<- mean(A & B)\# A & B means BOTH A and B happen\# So this gives probability of intersection\# \------------------------------------------------------------\# Step 4: Calculate conditional probability\# \------------------------------------------------------------P\_A\_given\_B\_empirical \<- P\_A\_and\_B / P\_B\# This follows definition:\# P(A | B) \= P(A and B) / P(B)P\_A\_given\_B\_empirical\# \------------------------------------------------------------\# What we did conceptually:\# 1\. Simulated many experiments\# 2\. Counted how often events happened\# 3\. Used proportions to estimate probability\# 4\. Verified conditional probability using data\#\# This is called empirical validation,\# because we check theory using simulation. |
| :---- |


---

### **4\. Random Variables and Probability Distributions**

**4.1 Random Variables**  
A random variable is a number that represents the outcome of a random experiment.

* **4.1.1** Discrete vs continuous random variables  
  **Discrete random variable** takes countable values like 0, 1, 2\.  
  **Continuous random variables** can take any value in a range like height or time.  
* **4.1.2** Probability mass and density functions

PMF (Probability Mass Function) is used for discrete data and gives the exact probability of each possible value, like probability of getting 1, 2, or 3 students.

![][image1]

**PDF (Probability Density Function)** is used for continuous data and shows probability as a curve, where probability is found by measuring the area under the curve within a range.

![][image2]

**4.2 Discrete Distributions**

* **4.2.1 Binomial distribution**  
  **Binomial distribution** models the probability of a fixed number of successes in repeated yes/no experiments. like counting how many students pass in 10 exams.  
* **4.2.2 Poisson distribution**  
  **Poisson distribution** models probability of rare events happening in a fixed time or space, like the number of calls received in an hour.  
* **4.2.3 Poisson approximation to Binomial**  
  Poisson approximation to Binomial means using Poisson distribution to estimate binomial probability when there are many trials but success chance is very small, such as estimating few defective products in mass production.

**4.3 Continuous Distributions**

* **4.3.1** Uniform distribution  
  **Uniform distribution** means all values in a given range have equal probability of occurring. Such as rolling a fair die, random time picking within an interval.  
* **4.3.2** Normal distribution  
  **Normal distribution** is a bell-shaped curve where most values are near the mean and fewer values are far away. Such as exam scores, IQ scores, and body measurements like height.


**4.4 Limit Theorems**

* **4.4.1 Central Limit Theorem**  
  **Central Limit Theorem means sample means tend to follow a normal distribution when sample size is large.**  
* **4.4.2 Implications for inference**  
  **Implications for inference mean we can use sample data to estimate population characteristics.**

**4.5 R Coverage**

* **4.5.1 dbinom(), rbinom()**

| \# 4.5.1 dbinom() and rbinom()\# \----------------------------------------------------\# Binomial distribution is used for yes/no type experiments.\# Example: success or failure, pass or fail.\# dbinom() calculates theoretical probability.\# Example:\# Probability of getting exactly 3 successes\# when number of trials \= 10\# and probability of success \= 0.5dbinom(3, size \= 10, prob \= 0.5)\# Interpretation:\# This gives probability of exactly 3 successes.\# \----------------------------------------------------\# rbinom() generates random binomial sample data.\# Example:\# Generate 20 experiments where each experiment has\# 10 trials and success probability is 0.5rbinom(20, size \= 10, prob \= 0.5) |
| :---- |


* **4.5.2 dpois(), rpois()**

| \# \----------------------------------------------------\# 4.5.2 dpois() and rpois()\# Poisson distribution is used for counting rare events\# happening in a fixed time or space.\# Example:\# Average event rate (lambda) \= 3\# dpois() calculates probability of exactly k events.dpois(2, lambda \= 3)\# Interpretation:\# Probability of observing exactly 2 events when average rate is 3\.\# \----------------------------------------------------\# rpois() generates random Poisson distributed data.\# Example:\# Generate 20 random observations with mean event rate \= 3rpois(20, lambda \= 3)\# These functions are useful for modeling\# discrete probability distributions. |
| :---- |


* **4.5.3 dnorm(), pnorm(), rnorm()**

| \# 4.5.3 dnorm(), pnorm(), rnorm() (More explanation)\# \-------------------------------------------\# dnorm() \- Probability density function\# \-------------------------------------------\# dnorm(x, mean, sd) gives height of the normal curve at point x.\# It does NOT give probability directly because continuous probability\# is calculated using area under the curve.dnorm(0, mean \= 0, sd \= 1)\# \-------------------------------------------\# pnorm() \- Cumulative probability\# \-------------------------------------------\# pnorm(x) gives probability that a random value is less than or equal to x.\# It calculates the area under the normal curve from left side up to x.pnorm(1.96, mean \= 0, sd \= 1)\# Example interpretation:\# pnorm(1.96) ≈ 0.975 means about 97.5% probability is below 1.96.\# \-------------------------------------------\# rnorm() \- Random sampling from normal distribution\# \-------------------------------------------\# Generates random numbers that follow normal distribution pattern.rnorm(20, mean \= 0, sd \= 1)\# These functions help analyze normal distribution behavior,\# probability calculation, and simulation experiments. |
| :---- |


* **4.5.4 CLT simulations**

| \# 4.5.4 CLT Simulations (Detailed Explanation)\# \----------------------------------------------------\# Step 1: Create population data\# \----------------------------------------------------\# Population does not need to follow normal distribution.set.seed(123)population \<- runif(10000, min \= 0, max \= 100)\# runif() generates random numbers uniformly between 0 and 100\# \----------------------------------------------------\# Step 2: Define simulation parameters\# \----------------------------------------------------num\_samples \<- 1000\# Number of repeated sampling experimentssample\_size \<- 30\# Number of observations in each sample\# \----------------------------------------------------\# Step 3: Calculate sample means repeatedly\# \----------------------------------------------------sample\_means \<- numeric(num\_samples)\# Create empty storage to save sample meansfor(i in 1:num\_samples){  sample\_means\[i\] \<- mean(sample(population,                                 sample\_size,                                 replace \= TRUE))}\# \----------------------------------------------------\# Step 4: Visualize result\# \----------------------------------------------------hist(sample\_means,     main \= "Central Limit Theorem Simulation",     xlab \= "Sample Means",     breaks \= 30)\# \----------------------------------------------------\# Concept behind this simulation:\# Even if population data is not normal,\# the distribution of sample means becomes approximately normal\# when sample size and number of samples are large. |
| :---- |


---

### **5\. Statistical Inference: Estimation and Testing**

**5.1 Principles of Inference**

* **5.1.1 Sampling distributions**  
  * Sampling distribution is the pattern formed by statistics from many repeated samples, like checking average height from many student groups.  
* **5.1.2 Point vs interval estimation**  
  * Point estimation means using one number to guess population value, like saying the average exam score is 75\.  
  * Interval estimation means using a range to guess population value, like saying the average score is between 70 and 80\.

**5.2 Hypothesis Testing Framework**

1) **5.2.1 Null and alternative hypotheses**  
   1) Null hypothesis means no effect or no difference, like saying a medicine has no effect.  
   2) Alternative hypothesis means there is an effect or difference.  
2) **5.2.2 Six-step hypothesis testing procedure**  
* State hypotheses  
* Choose test  
* Set significance level  
* Calculate statistic  
* Compare result  
* Make decision

Six-step hypothesis testing example: 

**Testing whether a new medicine lowers blood pressure.**

1. **State hypotheses:** Assume the medicine has no effect (null hypothesis) and the medicine lowers blood pressure (alternative hypothesis).  
2. **Choose test:** Use a t-test to compare blood pressure before and after taking the medicine.  
3. **Set significance level:** Usually 5% significance level is used, meaning there is a 5% risk of making a wrong decision.  
4. **Calculate statistics:** Collect sample data and compute the t-value and p-value.  
5. **Compare result:** If the p-value is smaller than 0.05, the result is considered statistically significant.  
6. **Make a decision:** Reject the null hypothesis if evidence is strong enough, otherwise do not reject it.

**5.3 Errors and Significance**

* **5.3.1 Type I error**  
  Type I error means wrongly rejecting a true null hypothesis, like saying a medicine works when it actually doesn’t.  
* **5.3.2 Type II error**  
  Type II error means failing to reject a false null hypothesis, like saying a medicine doesn’t work when it actually does.  
* **5.3.3 p-values**  
  p-value is the probability of getting the observed result if the null hypothesis is true; small p-value means strong evidence against the null hypothesis.

**5.4 R Coverage**

* **5.4.1 Manual test statistic computation**

| \# 5.4.1 Manual test statistic computation (Clean variable names)\# Sample dataset: blood pressure reduction measurementsbp\_sample \<- c(5, 7, 4, 6, 5, 8, 7, 6, 5, 4)\# Hypothesized population mean under null hypothesishypothesized\_mean \<- 5\# Sample statisticssample\_mean \<- mean(bp\_sample)sample\_sd \<- sd(bp\_sample)sample\_size \<- length(bp\_sample)\# Degree of freedom (independent information available)\# For one-sample t-test → df \= sample\_size \- 1degree\_freedom \<- sample\_size \- 1\# t-statistic measures distance between sample mean and hypothesized meant\_statistic \<- (sample\_mean \- hypothesized\_mean) /               (sample\_sd / sqrt(sample\_size))t\_statistic\# p-value calculation (two-tailed test)p\_value \<- 2 \* pt(-abs(t\_statistic), degree\_freedom)p\_value |
| :---- |


* **5.4.2 Simulation-based inference**

| \# \-------------------------------------------------\# 5.4.2 Simulation-based inference\# \-------------------------------------------------set.seed(123)number\_of\_simulations \<- 10000\# Store simulated sample meanssimulated\_means \<- numeric(number\_of\_simulations)for(i in 1:number\_of\_simulations){  \# Random sampling with replacement  simulated\_sample \<- sample(bp\_sample,                             sample\_size,                             replace \= TRUE)  \# Store mean of each simulated sample  simulated\_means\[i\] \<- mean(simulated\_sample)}\# Visualization of sampling distributionhist(simulated\_means,     main \= "Simulation-based Inference",     xlab \= "Sample Means")\# Red line represents null hypothesis meanabline(v \= hypothesized\_mean, col \= "red", lwd \= 2) |
| :---- |

---

### **6\. Classical Parametric Tests**

**6.1 Tests for Means**

* **6.1.1 z-tests**  
  z-test checks if a sample mean differs from a population mean when population variance (σ²) is known and sample size is large.  
* **6.1.2 One-sample t-test**  
  One-sample t-test compares sample mean (x̄) with population mean (μ) when population variance (σ²) is unknown.  
* **6.1.3 Independent two-sample t-test**  
  Independent two-sample t-test compares means (x̄₁, x̄₂) of two different groups.  
* **6.1.4 Paired t-test**  
  Paired t-test compares mean difference (d̄) within the same group before and after treatment.

**6.2 Tests for Proportions**

* **6.2.1 One-sample proportion tests**  
  One-sample proportion test checks whether a sample proportion (p̂) is different from a population proportion (p₀).  
* **6.2.2 Two-sample proportion tests**  
  Two-sample proportion test checks whether two sample proportions (p̂₁, p̂₂) are significantly different.

**6.3 Confidence Intervals (CI)**

* **6.3.1 Construction and interpretation**

  Construction and interpretation: A confidence interval is built as estimate ± margin of error, and it gives a range where the true population value (μ or p) is likely to lie.

* **6.3.2 Coverage probability**

  Coverage probability: If we repeat sampling many times, about 95% of the intervals (for 95% CI) will contain the true population value.

**6.4 R Coverage**

| \# 6.4.1 t.test() variants\# Used to test population mean (μ) when variance (σ²) is unknown.\# \-----------------------------\# One-sample t-test\# \-----------------------------\# Question: Is sample mean different from 5?t.test(bp\_sample, mu \= 5)\# mu \= hypothesized population mean (μ₀)\# Output gives:\# \- t value (test statistic)\# \- p-value (decision evidence)\# \- confidence interval for μ\# \-----------------------------\# Independent two-sample t-test\# \-----------------------------\# Question: Are means of two groups different?t.test(group1, group2)\# Compares x̄₁ and x̄₂\# Assumes groups are independent\# \-----------------------------\# Paired t-test\# \-----------------------------\# Question: Did treatment change same people's values?t.test(before, after, paired \= TRUE)\# Compares mean difference (d̄)\# Used for before-after measurements\# 6.4.2 prop.test()\# Used to test population proportion (p)\# One-sample proportion testprop.test(x \= 45, n \= 100, p \= 0.5)\# x \= number of successes\# n \= total trials\# p \= hypothesized population proportion (p₀)\# Two-sample proportion testprop.test(x \= c(45, 30), n \= c(100, 80))\# Compares two sample proportions (p̂₁ vs p̂₂)\# 6.4.3 Manual vs automated Confidence Intervals (CI)\# Automated CIt.test(bp\_sample)$conf.int\# Manual CI formula:\# x̄ ± t\_critical × (s / √n)\# x̄ \= sample mean\# s \= sample standard deviation\# n \= sample size\# t\_critical depends on degree of freedom (df \= n − 1\)\# CI gives the range where true μ likely lies. |
| :---- |

---

### **7\. Model Assumptions and Categorical Inference**

**7.1 Assumption Checking**

* **7.1.1 Normality**  
  Data should roughly follow a normal distribution when testing mean (μ).  
* **7.1.2 Equal variances**  
  Group variances (σ₁², σ₂²) should be approximately similar in two-sample tests.  
* **7.1.3 Independence**  
  Observations should not influence each other.

**7.2 Chi-Squared Methods**

* **7.2.1 Goodness-of-fit tests**  
  Goodness-of-fit test (χ² test) checks whether observed counts match expected counts.  
* **7.2.2 Tests of independence**  
  Test of independence (χ² test) checks whether two categorical variables are related or independent.

**7.3 Mathematical Foundations**

* **7.3.1 Chi-Squared distribution**  
  Chi-Squared distribution (χ² distribution) is the probability distribution used for tests based on squared differences between observed and expected counts.  
* **7.3.2 Degrees of freedom**  
  Degrees of freedom (df) is the number of independent values that can vary when calculating χ², usually based on number of categories.

**7.4 R Coverage**

| \# \==========================================================\# 7.4 R Coverage (Super simple explanation version)\# \==========================================================\# \----------------------------------------------------------\# 7.4.1 shapiro.test()  → Check if data looks normal\# \----------------------------------------------------------\# Why this test?\# Many statistical tests work only if data is normal.\# Idea:\# This test checks if sample data behaves like normal bell curve data.sample\_data \<- c(12, 15, 14, 10, 13, 16, 14, 11, 15, 13)shapiro.test(sample\_data)\# Simple rule:\# p-value \> 0.05 → Data looks normal.\# p-value \< 0.05 → Data is not normal.\# \----------------------------------------------------------\# 7.4.2 var.test()  → Compare spread of two groups\# \----------------------------------------------------------\# Why this test?\# Before comparing two groups' means, check if their spread is similar.group\_A \<- c(10, 12, 11, 13, 12)group\_B \<- c(14, 18, 15, 17, 16)var.test(group\_A, group\_B)\# Simple rule:\# p-value \> 0.05 → Spread of two groups is similar.\# p-value \< 0.05 → Spread is different.\# \----------------------------------------------------------\# 7.4.3 chisq.test()  → Check relationship between categories\# \----------------------------------------------------------\# Why this test?\# Used when data is categorical (like gender, yes/no, choice).\# Example: Relationship between two groups\# Create table like survey result countsdata\_table \<- matrix(c(30, 20,                       25, 25),                     nrow \= 2,                     byrow \= TRUE)chisq.test(data\_table)\# Simple rule:\# p-value \< 0.05 → Categories are related.\# p-value \> 0.05 → Categories are independent (no relation). |
| :---- |

---

### **8\. Effect Sizes and Practical Interpretation**

**8.1 Beyond p-values**  
**Beyond p-values means checking real-world importance, not only statistical test results.**

* **8.1.1 Statistical vs practical significance**  
  * Statistical significance means result is unlikely due to chance, while practical significance means result is actually useful in real life.


**8.2 Effect Size Measures**

* **8.2.1 Cohen’s d**  
  * Cohen’s d measures how big the difference is between two means.  
* **8.2.2 Phi coefficient**  
  * Phi coefficient (φ) measures the strength of relationship between two categorical variables.

**8.3 R Coverage**

| \# \==========================================================\# 8.3 R Coverage\# \==========================================================\# \----------------------------------------------------------\# 8.3.1 Manual computation of effect size\# \----------------------------------------------------------\# Example: Cohen's d (difference size between two groups)group1 \<- c(20, 22, 21, 23, 24)group2 \<- c(10, 11, 12, 13, 14)\# Mean difference between groupsmean\_diff \<- mean(group1) \- mean(group2)\# Pooled standard deviation (average spread of data)pooled\_sd \<- sqrt((var(group1) \+ var(group2)) / 2)\# Cohen's d formula (effect size measurement)cohen\_d \<- mean\_diff / pooled\_sdcohen\_d\# \----------------------------------------------------------\# 8.3.2 Validation via simulation\# \----------------------------------------------------------set.seed(123)simulation\_count \<- 10000simulated\_effects \<- numeric(simulation\_count)for(i in 1:simulation\_count){  \# Randomly sample from groups (with replacement)  sample1 \<- sample(group1, length(group1), replace \= TRUE)  sample2 \<- sample(group2, length(group2), replace \= TRUE)  \# Calculate simulated effect size  simulated\_effects\[i\] \<- (mean(sample1) \- mean(sample2)) /                          sqrt((var(sample1) \+ var(sample2)) / 2)}\# Visualize simulation resulthist(simulated\_effects,     main \= "Effect Size Simulation",     xlab \= "Cohen's d values")\# \----------------------------------------------------------\# 8.3.3 Reporting standards\# \----------------------------------------------------------\# When reporting results, always include:\# \- Effect size value\# \- Confidence interval if possible\# \- p-value\# \- Sample size\# Example report format:\# Effect size (Cohen's d) \= value\# Interpretation:\# 0.2 → small effect\# 0.5 → medium effect\# 0.8 → large effect |
| :---- |

---

### **9\. Likelihood-Based Inference and Estimation**

**9.1 Likelihood Theory**

* **9.1.1 Likelihood vs probability**  
  * Likelihood vs probability: Probability predicts future outcomes, while likelihood measures how well a parameter explains observed data.  
* **9.1.2 Maximum Likelihood principle**  
  * Maximum likelihood principle means choosing parameter values that make observed data most probable.

**9.2 MLE Construction**

* **9.2.1 Likelihood functions**  
  * **Likelihood function shows how likely data is for different parameter values.**  
* **9.2.2 Log-likelihoods**  
  * **Log-likelihood is the logarithm of likelihood, used to make calculation easier.**  
* **9.2.3 Derivatives and optimization logic**  
  * Derivatives and optimization logic mean finding parameter values that maximize likelihood mathematically.

**9.3 Analytical MLEs**

* **9.3.1 Poisson parameter estimation**  
  * **Poisson parameter estimation estimates λ (event rate).**  
* **9.3.2 Normal distribution parameters**  
  * Normal distribution parameter estimation estimates mean (μ) and variance (σ²).  
* **9.3.3 MLE vs unbiased estimators**  
  * MLE vs unbiased estimators means MLE gives most likely parameter value, while unbiased estimators give average correct value over many samples.


**9.4 R Coverage**

| \# \==========================================================\# 9.4 R Coverage (Very simple understanding style)\# \==========================================================\# \----------------------------------------------------------\# 9.4.1 Writing likelihood functions manually\# \----------------------------------------------------------\# Example: Likelihood function for normal distribution (σ \= 1\)\# Likelihood means:\# How well parameter value explains observed data.log\_likelihood \<- function(mu){  data \<- c(10, 12, 11, 13, 12)  \# Normal log-likelihood formula idea  \# We compute probability density for each data point  \# and add log values (log used for easier math)  sum(dnorm(data, mean \= mu, sd \= 1, log \= TRUE))}\# Test likelihood for one parameter valuelog\_likelihood(12)\# \----------------------------------------------------------\# 9.4.2 mle() usage (if package is available)\# \----------------------------------------------------------\# mle() is used to find parameter value that maximizes likelihood.\# Example structure (may need stats4 package)\# library(stats4)\# mle\_estimation \<- mle(function(mu){\#   \-log\_likelihood(mu)   \# negative because mle() minimizes by default\# })\# \----------------------------------------------------------\# 9.4.3 Basic optim() examples\# \----------------------------------------------------------\# optim() is a general function used to find best parameter value.\# Starting guess for parameterstart\_value \<- 12\# Use optimization to maximize likelihood (use negative likelihood)result \<- optim(  par \= start\_value,  fn \= function(mu) \-log\_likelihood(mu))result$par\# Simple idea:\# optim() searches for parameter value that makes data most likely. |
| :---- |

---

### **10\. Advanced Likelihood Methods and Numerical Optimization**

**10.1 Extended Distributions**

* **10.1.1 Gamma distribution**  
  * Gamma distribution Γ(α, β) is used for modeling waiting times and positive continuous data. α controls shape (curve form) and β controls spread (stretching of curve).  
    **![][image3]**

**10.2 Properties of MLE**

* **10.2.1 Consistency**  
  * **Consistency means MLE estimate → true parameter value as sample size (n → ∞) increases.**  
* **10.2.2 Efficiency**  
  * **Efficiency means MLE has smaller variance compared to other estimators.**  
* **10.2.3 Asymptotic normality**  
  * **Asymptotic normality means MLE estimate behaves like Normal distribution when sample size is large.**

**10.3 Likelihood-Based Testing**

* **10.3.1 Likelihood Ratio Tests**  
  * **Likelihood Ratio Test (LRT) compares two models using likelihood ratio (Λ) to check which model fits better.**  
* **10.3.2 Profile likelihood**  
  * **Profile likelihood means fixing one parameter and maximizing likelihood over others.**  
* **10.3.3 Likelihood-based confidence intervals**  
  * **Likelihood-based confidence interval is a parameter range where likelihood remains reasonably high.**

**10.4 Numerical Optimization Algorithms**

* **10.4.1 Gradient ascent and descent**  
  * **Gradient ascent moves in direction of increasing likelihood, while gradient descent moves opposite to minimize error.**  
* **10.4.2 Newton’s Method**  
  * **Newton’s method uses derivative and curvature information to find optimum parameter value quickly.**  
* **10.4.3 BFGS**  
  * **BFGS is a fast iterative optimization algorithm used for likelihood maximization.**  
* **10.4.4 Nelder–Mead**  
  * Nelder–Mead is a derivative-free optimization method used when derivatives are difficult to compute.

**10.5 R Coverage**

| \# \==========================================================\# 10.5 R Coverage (Likelihood Optimization Tools)\# \==========================================================\# \----------------------------------------------------------\# 10.5.1 optim() with multiple methods\# \----------------------------------------------------------\# optim() is a general optimization function in R.\# It searches for parameter value that maximizes likelihood\# or minimizes error.\# Example likelihood function (negative log-likelihood)likelihood\_function \<- function(mu){  data \<- c(10, 12, 11, 13, 12)  \# Negative log likelihood (because optim() usually minimizes)  return(-sum(dnorm(data, mean \= mu, sd \= 1, log \= TRUE)))}\# Try different optimization methodsstart\_value \<- 12optim(start\_value,      likelihood\_function,      method \= "BFGS")optim(start\_value,      likelihood\_function,      method \= "Nelder-Mead")\# Common methods:\# \- BFGS → fast and accurate for smooth functions\# \- Nelder-Mead → works when derivatives are hard to compute\# \----------------------------------------------------------\# 10.5.2 Convergence diagnostics\# \----------------------------------------------------------\# Convergence means optimization algorithm successfully found\# stable parameter estimate.result \<- optim(start\_value,                likelihood\_function,                method \= "BFGS",                control \= list(trace \= 1))\# If convergence code \= 0 → optimization successful\# \----------------------------------------------------------\# 10.5.3 Likelihood profiling and LRT implementation\# \----------------------------------------------------------\# Likelihood profiling means checking likelihood value\# across different parameter guesses.parameter\_grid \<- seq(10, 14, length.out \= 50)profile\_values \<- sapply(parameter\_grid, function(mu){  \-likelihood\_function(mu)})\# Likelihood Ratio Test (LRT) idea:\# Compare:\# Model 1 → full model likelihood\# Model 2 → simplified model likelihood\# LRT statistic:\# 2 × (logLik\_complex\_model \- logLik\_simple\_model)\# Large LRT value → complex model is better.\# Visualizationplot(parameter\_grid,     profile\_values,     main \= "Likelihood Profile",     xlab \= "Parameter value",     ylab \= "Likelihood") |
| :---- |

[image1]: <data:image/png;base64,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>

[image2]: <data:image/png;base64,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>

[image3]: <data:image/png;base64,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>