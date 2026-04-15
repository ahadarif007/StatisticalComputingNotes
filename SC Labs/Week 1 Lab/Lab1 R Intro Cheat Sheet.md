# Lab 1 R Intro – Ultra‑Compact Cheat Sheet

## 1️⃣ Console & Help
| Symbol | Action |
|---|---|
| `>` | Ready for command – run with **Ctrl+Enter** |
| `+` | Incomplete line – finish or **Esc** to cancel |
| `Tab` | Auto‑complete names |
| `?fn` | Open help for `fn` |
| `example(fn)` | Show quick demo |

## 2️⃣ Core Syntax
| Concept | R | Python |
|---|---|---|
| Assignment | `x <- 5` | `x = 5` |
| Vector | `c(1,2,3)` | `[1,2,3]` |
| Index (1‑based) | `x[1]` | `x[0]` |
| Append | `x <- c(x,4)` | `x.append(4)` |
| Load pkg | `library(pkg)` | `import pkg` |

## 3️⃣ Vectors
| Op | Code |
|---|---|
| Create | `x <- c(1,2,3)` |
| Mean | `mean(x)` |
| Sum | `sum(x)` |
| SD | `sd(x)` |
| Length | `length(x)` |
| Filter | `x[x>2]` |
| Replace | `x[x<0] <- 0` |

## 4️⃣ Data Frames
| Task | Code |
|---|---|
| Make | `df <- data.frame(name=c("A","B"), age=c(20,NA))` |
| Peek | `head(df)` / `str(df)` |
| Summary | `summary(df)` |
| Ignore NA | `mean(df$age, na.rm=TRUE)` |
| Add column via map | `g <- c(A=70,B=60); df$score <- g[df$grade]` |
| Group mean | `aggregate(age~grade, df, mean, na.rm=TRUE)` |

## 5️⃣ Simple Probability (R)
```r
omega <- 1:6               # sample space
A <- omega[omega%%2==0]    # even
B <- omega[omega>3]       # >3
P_A <- length(A)/6
P_B <- length(B)/6
P_A_given_B <- length(intersect(A,B))/length(B)
```
*Use `length()` counts; `intersect()` / `union()` for combos.*

## 6️⃣ Quick Plots
| Plot | Code |
|---|---|
| Histogram | `hist(x, breaks=15, col="lightblue")` |
| Add density | `lines(density(x), col="red")` |
| Boxplot (group) | `boxplot(score~grade, data=df)` |

## 7️⃣ Exam‑Survival 6‑step
1. **Read** – what data type & goal? (mean, prob, plot…)  
2. **Pick** – find matching row in tables above.  
3. **Copy** – one‑line R command.  
4. **Run** – `Ctrl+Enter`.  
5. **Check** – plausible? fix `na.rm=TRUE` if needed.  
6. **Answer** – state number & plain English meaning.

---
*Keep this sheet open, locate the row you need, copy‑paste, run, and write the answer.*
