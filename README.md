# Aggregate Equivalence ≠ Behavioral Equivalence: Per-Example Multiplicity in Hybrid Linear Recurrent Models

This repository contains analysis code and data for reproducing the experiments in the paper.

## Requirements

- Python 3.10+
- matplotlib >= 3.7
- numpy >= 1.24
- scipy >= 1.10

Install dependencies:
```bash
pip install -r requirements.txt
```

## Repository Structure

```
├── analysis/          # Analysis scripts
│   ├── sample_characterization.py    # Per-example characterization
│   ├── exp011_convergence_analysis.py # Convergence analysis
│   ├── a2_prediction_framework.py    # Confidence-based prediction
│   └── eval_composition.py           # Evaluation composition
├── figures/           # Figure generation scripts
│   ├── palette.py                    # Shared color palette
│   ├── gen_fig1.py                   # Fig 1: Decoupling hero
│   ├── gen_fig2.py                   # Fig 2: Task specificity
│   ├── gen_fig3_alpha_routing.py     # Fig 3a: Alpha routing
│   ├── gen_fig3_jaccard_heatmap.py   # Fig 3b: Jaccard heatmap
│   ├── gen_fig4_jaccard_saturation.py # Fig 4: Jaccard saturation
│   ├── gen_fig5_per_example_bars.py  # Fig 5: Per-example bars
│   ├── gen_fig_jaccard_hierarchy.py  # Jaccard hierarchy
│   └── gen_fig_method_overview.py    # Method overview
├── data/              # Experiment data (JSON/CSV)
└── requirements.txt
```

## Data

Pre-computed experiment results are provided in `data/`. Models are from the model zoo of Wang et al. (2025).

## Generating Figures

```bash
cd figures
python gen_fig1.py
python gen_fig2.py
# ... etc.
```

Figures are saved as PDF and PNG in the current directory.
