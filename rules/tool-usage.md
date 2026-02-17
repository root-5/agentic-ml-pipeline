# Tool Usage Guidelines

## 1. Essential Tools Only
- **Standard Library**: Prefer Python standard libraries whenever possible.
- **Core DS Stack**: pandas, numpy, scikit-learn, matplotlib/seaborn.
- **Avoid Bloat**: Do not introduce heavy frameworks unless absolutely justified by the problem requirements.

## 2. Tool Evalutation
- Before adding a new tool, ask:
    - Does it solve a critical problem?
    - Is the maintenance cost worth the benefit?
    - Is it compatible with the Kaggle environment?

## 3. Version Control
- All tools and libraries should be pinned to specific versions in `requirements.txt` or environment configuration to ensure reproducibility.
