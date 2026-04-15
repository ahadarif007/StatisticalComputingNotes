# R Lab Cheat Sheet

# Week 01

# R Basics – Concept + Code + Meaning Table

| Term | Simple Explanation | Code |
|---|---|---|
| Mean | Average value of data. Add all numbers and divide by count. | `mean(x, na.rm=TRUE)` |
| Variance | Measures how far data points are spread from the mean. | `var(x)` |
| Standard Deviation | Square root of variance; shows typical deviation from mean. | `sd(x)` |
| Vector Filtering | Selects data that satisfies a condition. | `x[x > 10]` |
| Replace Values | Change unwanted values to something else. | `x[x < 0] <- 0` |
| Vector Length | Number of elements in a vector. | `length(x)` |
| Histogram | Shows how data values are distributed. | `hist(x, breaks=15)` |
| Density Plot | Smooth curve showing distribution shape. | `lines(density(x))` |
| Boxplot | Displays median, spread, and possible outliers. | `boxplot(score ~ group, data=df)` |
| Read CSV | Load dataset stored in CSV file. | `df <- read.csv("file.csv")` |
| Write CSV | Save dataset into CSV format. | `write.csv(df,"out.csv",row.names=FALSE)` |
| Data Preview | Look at first few rows of data. | `head(df)` |
| Data Structure | Shows variable types and dataset layout. | `str(df)` |
| Summary Statistics | Quick overview of data (min, median, mean, max). | `summary(df)` |
| Row Selection | Choose specific rows from dataset. | `df[df$age > 20, ]` |
| Column Selection | Choose specific columns from dataset. | `df[, c("name","age")]` |
| Group Mean | Mean value calculated for each category group. | `aggregate(age ~ group, df, mean, na.rm=TRUE)` |
| Factor Variable | Used for categorical data like gender or grade. | `factor(c("A","B","A"))` |
| Missing Value Handling | Ignore missing data during calculation. | `mean(df$age, na.rm=TRUE)` |

## Tips

- First check: What is asked (mean, plot, probability, filtering, etc.).
- Search matching command in table.
- Add `na.rm=TRUE` if dataset may contain missing values.
- Write final numeric answer plus one short interpretation sentence.

---
# Week 2 Probability & Distributions

| Topic | What it means | When to use | R function(s) | Tip |
|---|---|---|---|---|
| Hypergeometric | Probability without replacement | Sampling items without putting them back (like cards from deck) | `dhyper()`, `phyper()` | dhyper = exact probability of k successes; phyper = cumulative ≤k |
| Binomial | Fixed number of independent trials | Coin flips or success/failure experiments | `dbinom()`, `pbinom()` | dbinom = exact probability of k successes; pbinom = cumulative ≤k |
| Poisson | Counting rare events | Number of events in fixed time or space | `dpois()`, `ppois()` | dpois = exact probability of k events; ppois = cumulative ≤k |
| Normal | Continuous data distribution | Height, marks, temperature, CLT related data | `dnorm()`, `pnorm()`, `qnorm()` | dnorm = density (curve height); pnorm = cumulative ≤x; qnorm = inverse probability |
| Birthday problem | Shared birthday probability | Finding number of people needed so shared birthday probability exceeds 50% | Custom code (see below) | \( P(shared)=1-P(all\;different) \) |

## Quick Snippets

- `dhyper(3,20,40,7)`
- `pbinom(k, size=10, prob=0.5)`
- `dpois(5, lambda=1)`
- `pnorm(68, mean=65, sd=3)`
- `qnorm(0.90, mean=65, sd=3)`

## Birthday Problem Code

```r
prob_all_diff <- function(N){
  if(N<=1) return(1)
  prob_all_diff(N-1)*(365-(N-1))/365
}
prob_shared <- function(N){
  1 - prob_all_diff(N)
}
which(sapply(1:60, prob_shared) >= 0.5)[1]  # → 23
```

# Week 3 Hypothesis Testing

