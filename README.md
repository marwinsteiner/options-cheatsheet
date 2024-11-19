# Derivatives & Options Formula Cheat Sheet

## Compounding & Interest Rates

### Discrete Compounding
- Future Value = $P(1 + r)^T$
- Present Value = $\frac{FV}{(1 + r)^T}$
- $P$: Principal
- $r$: Interest rate per period
- $T$: Number of periods

### Continuous Compounding
- Future Value = $P \times e^{rT}$
- Present Value = $FV \times e^{-rT}$
- $e$: Euler's number (≈ 2.71828)
- $r$: Continuous interest rate
- $T$: Time in years

### Converting Between Rates
- Continuous rate = $\ln(1 + \text{discrete rate})$
- Discrete rate = $e^{\text{continuous rate}} - 1$

## Hedging Calculations

### Effective Price Received/Paid
- Long Hedge (Buyer): $\text{Effective Price} = \text{Spot Price} + (\text{Initial Futures} - \text{Final Futures})$
- Short Hedge (Seller): $\text{Effective Price} = \text{Spot Price} - (\text{Final Futures} - \text{Initial Futures})$

### Hedge Ratio
- Optimal Hedge Ratio = $\rho(\sigma_S/\sigma_F)$
- $\rho$: Correlation coefficient between spot and futures prices
- $\sigma_S$: Standard deviation of spot price changes
- $\sigma_F$: Standard deviation of futures price changes

### Index Futures Hedge
- Number of contracts = $\frac{\beta_P}{(\beta_F \times F \times M)}$
- $P$: Value of portfolio to be hedged
- $\beta_P$: Beta of portfolio
- $\beta_F$: Beta of futures (usually 1.0)
- $F$: Futures price
- $M$: Contract multiplier

## Forward Pricing

### Basic Forward Price (No dividends)
- Discrete: $F = S(1 + r_t)^T$
- Continuous: $F = Se^{rT}$
- $F$: Forward price
- $S$: Spot price
- $r_t$: Interest rate for period $T$
- $T$: Time to maturity

### Forward Price with Known Income
- Discrete: $F = (S - I)(1 + r_t)^T$
- Continuous: $F = (S - I)e^{rT}$
- $I$: Present value of known income

### Commodity Forward Price
- Discrete: $F = (S + U - Y)(1 + r_t)^T$
- Continuous: $F = (S + U - Y)e^{rT}$
- $U$: Present value of storage costs
- $Y$: Present value of convenience yield

### Currency Forward Price
- Discrete: $F_t = S\frac{(1 + r_t)^T}{(1 + r_{f,t})^T}$
- Continuous: $F_t = Se^{(r-r_f)T}$
- $r_{f,t}$: Foreign interest rate
- $S$: Current exchange rate

## Options

### Put-Call Parity
- Discrete: $S + p = c + \frac{K}{(1 + r)^T}$
- Continuous: $S + p = c + Ke^{-rT}$
- $p$: Put premium
- $c$: Call premium
- $K$: Strike price

### Option Payoffs at Maturity
- Long Call = $\max[S_T - K, 0]$
- Short Call = $\min[K - S_T, 0]$
- Long Put = $\max[K - S_T, 0]$
- Short Put = $\min[S_T - K, 0]$

### Option Profits
- Long Call Profit = $\max[S_T - K, 0] - c$
- Short Call Profit = $c - \max[S_T - K, 0]$
- Long Put Profit = $\max[K - S_T, 0] - p$
- Short Put Profit = $p - \max[K - S_T, 0]$

## Binomial Option Pricing

### Risk-Neutral Probability
- $q = \frac{(1 + r) - d}{u - d}$
- $u$: Up factor
- $d$: Down factor
- $r$: Risk-free rate

### Option Value
- $c = \frac{[qc_u + (1-q)c_d]}{1 + r}$
- $c_u$: Call value if stock goes up
- $c_d$: Call value if stock goes down

### Delta Hedging
- $\Delta = \frac{c_u - c_d}{(u - d)S}$
- $N = \frac{dc_u - uc_d}{u - d}$

## Option Price Bounds

### European Call Bounds
- $\max(0, S - Ke^{-rT}) \leq c \leq S$

### European Put Bounds
- $\max(0, Ke^{-rT} - S) \leq p \leq Ke^{-rT}$

### Option Value Components
- Total Value = Intrinsic Value + Time Value
- Intrinsic Value (Call) = $\max(S - K, 0)$
- Intrinsic Value (Put) = $\max(K - S, 0)$
- Time Value = Option Price - Intrinsic Value

## Daily Price Movement

### Standard Deviation of Daily Price Changes
- $\sigma_{daily} = \sigma_{annual} \times \sqrt{\frac{1}{365}}$
- $\sigma_{daily}$: Daily standard deviation
- $\sigma_{annual}$: Annual volatility
