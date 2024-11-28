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

# Binomial Option Pricing Formulas

## Single-Period Model

### Basic Parameters
- $S_0$: Initial stock price
- $u$: Up factor
- $d$: Down factor
- $r$: Risk-free interest rate
- $X$: Strike price
- $T$: Time to maturity

### Risk-Neutral Probability
- $q = \frac{(1 + r) - d}{u - d}$ (Discrete compounding)
- $q = \frac{e^{rT} - d}{u - d}$ (Continuous compounding)

### Option Values at Maturity
- Up state stock price: $S_u = S_0 \times u$
- Down state stock price: $S_d = S_0 \times d$
- Call payoff up: $c_u = \max(S_u - X, 0)$
- Call payoff down: $c_d = \max(S_d - X, 0)$
- Put payoff up: $p_u = \max(X - S_u, 0)$
- Put payoff down: $p_d = \max(X - S_d, 0)$

### Single-Period Option Pricing

#### Discrete Compounding
- Call: $c = \frac{1}{1 + r}[qc_u + (1-q)c_d]$
- Put: $p = \frac{1}{1 + r}[qp_u + (1-q)p_d]$

#### Continuous Compounding
- Call: $c = e^{-rT}[qc_u + (1-q)c_d]$
- Put: $p = e^{-rT}[qp_u + (1-q)p_d]$

## Two-Period Model

### Stock Price Movements
- $S_{uu} = S_0 \times u^2$ (Up-Up)
- $S_{ud} = S_{du} = S_0 \times u \times d$ (Up-Down or Down-Up)
- $S_{dd} = S_0 \times d^2$ (Down-Down)

### Option Values at Maturity
- Call payoffs:
  * $c_{uu} = \max(S_{uu} - X, 0)$
  * $c_{ud} = \max(S_{ud} - X, 0)$
  * $c_{dd} = \max(S_{dd} - X, 0)$
- Put payoffs:
  * $p_{uu} = \max(X - S_{uu}, 0)$
  * $p_{ud} = \max(X - S_{ud}, 0)$
  * $p_{dd} = \max(X - S_{dd}, 0)$

### Two-Period Option Pricing

#### Discrete Compounding
Working backwards:

1. Middle node values (at time T₁):
   - Call up: $c_u = \frac{1}{1 + r}[qc_{uu} + (1-q)c_{ud}]$
   - Call down: $c_d = \frac{1}{1 + r}[qc_{ud} + (1-q)c_{dd}]$
   - Put up: $p_u = \frac{1}{1 + r}[qp_{uu} + (1-q)p_{ud}]$
   - Put down: $p_d = \frac{1}{1 + r}[qp_{ud} + (1-q)p_{dd}]$

2. Initial value (at time 0):
   - Call: $c = \frac{1}{1 + r}[qc_u + (1-q)c_d]$
   - Put: $p = \frac{1}{1 + r}[qp_u + (1-q)p_d]$

#### Continuous Compounding
Working backwards:

1. Middle node values (at time T₁):
   - Call up: $c_u = e^{-r\Delta t}[qc_{uu} + (1-q)c_{ud}]$
   - Call down: $c_d = e^{-r\Delta t}[qc_{ud} + (1-q)c_{dd}]$
   - Put up: $p_u = e^{-r\Delta t}[qp_{uu} + (1-q)p_{ud}]$
   - Put down: $p_d = e^{-r\Delta t}[qp_{ud} + (1-q)p_{dd}]$

2. Initial value (at time 0):
   - Call: $c = e^{-r\Delta t}[qc_u + (1-q)c_d]$
   - Put: $p = e^{-r\Delta t}[qp_u + (1-q)p_d]$

Where $\Delta t = T/n$ is the time step (T/2 for two-period model)

### **Direct Formula** to get from end to beginning value:
1. Discrete Compounding:
   $$c = \frac{1}{1+r^2}(q^2c_{uu} + 2q(1-q)c_{ud} + (1-q)^2c_{dd})$$
   $$p = \frac{1}{1+r^2}(q^2p_{uu} + 2q(1-q)p_{ud} + (1-q)^2p_{dd})$$