| Test | What it means | When to use | R function(s) | Tip |
|---|---|---|---|---| 
| Paired t-test | Compare mean difference of same subjects | Used when data is collected from same group before and after | `t.test(x, y, paired=TRUE)` | Tests if mean difference is zero |
| Wilcoxon signed-rank test | Non-parametric paired test | Used when paired data is not normally distributed | `wilcox.test(x, y, paired=TRUE)` | Good alternative to paired t-test |
| Two-sample t-test (equal variance) | Compare means of two independent groups | When data is normal and variance is similar | `t.test(g1, g2, var.equal=TRUE)` | Checks difference between group means |
| Welch’s t-test | Two independent groups with unequal variance | When variance between groups is different | `t.test(g1, g2, var.equal=FALSE)` | Default safer option |
| Wilcoxon rank-sum test | Non-parametric independent group test | When data is not normal | `wilcox.test(g1, g2)` | Distribution-free method |
| Proportion test | Compare success probability between groups | Used for binary outcomes like pass/fail | `prop.test(successes, trials)` | Works with percentages |
| Chi-square goodness-of-fit test | Check if observed data matches expected distribution | Single categorical variable | `chisq.test(observed, p=expected)` | Tests distribution fit |
| Chi-square test of independence | Check relationship between two categorical variables | Used for contingency table analysis | `chisq.test(matrix)` | Tests association between variables |


# Week 4 Likelihood & Maximum Likelihood Estimation (MLE)
| Topic | What it means | When to use | R function(s) | Tip |
|---|---|---|---|---|
| General likelihood | Find parameter values that make data most probable | Any statistical model requiring parameter estimation | Write log-likelihood manually, then use `mle()` or `optim()` | Always maximise log-likelihood (log makes multiplication easier) |
| Poisson log-likelihood | Likelihood for count data | When data represents number of events | `dpois(x, lambda, log=TRUE)` and sum results | MLE estimate of λ is sample mean |
| Normal log-likelihood (known σ) | Likelihood for continuous data | When data is normally distributed and variance is known | `dnorm(x, mu, sd, log=TRUE)` and sum | MLE estimate of μ is sample mean |
| Binomial log-likelihood | Likelihood for binary outcome data | When observations are success/failure counts | `dbinom(y, size=n, prob=p, log=TRUE)` | MLE estimate of p = total successes ÷ total trials |
| Exponential log-likelihood | Models waiting time or survival data | When time between events is studied | `dexp(x, rate=lambda, log=TRUE)` | MLE estimate of rate λ = 1 / mean(x) |
| Gamma log-likelihood | Right-skewed positive continuous data | For skewed data like income or survival time | `dgamma(x, shape=α, rate=β, log=TRUE)` | Usually solved using optimisation functions |
| `mle()` function | Estimates parameters by likelihood maximisation | When analytic likelihood form is available | `mle(negloglik, start=list(param=1), nobs=N)` | Returns estimate, standard error and convergence status |
| `optim()` function | General optimisation tool | When likelihood function is complex | `optim(par=start, fn=negloglik, method="BFGS")` | BFGS is fast; Nelder-Mead is more robust |
| Gradient ascent | Iterative likelihood maximisation | Simple optimisation problems | Update rule: `theta <- theta + gamma * gradient` | Learning rate must be small |
| Likelihood surface plot | Visualise likelihood across parameter values | When two parameters are unknown | Grid search + `filled.contour()` | Shows peak region of likelihood |
| Convergence check | Verify optimisation success | After running optimisation | `fit@details$convergence == 0` | Zero means optimisation succeeded |

**Quick snippets**
- Poisson log‑likelihood: `sum(dpois(x, lambda, log=TRUE))`
- Normal log‑likelihood (σ=1): `sum(dnorm(x, mu, sd=1, log=TRUE))`
- Binomial log‑likelihood: `sum(dbinom(y, size=n, prob=p, log=TRUE))`
- Exponential log‑likelihood: `sum(dexp(x, rate=lambda, log=TRUE))`
- Gamma log‑likelihood: `sum(dgamma(x, shape=α, rate=β, log=TRUE))`
- MLE with `mle()`: `fit <- mle(negloglik, start=list(param=1), nobs=length(data))`
- Optimise with BFGS: `optim(par=1, fn=negloglik, method="BFGS")`

