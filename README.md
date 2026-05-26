# Aggregate Equivalence ≠ Behavioral Equivalence: Per-Example Multiplicity in Hybrid Linear Recurrent Models

## Abstract

Hybrid linear recurrent architectures that appear interchangeable by aggregate benchmarks can differ on which specific examples they handle correctly. Using a controlled model zoo (Wang et al., 2025) spanning three architectures, five attention ratios, and two scales, we decompose per-example effects of adding attention and find structured predictive multiplicity (Marx et al., 2020): pairwise overlap of helped and hurt example sets is uniformly low (Jaccard ≤ 0.14, roughly twice the independence baseline; all p < .01 across five architectures). This multiplicity varies by task type or evaluation format (α = 0.14–0.30) rather than attention ratio. Per-example overlap appears to stabilize at 4% attention and remains flat across higher ratios, suggesting that minimal attention may establish which examples each architecture affects. Confidence margins partially predict affected examples (AUC 0.70–0.74). Low cross-architecture overlap implies substantial complementarity, though routing-based exploitation remains task-dependent.

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
├── data/              # Pre-computed experiment data (JSON/CSV)
└── requirements.txt
```

## Data

Pre-computed experiment results are provided in `data/`. Models are from the controlled model zoo of Wang et al. (2025), which holds training data, tokenizer, and hyperparameters constant across three recurrent architectures (GatedDeltaNet, RetNet, HGRN2) at five attention ratios (0%, 4%, 7.7%, 14.3%, 25%) and two scales (340M, 1.3B). Extended validation includes GLA and DeltaNet at 340M.

Benchmarks: LAMBADA (N=5,153), HellaSwag (N=10,042), PIQA (N=1,838), ARC-Easy (N=2,376), plus supplementary analyses on BoolQ and WinoGrande.

## Generating Figures

```bash
cd figures
python gen_fig1.py
python gen_fig2.py
python gen_fig3_alpha_routing.py
python gen_fig3_jaccard_heatmap.py
python gen_fig4_jaccard_saturation.py
python gen_fig5_per_example_bars.py
python gen_fig_jaccard_hierarchy.py
python gen_fig_method_overview.py
```

Figures are saved as PDF and PNG in the current directory.

## Analysis

```bash
cd analysis
python sample_characterization.py      # Per-example helped/hurt decomposition
python exp011_convergence_analysis.py   # Cross-architecture convergence vs attention ratio
python a2_prediction_framework.py       # Confidence-based prediction of attention effects
python eval_composition.py              # Evaluation composition analysis
```
