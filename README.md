# Outcome Selection with Algorithmic Learners

**Working Paper** — Mateus Hiro Nagata & Francesco Giordano  
HEC Paris, Economics and Decision Sciences  
*Preliminary Draft — July 2025*

---

## 📘 Overview

This repository contains the reproduction package for the working paper *"Outcome Selection with Algorithmic Learners"*.

We study whether it is possible to nudge independent reinforcement learning algorithms towards welfare-improving outcomes in repeated games. The core idea is to augment standard learning dynamics — specifically, **Correlated Hedge** (a variant of Multiplicative Weights / stateless Q-learning) — with a **correlation device**: a mediator that sends payoff-irrelevant messages to players before each round.

Messages can be **public** (shared by all players) or **private** (player-specific). The probability distribution over messages is either **fixed** or **time-varying** according to a welfare criterion. We ask:

- Do algorithms learn desirable correlated equilibria when guided by messages?
- Does information improve welfare and fairness when algorithms compete?

We provide a partial answer based on simulations across several classes of repeated simultaneous-move games.

---

## 🔑 Key Contributions

- **Correlated Hedge algorithm**: an augmentation of standard Hedge/MWU where Q-values and mixed strategies are conditioned on private messages drawn from a joint distribution.
- **Analytical results**: continuous-time ODE characterization of the learning dynamics (Lemma 1 & 2); equivalence between fixed points and Per-signal Quantal Correlated Equilibrium (Proposition 2); stability conditions linking fixed points to correlated equilibria (Proposition 1).
- **Price of Learning (PoL)**: a new concept — analogous to Price of Anarchy — measuring welfare loss due to learning relative to the theoretically optimal social welfare.
- **Adaptive designer theory**: a framework where the information designer itself uses a learning algorithm to adjust the message distribution over time.
- **Simulation results**: convergence analysis across Hawk-Dove, Coordination, 2×3, 3×2, and 3×3 games.

---

## 📁 Repository Structure

```
├── code/
│   ├── 01_baseline_qlearning.ipynb          # Baseline Hedge algorithm (no messages)
│   ├── 02_public_messages.ipynb             # Correlated Hedge with public messages (Section 3)
│   ├── 03_private_messages.ipynb            # Correlated Hedge with private messages (Section 3)
│   ├── 04_adaptive_messages.ipynb           # Adaptive message distribution (Section 4.1)
│   └── 05_prototype_exploration.ipynb       # Parameter exploration and robustness checks
├── output/
│   ├── figures/                             # Generated heatmaps and convergence plots
│   └── tables/                             # Results tables
└── README.md
```

---

## 🗂️ Notebook Guide

| Notebook | Description | Paper Section |
|---|---|---|
| `01_baseline_qlearning.ipynb` | Baseline Hedge algorithm without messages, used as benchmark | §2 |
| `02_public_messages.ipynb` | Correlated Hedge with public messages; produces heatmaps of convergence to correlated equilibrium vs. Nash across (α, β) grid | §3 |
| `03_private_messages.ipynb` | Correlated Hedge with private messages; key result on welfare-improving equilibrium selection | §3 |
| `04_adaptive_messages.ipynb` | Information designer updates message distribution dynamically using a Hedge-style rule on observed welfare | §4.1 |
| `05_prototype_exploration.ipynb` | Decreasing exploration (β increasing over time), alternative parametrizations | §4 |

> **Note:** `02_public_messages.ipynb` takes **more than 4 hours** to run the full (α, β) grid (100 × 11 combinations, 100 simulations each).

---

## ⚙️ Setup & Requirements

All data comes from simulations — **no external dataset is required**.

```bash
pip install numpy scipy matplotlib seaborn jupyter
```

To run the notebooks:

```bash
jupyter notebook
```

---

## 🎮 Games Studied

| Game | Type | Key Finding |
|---|---|---|
| Hawk-Dove | 2×2, symmetric | With baseline η, ~10% convergence to obedient correlated equilibrium (α=0); theoretically optimal η′ rarely induces obedience |
| Coordination | 2×2, asymmetric | Messages enable alternation between pure Nash equilibria, improving fairness |
| 2×3 Rock-Paper-Scissors variant | 2-player | Adaptive messages improve average welfare at intermediate iteration ranges |
| 3×2 game | 3-player | Public messages between players 1 & 2 improve both welfare and fairness |
| 3×3 game | 3-player | Mild improvements for some hyperparameter configurations |

---

## 📊 Main Results

**Result 1.** Under message distribution η (non-optimal, higher incentive compatibility), algorithms converge to the obedient correlated equilibrium ~10% of the time when α = 0; the remaining ~90% converges to pure Nash.

**Result 2.** Under the theoretically welfare-optimal distribution η′, convergence to obedience is near zero — algorithms almost always converge to pure Nash instead.

**Result 3.** Convergence to correlated equilibrium is governed by the ratio α/β (memory-loss vs. exploitation intensity), producing a staircase structure in the parameter space.

**Result 4 (Price of Learning).** Theoretically optimal information design does not guarantee obedience. The induced welfare of η surpasses η′ in practice: SW_η = 9.3 vs. SW_η′ = 9.0.

---

## 📄 Citation

If you use this code or build on these results, please cite:

> Giordano, F. & Nagata, M.H. (2025). *Outcome Selection with Algorithmic Learners*. Working Paper, HEC Paris.

---

## 🪪 License

This project is released under the [MIT License](LICENSE).

---

## 📬 Contact

- Francesco Giordano — HEC Paris, Economics and Decision Sciences
- Mateus Hiro Nagata — HEC Paris, Economics and Decision Sciences
