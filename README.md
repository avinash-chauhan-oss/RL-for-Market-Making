# Reinforcement Learning for Market Making

## Overview
This project studies market making as a reinforcement learning problem and investigates whether RL agents can outperform the classical Avellaneda-Stoikov analytical benchmark. 

By implementing continuous-control algorithms—specifically Proximal Policy Optimization (PPO) and Soft Actor-Critic (SAC)—this repository explores how agents learn optimal bid-ask quoting strategies to manage stochastic inventory risk across multiple simulated market environments.

## Key Features
* **Continuous Action Space:** Dynamic control for optimal bid-ask spread placement.
* **Algorithm Implementation:** Custom environments trained using PPO and SAC.
* **Baseline Benchmarking:** Direct comparative analysis against the Avellaneda-Stoikov model.
* **Volatility Testing Environments:**
  * Brownian motion (Standard baseline)
  * Jump-diffusion (Stress testing)
  * Toxic order flow scenarios (Adverse selection)

## Results & Findings
* Both PPO and SAC demonstrate highly adaptive quoting behavior during volatile regimes.
* The RL agents successfully outperform the rigid Avellaneda-Stoikov benchmark in simulated environments with non-linear order flow.
* The SAC agent exhibits superior robustness and sample efficiency under noisy, non-stationary market conditions.

## Repository Structure

```text
├── notebooks/
│   ├── PPO.ipynb                 # PPO training and evaluation
│   ├── SAC.ipynb                 # SAC implementation and inventory risk modeling
│   └── Other_Comp_Algorithms.ipynb
├── report/
│   └── rl_market_making.pdf      # Comprehensive final research paper
├── results/                      # Generated PnL plots and spread behavior metrics
└── README.md
