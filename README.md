# Reinforcement Learning for Market Making

[![Python 3.8+](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/)
[![PyTorch](https://img.shields.io/badge/Framework-PyTorch-EE4C2C.svg)](https://pytorch.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Status](https://img.shields.io/badge/Status-Completed-success.svg)]()

A comparative study of deep reinforcement learning agents (PPO and SAC) versus the classical Avellaneda-Stoikov analytical benchmark for automated market making in simulated Limit Order Book environments.

---

## Overview

Market making is the practice of simultaneously quoting bid and ask prices to provide liquidity while profiting from the spread. Classical approaches (Avellaneda-Stoikov, 2008) rely on analytical solutions that make strong assumptions about market structure. This project investigates whether **model-free deep RL agents** can learn superior quoting strategies by interacting directly with simulated market environments.

**Core question:** *Can PPO and SAC agents autonomously discover bid-ask quoting policies that outperform the AS analytical benchmark across varying market regimes?*

---

## Methodology

### Algorithms Implemented

| Algorithm | Type | Key Characteristic |
|-----------|------|--------------------|
| **SAC** (Soft Actor-Critic) | Off-policy | Maximum entropy framework; robust to reward shaping |
| **PPO** (Proximal Policy Optimization) | On-policy | Clipped objective; stable training dynamics |
| **Avellaneda-Stoikov** | Analytical Benchmark | Closed-form solution under GBM assumption |

### Market Environments

Three simulated LOB environments of increasing complexity:

1. **Brownian Motion** — Standard GBM mid-price dynamics (baseline)
2. **Jump-Diffusion** — Poisson-distributed price jumps for stress testing
3. **Toxic Order Flow** — Adverse selection pressure from informed traders

### Reward Design

The inventory-adjusted reward function penalizes holding risk:

$$r_t = \Delta \text{PnL}_t - \phi \cdot q_t^2$$

where $q_t$ is the inventory position and $\phi$ is the risk-aversion coefficient.

---

## Results

| Environment | SAC PnL | PPO PnL | AS Benchmark |
|-------------|---------|---------|--------------|
| Brownian Motion | ✅ Outperforms | ≈ Matches | Baseline |
| Jump-Diffusion | ✅ Outperforms | ⚠️ Mixed | Baseline |
| Toxic Flow | ✅ Outperforms | ❌ Underperforms | Baseline |

SAC's maximum entropy objective proved significantly more robust to non-stationary market regimes.

---

## Tech Stack

| Component | Tool |
|-----------|------|
| RL Algorithms | PyTorch (custom implementations) |
| Environment | Custom `gym`-compatible LOB simulator |
| Numerical Computing | NumPy, SciPy |
| Visualization | Matplotlib, Seaborn |

---

## Repository Structure

```
RL-for-Market-Making/
├── environments/       # Custom LOB gym environments
├── agents/             # SAC and PPO implementations
├── notebooks/          # Experiment notebooks and result analysis
├── results/            # Saved model weights and performance logs
└── README.md
```

---

## Background

This project builds upon:
- Avellaneda, M., & Stoikov, S. (2008). *High-frequency trading in a limit order book.* Quantitative Finance, 8(3), 217–224.
- Haarnoja et al. (2018). *Soft Actor-Critic: Off-Policy Maximum Entropy Deep Reinforcement Learning with a Stochastic Actor.*

---

## Author

**Avinash Chauhan** — BS-MS Mathematics, IISER Thiruvananthapuram
