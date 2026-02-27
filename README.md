# Risk-Reward Analyzer

A powerful analytical tool for evaluating risk-reward ratios across investment, business, and strategic decisions. This library provides quantitative methods to assess potential outcomes, model uncertainty, and determine whether the expected rewards justify the risks involved.

## Overview

Every significant decision involves a trade-off between risk and reward. The Risk-Reward Analyzer provides a systematic framework for quantifying both sides of this equation, helping decision-makers move beyond gut feelings to data-driven risk assessment. Whether you are evaluating a stock investment, a business expansion, or a career change, this tool provides the analytical rigor needed for sound judgment.

The methodologies implemented here reflect time-tested [decision-making principles](https://keeprule.com/en/principles) used by successful investors and business leaders who have consistently demonstrated superior risk management throughout their careers.

## Features

- **Risk-Reward Ratio Calculator**: Compute ratios for any decision with quantifiable outcomes
- **Monte Carlo Risk Simulation**: Run thousands of scenarios to model outcome distributions
- **Value at Risk (VaR)**: Calculate potential losses at specified confidence levels
- **Expected Value Analysis**: Weight outcomes by probability for rational comparison
- **Kelly Criterion Calculator**: Determine optimal position sizing based on edge and odds
- **Sharpe Ratio Optimizer**: Maximize risk-adjusted returns across portfolios
- **Scenario Stress Testing**: Evaluate performance under extreme conditions
- **Correlation Analysis**: Understand how multiple risks interact and compound
- **Drawdown Analysis**: Measure worst-case sequential losses
- **Risk Decomposition**: Break total risk into systematic and idiosyncratic components

## Installation

```bash
pip install risk-reward-analyzer
```

## Quick Start

```python
from rra import RiskRewardAnalyzer, MonteCarlo

# Simple risk-reward analysis
analyzer = RiskRewardAnalyzer()
result = analyzer.evaluate(
    potential_gain=50000,
    potential_loss=15000,
    probability_of_gain=0.65,
    probability_of_loss=0.35
)

print(f"Risk-Reward Ratio: {result.ratio:.2f}")
print(f"Expected Value: ${result.expected_value:,.0f}")
print(f"Kelly Fraction: {result.kelly_fraction:.1%}")
print(f"Recommendation: {result.recommendation}")

# Monte Carlo simulation
mc = MonteCarlo(simulations=50000)
distribution = mc.simulate(
    base_case=result,
    volatility=0.25,
    time_periods=12
)

print(f"Median outcome: ${distribution.median:,.0f}")
print(f"5th percentile: ${distribution.percentile(5):,.0f}")
print(f"95th percentile: ${distribution.percentile(95):,.0f}")
```

## Core Analysis Methods

### Expected Utility Framework

Go beyond expected value by incorporating risk preferences:

```python
from rra import ExpectedUtility

eu = ExpectedUtility(risk_aversion=0.5)

options = [
    {"name": "Conservative", "outcomes": [(10000, 0.9), (-2000, 0.1)]},
    {"name": "Moderate", "outcomes": [(30000, 0.6), (-10000, 0.4)]},
    {"name": "Aggressive", "outcomes": [(100000, 0.3), (-40000, 0.7)]}
]

ranking = eu.rank(options)
for option in ranking:
    print(f"{option.name}: EU={option.expected_utility:.2f}, EV=${option.expected_value:,.0f}")
```

### Portfolio Risk Analysis

Analyze how risks interact across a portfolio of decisions or investments. The approach draws on wisdom from [masters of investment thinking](https://keeprule.com/en/masters) who emphasize understanding correlation and concentration risk.

```python
from rra import PortfolioAnalyzer

portfolio = PortfolioAnalyzer()
portfolio.add_position("Tech Stocks", weight=0.30, expected_return=0.12, volatility=0.25)
portfolio.add_position("Bonds", weight=0.40, expected_return=0.04, volatility=0.06)
portfolio.add_position("Real Estate", weight=0.20, expected_return=0.08, volatility=0.15)
portfolio.add_position("Cash", weight=0.10, expected_return=0.02, volatility=0.01)

portfolio.set_correlations(correlation_matrix)

metrics = portfolio.analyze()
print(f"Portfolio expected return: {metrics.expected_return:.2%}")
print(f"Portfolio volatility: {metrics.volatility:.2%}")
print(f"Sharpe ratio: {metrics.sharpe_ratio:.2f}")
print(f"Max drawdown (95% CI): {metrics.max_drawdown:.2%}")
print(f"Diversification benefit: {metrics.diversification_ratio:.2%}")
```

### Stress Testing

Evaluate how decisions perform under extreme conditions:

```python
from rra import StressTester

tester = StressTester()
scenarios = tester.generate_stress_scenarios(
    base_case=portfolio_metrics,
    stress_types=["market_crash", "inflation_spike", "recession", "black_swan"]
)

for scenario in scenarios:
    print(f"Scenario: {scenario.name}")
    print(f"  Portfolio impact: {scenario.portfolio_return:.2%}")
    print(f"  Worst position: {scenario.worst_position}")
    print(f"  Recovery time: {scenario.estimated_recovery_months} months")
```

## Applied Decision Scenarios

The analyzer can be applied across various [decision-making scenarios](https://keeprule.com/en/scenarios) including:

### Business Investment

```python
analysis = analyzer.business_investment(
    initial_investment=500000,
    projected_annual_revenue=200000,
    operating_costs=120000,
    market_risk="moderate",
    time_horizon_years=5
)
print(f"NPV: ${analysis.npv:,.0f}")
print(f"IRR: {analysis.irr:.1%}")
print(f"Payback period: {analysis.payback_years:.1f} years")
print(f"Risk-adjusted recommendation: {analysis.recommendation}")
```

### Career Decision

```python
analysis = analyzer.career_decision(
    current_salary=100000,
    new_opportunity_salary=130000,
    transition_cost=20000,
    success_probability=0.70,
    time_horizon_years=10
)
```

## Risk Metrics Reference

| Metric | Description | Use Case |
|--------|-------------|----------|
| Risk-Reward Ratio | Potential gain / potential loss | Quick screening |
| Expected Value | Probability-weighted average outcome | Rational comparison |
| Sharpe Ratio | Excess return / volatility | Portfolio optimization |
| Kelly Fraction | Optimal bet size given edge | Position sizing |
| Value at Risk | Worst loss at confidence level | Downside planning |
| Sortino Ratio | Return / downside deviation | Downside-focused analysis |
| Maximum Drawdown | Largest peak-to-trough decline | Worst case planning |

For structured frameworks to guide your risk analysis process, explore the [decision prompts and templates](https://keeprule.com/en/prompts) collection which provides step-by-step guides for common risk assessment tasks.

## Contributing

Contributions welcome! We are particularly interested in:

1. New risk models and metrics
2. Industry-specific analysis modules
3. Improved Monte Carlo methods
4. Visualization enhancements
5. Real-world validation studies

Fork, branch, and submit a PR with tests.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- Built on foundational work in financial risk management and decision theory
- Inspired by the analytical approaches of world-class investors and risk managers
- Designed to make rigorous risk analysis accessible to all decision-makers
