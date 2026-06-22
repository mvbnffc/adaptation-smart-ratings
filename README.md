# Code for "Modelling the impact of physical climate risk and adaptation on sovereign credit ratings"

A probabilistic modelling framework for estimating how river flooding, climate
change, and adaptation investments can affect Thailand's macroeconomy and
sovereign credit rating.

![Projected downgrade probabilities with and without adaptation](assets/Figure_1.jpg)

<p align="center">
  <img src="assets/Figure_5.png" alt="Figure 5: Projected downgrade probabilities with and without adaptation" width="800">
</p>

## Model Overview

The model links river-flood risk, macroeconomic shocks, and sovereign credit
ratings for Thailand. It simulates many possible flood years under current and
future climate scenarios, compares baseline protection with adaptation, and
tracks impacts through the chain:

1. flood hazard, exposure, and vulnerability;
2. basin-level capital and output losses;
3. DIGNAD macroeconomic impacts; and
4. sovereign rating, default-risk, and borrowing-cost outcomes.

## Running the Code

Create the Python environment from the repository root:

```bash
conda env create -f environment.yml
conda activate sovereign-risk
pip install -e .
```

Then open the notebooks from the repository root:

```bash
jupyter notebook
```

The main paper workflow is:

1. `notebooks/preparation/`
2. `notebooks/pre_sim/`
3. `notebooks/paper_analysis/full_simulation.ipynb`
4. `notebooks/paper_analysis/validation_2011_floods.ipynb`
5. `notebooks/paper_analysis/results_and_figures.ipynb`

Some notebooks depend on files produced by earlier notebooks. The full pipeline
also requires input data, generated output caches, MATLAB, and the IMF DIGNAD
toolkit, which are not stored in this code repository.

## Reproducing Figures

To reproduce the final paper figures from archived model outputs, run:

```text
notebooks/paper_analysis/results_and_figures.ipynb
```

Figure 5, shown above, is produced by this notebook from the final model output
file `outputs/results/full_model_simulation.csv`.

## Reproducibility Repositories

Separate repositories for different levels of reproducibility will be created
for publication:

- code record: this repository
- figure reproduction: archived outputs needed to regenerate tables and figures
- results reproduction: prepared inputs and selected pre-computed outputs
- full pipeline reproduction: source inputs and all intermediate data required
  to rebuild the analysis

The final DOI or repository links will be added here once they are available.

## Repository Contents

- `sovereign/`: reusable Python functions for flood risk, DIGNAD coupling, and
  credit-risk analysis
- `notebooks/preparation/`: input preparation notebooks
- `notebooks/pre_sim/`: expensive pre-simulation notebooks
- `notebooks/paper_analysis/`: final simulation, validation, and figure notebooks
- `assets/`: README and publication-facing assets

Local `inputs/`, `outputs/`, and `DIGNAD/` directories are intentionally ignored
by Git.

## System Requirements

This code was developed with Python 3.11. The Conda environment installs the
geospatial and scientific Python dependencies used by the notebooks, including
`geopandas`, `rasterio`, `xarray`, `cfgrib`, `scipy`, `scikit-learn`,
`openpyxl`, `matplotlib`, and `seaborn`.

The DIGNAD-linked parts of the workflow require:

- MATLAB available on `PATH`
- IMF DIGNAD toolkit at `DIGNAD/DIGNAD_Toolkit/`
- the Thailand-calibrated `input_DIG-ND.xlsx` workbook supplied with the
  reproducibility materials

## Citation

Citation details will be added when the paper is published.

## Licence

This repository is released under the MIT Licence. See `LICENSE` for details.
