# Week 3 Lab – Quick Reference (Non‑Statisticians)

| **Topic** | **When to use it** | **Key R function(s)** | **One‑line tip** |
|---|---|---|---|
| **Poisson distribution** | Counting rare events in a fixed interval (e.g., emails per hour) | `dpois(k, lambda)` – exact; `ppois(q, lambda)` – cumulative | Use for *counts* when events are independent and λ is small. |
| **Normal distribution** | Continuous measurements that look bell‑shaped (heights, test scores) | `dnorm(x, mean, sd)`, `pnorm(q, mean, sd)`, `qnorm(p, mean, sd)` | Use for probabilities about *continuous* data; CLT makes many means approx Normal. |
| **Gamma distribution** | Positive, right‑skewed data such as waiting times | `dgamma(x, shape, rate)` | Good for modelling *time until an event* occurs. |
| **Chi‑squared distribution** | Test statistics for variance, goodness‑of‑fit, or independence (categorical data) | `dchisq(x, df)`, `pchisq(q, df)` | Used inside `chisq.test()` for categorical tables. |
| **Paired t‑test** | Same subjects measured twice (before/after) and data is roughly normal | `t.test(before, after, paired = TRUE)` | Checks if the *mean difference* ≠ 0. |
| **Wilcoxon signed‑rank test** | Paired data that isn’t normal (small sample) | `wilcox.test(before, after, paired = TRUE)` | Non‑parametric alternative to paired t‑test. |
| **Two‑sample t‑test (equal var)** | Two independent groups, normal, similar spreads | `t.test(group1, group2, var.equal = TRUE)` | Tests if the two means differ. |
| **Welch’s t‑test** | Two independent groups, normal, unequal spreads | `t.test(group1, group2, var.equal = FALSE)` | Handles *unequal variances*. |
| **Wilcoxon rank‑sum test** | Two independent groups, not normal | `wilcox.test(group1, group2)` | Non‑parametric version of two‑sample t‑test. |
| **Proportion test** | Comparing success rates / proportions (e.g., pass/fail) | `prop.test(successes, trials, alternative = "greater"/"two.sided")` | Use for *binary* outcomes. |
| **Chi‑squared goodness‑of‑fit** | Single categorical variable – does observed count match expected? | `chisq.test(observed, p = expected_probs)` | Checks if a distribution (e.g., fair die) fits data. |
| **Chi‑squared test of independence** | Two categorical variables – are they related? | `chisq.test(matrix)` | Tests *association* between categories. |

### Quick exam strategy (same 6‑step recipe)
1. **Read the prompt** – identify the variable type (continuous vs count vs categorical) and whether samples are paired or independent.
2. **Map to a distribution / test** using the table above.
3. **Write down the R command** (copy‑paste from the “Key R function(s)” column).
4. **Run it** – note the p‑value.
5. **Interpret** – p < 0.05 → reject H₀; otherwise fail to reject.
6. **State the conclusion in plain English** (e.g., “The workshop significantly increased study time”).

---
*Keep this table open, find the row you need, copy the R line, run it, and write the answer in plain English.*
