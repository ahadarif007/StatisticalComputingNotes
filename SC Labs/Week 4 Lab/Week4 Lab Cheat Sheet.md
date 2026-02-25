# Week 4 Lab – Quick Reference (Non‑Statisticians)

| **Topic** | **When to use it** | **Key R function(s)** | **One‑line tip** |
|---|---|---|---|
| **Likelihood (general)** | Any model where you want the most plausible parameter(s) given data | Write a *log‑likelihood* function and maximise it (e.g., with `mle()` or `optim()`) | Think of it as “which parameter makes my data most likely?”. |
| **Poisson log‑likelihood** | Counting rare events (e.g., horse‑kick deaths, number of emails) | `dpois(x, lambda, log = TRUE)` → sum for log‑likelihood | MLE for λ = sample mean. |
| **Normal log‑likelihood (known σ)** | Continuous data where variance is known (e.g., birth weight with σ=1) | `dnorm(x, mean = mu, sd = 1, log = TRUE)` → sum | MLE for μ = sample mean. |
| **Binomial log‑likelihood** | Success/failure counts with fixed number of trials (e.g., seed germination) | `dbinom(y, size = n, prob = p, log = TRUE)` → sum | MLE for p = total successes / total trials. |
| **Exponential log‑likelihood** | Waiting times between events (e.g., coffee‑shop arrivals) | `dexp(x, rate = lambda, log = TRUE)` → sum | MLE for λ = 1 / sample mean. |
| **Gamma log‑likelihood** | Positive, right‑skewed data with two parameters (shape α, rate β) | `dgamma(x, shape = alpha, rate = beta, log = TRUE)` → sum | No closed‑form MLE for α – use numerical optimisation. |
| **`mle()`** | Find MLEs when you have a (negative) log‑likelihood function | `mle(negloglik, start = list(param = value), nobs = N)` | Returns estimates, standard errors, and a convergence code. |
| **`optim()`** | General optimiser; underlying engine for `mle()` | `optim(par = start, fn = negloglik, method = "BFGS"/"Nelder-Mead"/"L-BFGS-B")` | Choose **BFGS** for speed (needs gradient), **Nelder‑Mead** if you have no derivatives. |
| **Gradient ascent (manual)** | Simple “walk uphill” method for a single‑parameter log‑likelihood | Write a gradient function, update `theta <- theta + gamma * grad(theta)` | Works but may need many iterations; tune the learning rate `gamma`. |
| **Likelihood surface (2‑D)** | When two parameters are unknown (e.g., μ & σ for Normal) | Evaluate `loglik(mu, sigma)` on a grid and plot with `filled.contour()` | Visualise the peak and shape of uncertainty. |
| **Convergence check** | After optimisation, ensure the algorithm succeeded | `fit@details$convergence == 0` (0 = success) | Always verify before trusting the result! |
| **Exam strategy** | Any lab question about likelihood or MLE | 1️⃣ Identify the distribution → 2️⃣ Write the log‑likelihood → 3️⃣ Use `mle()`/`optim()` or the analytic MLE → 4️⃣ Check convergence → 5️⃣ State the estimate in plain English |

### Quick R snippets (copy‑paste)
- Poisson log‑likelihood (λ): `sum(dpois(x, lambda, log = TRUE))`
- Normal log‑likelihood (μ, σ = 1): `sum(dnorm(x, mean = mu, sd = 1, log = TRUE))`
- Binomial log‑likelihood (p): `sum(dbinom(y, size = 20, prob = p, log = TRUE))`
- Exponential log‑likelihood (λ): `sum(dexp(x, rate = lambda, log = TRUE))`
- Gamma log‑likelihood (α, β): `sum(dgamma(x, shape = alpha, rate = beta, log = TRUE))`
- MLE with `mle()`: `fit <- mle(negloglik, start = list(param = 1), nobs = length(data))`
- Optimise with BFGS: `optim(par = 1, fn = negloglik, method = "BFGS")`
- Gradient ascent (single param):
```r
grad <- function(theta) { /* derivative of log‑likelihood */ }
for(i in 1:500){ theta <- theta + gamma * grad(theta) }
```

### Handy tips
- **Log‑likelihood** is easier to work with than raw likelihood (adds instead of multiplies). 
- **MLE = parameter that maximises log‑likelihood**; often equals a simple sample statistic (mean, proportion, 1/mean). 
- **Check convergence** (`fit@details$convergence`). If not 0, rerun with a better start value. 
- **Bounded parameters** (like probabilities) → use `method = "Brent"` or `L‑BFGS‑B` with `lower`/`upper`. 
- **Plot the surface** for two parameters to see uncertainty shape. 
- **One‑sentence conclusion**: “The MLE for λ is 0.73, meaning the average rate of events is about 0.73 per unit.”

---
*Keep this table open, locate the row you need, copy the R line, run it, and write the answer in plain English.*
