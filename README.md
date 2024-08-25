# Balancing Revenue Goals and Off-Policy Evaluation Performance in Coupon Allocation

This repository contains the code to reproduce the synthetic data experiments from our paper "Balancing Revenue Goals and Off-Policy Evaluation Performance in Coupon Allocation", which has been accepted for publication in the Proceedings of the 21st Pacific Rim International Conference on Artificial Intelligence (PRICAI 2024).

## Overview

We propose a novel approach to balance the tradeoff between revenue goals and off-policy evaluation performance in coupon allocation by combining model-based deterministic and probabilistic policies. The optimal policy mixture ratio is formulated as a multi-objective optimization problem.

Experiments on synthetic data demonstrate that, compared to using a single policy, the proposed method simultaneously achieves efficient data collection for future policy improvement and near-optimal revenue acquisition. 

## Experimental Setup

### Data Generation Process

- Synthetic dataset with 10,000 users
- Each user j has a 4-dimensional feature vector x_j = (x_j,1, x_j,2, x_j,3, x_j,4)
  - Each x_j,d ~ Uniform(0,1)
- Action space: a ∈ {0,1}^|J|
  - a_j = 1: coupon allocated to user j
  - a_j = 0: no coupon allocated
- Noise terms: ε_j,0, ε_j,1 ~ N(0,1) i.i.d. for each user
- Revenue functions:
  $$r_j(x_j, 0) = ε_{j,0}$$
  $$r_j(x_j, 1) = 1 x_{j,2} + 1 x_{j,3} + ε_{j,1}$$

## Data Collection and Evaluation Policies

### Data Collection Policies
- π_1: random allocation using x_j,1 as probability
- π_2: deterministic, allocate when x_j,2 ≥ 0.5
- π_3: deterministic, allocate when x_j,3 ≥ 0.5

Mixture ratios: α_1, α_2, α_3

### Evaluation Policies
- π_e,1: positively correlated with π_2
  - P(allocate) = 0.8 when x_j,2 ≥ 0.5
  - P(allocate) = 0.2 when x_j,2 < 0.5
- π_e,2: negatively correlated with π_2
  - P(allocate) = 0.2 when x_j,2 ≥ 0.5
  - P(allocate) = 0.8 when x_j,2 < 0.5

### Performance Metrics

#### Revenue Metric
$$f^r(α) = V(π̄_{1:K}) = \frac{1}{n}\sum_{i=1}^K\sum_{j=1}^{n_i}r_j(x_j^{(i)}, h_i(x_j^{(i)}))$$

#### OPE Performance Metric
$$f^e(α) = (V(π_e) - \hat{V}_{\text{BIPS}}(π_e))^2$$

### Optimization

- Tool: Optuna v3.6.0
- Algorithm: NSGA-II (default in Optuna)
- Trials: 1,000 per experiment

## Repository Contents

- `synthetic_experiments.ipynb`: Generates the synthetic datasets, runs the synthetic data experiments and generates result plots
- `results/`: Folder where experiment results and plots are saved
- `requirements.txt`: Lists the required Python dependencies

## Setup

1. Clone this repository
2. Install the required packages:

pip install -r requirements.txt

## Running Experiments 

1. Open and run the `synthetic_experiments.ipynb` Jupyter notebook

The notebook will generate synthetic data, optimize the policy mixture ratios, evaluate the policies, and plot the results. Figures will be saved to the `results/` directory.

## Citing

If you use this code in your research, please cite our paper:

```bibtex
@inproceedings{anonymous2024balancing,
title={Balancing Revenue Goals and Off-Policy Evaluation Performance in Coupon Allocation},
author={Nishimura, Naoki and Kobayashi, Ken and Nakata, Kazuhide},
booktitle={Proceedings of the 21st Pacific Rim International Conference on Artificial Intelligence},
pages={TBD},
year={2024},
organization={Springer}
}
```
## License
This project is licensed under the MIT License.