# auto_callable_option


An Auto-Callable Option is a structured financial product that can be automatically terminated ("called") before its maturity date if certain predefined conditions are met. These conditions are typically based on the performance of an underlying asset, such as a stock or index. If the underlying asset's price reaches or exceeds a specified barrier level at certain observation dates, the option is automatically exercised, and the investor receives a predefined payout.



Underlying Asset (S): The financial asset on which the option is based (e.g., a stock, index).
Strike Price (K): The price at which the option can be exercised at maturity.
Call Barrier (B): A predetermined price level of the underlying asset that triggers the automatic exercise of the option.
Coupon Rate (c): The rate at which the investor receives payments if the option is called early.
Maturity (T): The time until the option expires.
Risk-Free Rate (r): The theoretical rate of return on an investment with zero risk, used in pricing models.
Volatility (sigma): The measure of the underlying asset's price fluctuations over time.
Time Steps (n): The number of time intervals used in simulating the price path.


Price Path Simulation: The price of the underlying asset is often modeled using Geometric Brownian Motion (GBM):
dS_t = r * S_t * dt + sigma * S_t * dW_t
Where:
dS_t is the change in price at time t.
S_t is the price of the underlying asset at time t.
r is the risk-free interest rate.
sigma is the volatility.
dW_t is a Wiener process (random term).

The discrete version of this for simulations is:
S_{t+dt} = S_t * exp((r - 0.5 * sigma^2) * dt + sigma * sqrt(dt) * Z_t)
Where:
dt is the time step.
Z_t is a standard normal random variable.

Auto-Call Condition: The option is automatically called if, at any observation date t_j where j is an index for observation dates, the underlying asset's price S_{t_j} exceeds the call barrier B:
Auto-Call if S_{t_j} >= B

Payoff Calculation:
1) If Called Early: The investor receives a payoff based on the coupon rate and the time elapsed:
Payoff = c * (t_j / T)
2) If Not Called: The investor receives the payoff at maturity, which could be the intrinsic value:
Payoff = max(S_T - K, 0)
Where S_T is the price of the underlying asset at maturity.
