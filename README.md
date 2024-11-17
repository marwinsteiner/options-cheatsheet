# Derivatives & Options Formula Cheat Sheet

## Compounding & Interest Rates

### Discrete Compounding
- Future Value = P(1 + r)ᵀ
- Present Value = FV/(1 + r)ᵀ
- P: Principal
- r: Interest rate per period
- T: Number of periods

### Continuous Compounding
- Future Value = P × eʳᵀ
- Present Value = FV × e⁻ʳᵀ
- e: Euler's number (≈ 2.71828)
- r: Continuous interest rate
- T: Time in years

### Converting Between Rates
- Continuous rate = ln(1 + discrete rate)
- Discrete rate = e^(continuous rate) - 1

## Hedging Calculations

### Effective Price Received/Paid
- Long Hedge (Buyer): Effective Price = Spot Price + (Initial Futures - Final Futures)
- Short Hedge (Seller): Effective Price = Spot Price - (Final Futures - Initial Futures)
- Initial Futures: Futures price when hedge initiated
- Final Futures: Futures price when hedge closed out
- Spot Price: Price of underlying when transaction occurs

### Hedge Ratio
- Optimal Hedge Ratio = ρ(σS/σF)
- ρ: Correlation coefficient between spot and futures prices
- σS: Standard deviation of spot price changes
- σF: Standard deviation of futures price changes

## Forward Pricing

### Basic Forward Price (No dividends)
- Discrete: F = S(1 + rₜ)ᵀ
- Continuous: F = Se^(rT)
- F: Forward price
- S: Spot price
- rₜ: Interest rate for period T
- T: Time to maturity

### Forward Price with Known Income
- Discrete: F = (S - I)(1 + rₜ)ᵀ
- Continuous: F = (S - I)e^(rT)
- I: Present value of known income

### Commodity Forward Price
- Discrete: F = (S + U - Y)(1 + rₜ)ᵀ
- Continuous: F = (S + U - Y)e^(rT)
- U: Present value of storage costs
- Y: Present value of convenience yield

### Currency Forward Price
- Discrete: Fₜ = S(1 + rₜ)ᵀ/(1 + rᶠ,ₜ)ᵀ
- Continuous: Fₜ = Se^((r-rᶠ)T)
- rᶠ,ₜ: Foreign interest rate
- S: Current exchange rate

## Options

### Put-Call Parity
- Discrete: S + p = c + K/(1 + r)ᵀ
- Continuous: S + p = c + Ke⁻ʳᵀ
- p: Put premium
- c: Call premium
- K: Strike price

### Option Payoffs at Maturity
- Long Call = max[Sₜ - K, 0]
- Short Call = min[K - Sₜ, 0]
- Long Put = max[K - Sₜ, 0]
- Short Put = min[Sₜ - K, 0]

### Option Profits
- Long Call Profit = max[Sₜ - K, 0] - c
- Short Call Profit = c - max[Sₜ - K, 0]
- Long Put Profit = max[K - Sₜ, 0] - p
- Short Put Profit = p - max[K - Sₜ, 0]

## Binomial Option Pricing

### Replication Method
- Δ = (cᵤ - cᵈ)/((u - d)S)
- N = (dcᵤ - ucᵈ)/(u - d)
- c = ΔS - N/(1 + r)
- cᵤ: Call value if stock goes up
- cᵈ: Call value if stock goes down
- u: Up factor
- d: Down factor

### Risk-Neutral Method
- q = ((1 + r) - d)/(u - d)
- c = [qcᵤ + (1-q)cᵈ]/(1 + r)
- q: Risk-neutral probability

## Option Price Bounds

### European Call Bounds
- max(0, S - Ke⁻ʳᵀ) ≤ c ≤ S

### European Put Bounds
- max(0, Ke⁻ʳᵀ - S) ≤ p ≤ Ke⁻ʳᵀ

### Option Value Components
- Total Value = Intrinsic Value + Time Value
- Intrinsic Value (Call) = max(S - K, 0)
- Intrinsic Value (Put) = max(K - S, 0)
- Time Value = Option Price - Intrinsic Value

## Option States
- In-the-money (Call): S > K
- At-the-money (Call): S = K
- Out-of-the-money (Call): S < K
- In-the-money (Put): K > S
- At-the-money (Put): K = S
- Out-of-the-money (Put): K < S