3. Continuous Compounding:
   $$c = e^{-2r\Delta t}(q^2c_{uu} + 2q(1-q)c_{ud} + (1-q)^2c_{dd})$$
   $$p = e^{-2r\Delta t}(q^2p_{uu} + 2q(1-q)p_{ud} + (1-q)^2p_{dd})$$

### Delta Hedging Parameters
- $\Delta_{call} = \frac{c_u - c_d}{S_0(u-d)}$
- $\Delta_{put} = \frac{p_u - p_d}{S_0(u-d)}$

### No-Arbitrage Conditions
- $d < 1 + r < u$ (Discrete compounding)
- $d < e^{rT} < u$ (Continuous compounding)

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

## Margin Calculations

### Margin Call Thresholds

For Short Position:
- Margin Call Trigger Price = Initial Price + ((Initial Margin - Maintenance Margin)/(Units × Price per Unit))
- Where:
  * Initial Price = Original futures price
  * Initial Margin = Initial deposit required
  * Maintenance Margin = Minimum required balance
  * Units = Number of units in contract

For Long Position:
- Margin Call Trigger Price = Initial Price - ((Initial Margin - Maintenance Margin)/(Units × Price per Unit))

### Example Calculation
For Q3:
- Initial Price = $0.70
- Initial Margin = $4,000
- Maintenance Margin = $3,000
- Units = 50,000
- Price Change Threshold = ($4,000 - $3,000)/(50,000) = $0.02
- Margin Call Price (Short) = $0.70 + $0.02 = $0.72

Therefore, if futures price rises above $0.72, there will be a margin call.

### General Rules
- Short Position: Margin call when price rises above threshold
- Long Position: Margin call when price falls below threshold
- Loss Threshold = Initial Margin - Maintenance Margin
- Price Move for Margin Call = Loss Threshold ÷ (Units × Price per Unit)

## Daily Price Movement

### Standard Deviation of Daily Price Changes
- $\sigma_{daily} = \sigma_{annual} \times \sqrt{\frac{1}{365}}$
- $\sigma_{daily}$: Daily standard deviation
- $\sigma_{annual}$: Annual volatility

## Black-Scholes Option Pricing Formulas

### Core Equations

#### European Call Option

$c = SN(d_1) - Xe^{-rT}N(d_2)$

#### European Put Option

$p = Xe^{-rT}N(-d_2) - SN(-d_1)$

Where:
$d_1 = \frac{\ln(S/X) + (r + \sigma^2/2)T}{\sigma\sqrt{T}}$

$d_2 = d_1 - \sigma\sqrt{T}$

### Parameters

- $S$ = Current stock price
- $X$ = Strike price
- $r$ = Risk-free interest rate (continuous compounding)
- $T$ = Time to maturity (in years)
- $\sigma$ = Stock price volatility (annual)
- $N(x)$ = Cumulative standard normal distribution function

### Geometric Brownian Motion (GBM)

#### Stock Price Process

$\frac{dS}{S} = \mu dt + \sigma dZ$

#### Distribution Properties

- Returns distribution: $\frac{dS}{S} \sim N(\mu dt, \sigma^2dt)$
- Log price distribution: $\ln(S_T) \sim N[\ln(S_0) + (\mu - \frac{\sigma^2}{2})T, \sigma^2T]$

### Parameter Effects on Option Prices

| Parameter Increase | Call Price | Put Price |
|-------------------|------------|-----------|
| Stock Price ($S$) | ↑          | ↓         |
| Strike Price ($X$)| ↓          | ↑         |
| Volatility ($\sigma$) | ↑      | ↑         |
| Time to Mat. ($T$)| ↑          | ↑         |
| Interest Rate ($r$)| ↑         | ↓         |

### Important Properties

#### American vs European Options

For non-dividend paying stocks:

- American calls = European calls
- American puts > European puts

#### Implied Volatility

- Implied volatility is the value of $\sigma$ that makes the Black-Scholes price equal to the market price
- Used as a measure of market expectations of future volatility
- Often used to quote option prices in markets

#### Model Assumptions

1. No arbitrage opportunities
1. Geometric Brownian motion for stock prices
1. Constant volatility
1. No dividends
1. European exercise
1. Continuous trading


