# Sustainable ALM & Strategic Asset Allocation Engine

An actuarial **Asset-Liability Management (ALM)** and **Strategic Asset Allocation (SAA)** engine designed for a Defined Benefit (DB) pension fund. The framework optimizes asset allocations across fixed income (matching sleeve) and a 6-company Indian energy equity universe (growth sleeve) under liability duration matching, regulatory capital floors, and decarbonization pathways.

---

## 🚀 Run Interactive Google Colab Notebooks

| Notebook | Focus Area | Link |
| :--- | :--- | :--- |
| **01 Liability Model** | 30-Year Cash Flow Projection & Modified Duration | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/sramantika/sustainable_pension_alm/blob/main/notebooks/01_actuarial_liability_model.ipynb) |
| **02 Asset & ESG Analytics** | Multi-Asset Covariance & Carbon Intensity ($t\text{CO}_2e/\$M$) | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/sramantika/sustainable_pension_alm/blob/main/notebooks/02_asset_covariance_and_esg.ipynb) |
| **03 SAA Optimization** | SciPy Surplus Optimization under Solvency Constraints | [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/sramantika/sustainable_pension_alm/blob/main/notebooks/03_saa_surplus_optimization.ipynb) |

---

## 📊 Core Mathematical Framework

### 1. Actuarial Pension Liability Valuation
$$\text{PV}_L = \sum_{t=1}^{30} \frac{L_0 \cdot (1 + g)^t \cdot (1 + \pi)^t}{(1 + r_t)^t}$$

### 2. Multi-Objective Surplus Optimization
$$\min_{\mathbf{w}} \quad \mathbf{w}^T \boldsymbol{\Sigma}_{\text{Asset}} \mathbf{w} - \lambda \cdot (\mathbf{w}^T \mathbf{\mu}_{\text{Asset}}) + \gamma \cdot (\mathbf{w}^T \mathbf{C}_{\text{Carbon}})$$

**Subject to:**
1. **Regulatory Fixed Income Floor:** $\sum_{i \in \text{Bonds}} w_i \ge 0.55$
2. **Duration Matching Limit:** $|\text{Duration}_{\text{Assets}}(\mathbf{w}) - \text{Duration}_{\text{Liabilities}}| \le 1.5 \text{ years}$
3. **No Shorting:** $w_i \ge 0, \quad \sum w_i = 1$
