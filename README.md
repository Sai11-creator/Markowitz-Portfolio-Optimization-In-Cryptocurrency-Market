# Portfolio-Optimization-In-Cryptocurrency-Market
This project investigates systematic portfolio construction in the cryptocurrency market using constrained mean–variance (Markowitz) optimization.# Portfolio Optimization in Cryptocurrency Markets

Systematic portfolio construction in crypto using **constrained mean–variance (Markowitz) optimization** with a **risk-free cash allocation**, realistic risk controls, and robustness improvements.

> Backtest window: **Jan 2022 → Jan 2024**  
> Universe: **20 liquid crypto-assets + cash**   
> Optimization: **CVXPY (ECOS/SCS)**

---

## Project overview

Crypto portfolios are challenging because returns/covariances are noisy and correlations can spike. This project:
- Benchmarks simple strategies (**Bitcoin-only**, **equal-weighted**)
- Implements **constrained Markowitz rebalancing** (rolling estimates)
- Adds robustness layers to stabilize allocations:
  - Per-asset concentration cap (`w_max`)
  - Transaction fees (proportional costs)
  - Covariance shrinkage (**Ledoit–Wolf**)
  - Convex **SOC diversification constraint** (`D_min`)

---

## Risk controls implemented

Throughout the backtest we consider realistic constraints such as:
- **Long-only** (no shorting)
- **Volatility cap** (annualized)
- **Diversification / concentration control** (via a diversification metric and/or SOC constraint)
- **Fee-cost budget** over the whole backtest (transaction costs)

Full definitions and metrics (Sharpe, max drawdown, diversification metric, etc.) are detailed in the report.

---

## Repository contents

### Notebooks (recommended run order)
- `0_Data_study.ipynb`  
  Data inspection + plots (returns / correlations).
- `1_Benchmark-bitcoin.ipynb`  
  Bitcoin-only benchmark + performance metrics.
- `1_Benchmark-equal_weights.ipynb`  
  Equal-weight benchmark + performance metrics.
- `2_i_Markowitz_without_x_max.ipynb`  
  Baseline constrained Markowitz (volatility-capped) without concentration cap.
- `2_ii_Markowitz_x_max_only.ipynb`  
  Markowitz + per-asset cap `w_max`.
- `2_iii_Markowitz_LedoitWolf.ipynb`  
  Markowitz + Ledoit–Wolf covariance shrinkage.
- `2_iv_Markowitz_LedoitWolf_D_min.ipynb`  
  Markowitz + Ledoit–Wolf + SOC diversification constraint (`D_min`).
- `main_not_really_useful.ipynb`  
  Extra/legacy notebook (can be moved to `drafts/`).

### Data
The notebooks expect a CSV named `_data.csv` with:
- One row per day
- A `date` column
- One column per asset price (20 assets)



### Report
- `Portfolio_optimization.pdf` 




