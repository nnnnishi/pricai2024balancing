# Balancing Revenue Goals and Off-Policy Evaluation Performance in Coupon Allocation

This repository contains the code to reproduce the synthetic data experiments from the paper "Balancing Revenue Goals and Off-Policy Evaluation Performance in Coupon Allocation". 

## Overview

We propose a novel approach to balance the tradeoff between revenue goals and off-policy evaluation performance in coupon allocation by combining model-based deterministic and probabilistic policies. The optimal policy mixture ratio is formulated as a multi-objective optimization problem.

Experiments on synthetic data demonstrate that, compared to using a single policy, the proposed method simultaneously achieves efficient data collection for future policy improvement and near-optimal revenue acquisition. 

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
author={Anonymous},
booktitle={Anonymous Conference},
year={2024}
}
```
## License
This project is licensed under the MIT License.