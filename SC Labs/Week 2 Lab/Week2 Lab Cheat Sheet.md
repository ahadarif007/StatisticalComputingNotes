# Week 2 Lab – Quick Reference (Non‑Statisticians)

| **Topic** | **When to use it** | **Key R function(s)** | **One‑line tip** |
|---|---|---|---|
| **Hypergeometric** | Drawing *without* replacement from a known finite set (e.g., card deck, selecting items) | `dhyper(x, m, n, k)` – exact; `phyper(q, m, n, k)` – cumulative | Use for “how many successes in a hand of cards”. |
| **Binomial** | Independent trials with the same success chance (e.g., coin flips, repeated yes/no) | `dbinom(k, size, prob)` – exact; `pbinom(k, size, prob)` – cumulative | Use for “number of heads in 10 flips”. |
| **Poisson** | Rare events over many trials or a time/space interval; also approximates a Binomial when *n* is large & *p* tiny | `dpois(k, lambda)` – exact; `ppois(k, lambda)` – cumulative | Use for “defects per 100 items” or “calls per hour”. |
| **Normal** | Continuous measurements or the sampling distribution of a mean (by CLT) – heights, test scores, etc. | `dnorm(x, mean, sd)`, `pnorm(q, mean, sd)`, `qnorm(p, mean, sd)` | Use for “probability a height is below 68 in”. |
| **Birthday problem** | Find smallest group where the chance of a shared birthday exceeds 50 % | Custom recursive/iterative code (see below) | Remember: `P(shared) = 1 - P(all different)`. |
| **Exam strategy** | Any lab question involving probability | Follow the **d‑p‑q‑r** pattern (density, cumulative, quantile, random) | 1️⃣ Read → 2️⃣ Map to distribution → 3️⃣ Write R line → 4️⃣ Run → 5️⃣ State answer. |

### Quick R snippets (copy‑paste)
- Hypergeometric exact: `dhyper(3,20,40,7)`
- Binomial cumulative ≤ k: `pbinom(k, size=10, prob=0.5)`
- Poisson probability of 5 events: `dpois(5, lambda=1)`
- Normal CDF: `pnorm(68, mean=65, sd=3)`
- Inverse Normal (90th percentile): `qnorm(0.90, mean=65, sd=3)`
- Birthday threshold (R code):
```r
prob_all_diff <- function(N) {
  if (N <= 1) return(1)
  prob_all_diff(N-1) * (365-(N-1))/365
}
prob_shared <- function(N) 1 - prob_all_diff(N)
which(sapply(1:60, prob_shared) >= 0.5)[1]  # → 23
```

### Handy tips
- **Complement**: `P(X > k) = 1 - P(X ≤ k)`.
- **Rounding**: 2‑3 decimals (or as a % with 1‑2 %).
- **Simulation check**: use `r*` functions if time permits.
- **Write a one‑sentence conclusion** – the exam often asks “interpret the result”.

---
*Keep this table open, find the row you need, copy the R line, run it, and write the answer in plain English.*
