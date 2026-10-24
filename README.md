# Replication package

**Machine-Learning Prediction of Corporate Financial Performance Using ESG and Governance Data: An Incremental, Out-of-Sample Approach**

Yasean Tahat, Yara Ibrahim (corresponding author), Ahmed Hassanein

This repository contains the analysis code and supporting materials needed to reproduce the
results in the paper from a licensed data extract. It accompanies the manuscript submitted to
*Data* (MDPI).

## What this study does

The study evaluates whether environmental, social and governance (ESG) and corporate-governance
information provides incremental out-of-sample predictive information for one-period-ahead return
on assets (ROA) in a panel of 373 European listed firms, over fiscal years 2012–2023, beyond
conventional financial predictors. Four model classes (elastic net, random forest, extremely
randomized trees, histogram gradient boosting) are compared across three nested information sets
under a temporally ordered train/validation/test split.

## Repository contents

| File | Description |
|------|-------------|
| `reproduction_notebook.ipynb` | Regenerates the benchmark, test and diagnostic analyses (naive persistence and AR(1) benchmarks, nested ExtraTrees pipeline, Diebold–Mariano test, held-out split-conformal recalibration, complete-case check, Table E1 chronological split, and verification of the descriptive statistics). |
| `firm_identifiers.csv` | The 373 sample firms: Reuters Instrument Code (RIC), company name, country of headquarters, and ICB industry. |
| `field_definitions.md` | Exact LSEG/Refinitiv field definitions for every variable used. |
| `requirements.txt` | Python dependencies. |
| `LICENSE` | MIT licence (covers the code in this repository). |

## Data availability

The firm-level data are licensed from **LSEG/Refinitiv** (Datastream accounting and market
fundamentals combined with Refinitiv ESG, formerly ASSET4, pillar and category scores) and
**cannot be redistributed**. Researchers with an LSEG/Refinitiv subscription can reconstruct the
extract from the firm identifiers in `firm_identifiers.csv` and the field definitions in
`field_definitions.md`. Place the resulting workbook next to the notebook as
`Cleaned_GridExport_March_27_2023.xlsx` before running.

## How to run

```bash
python -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate
pip install -r requirements.txt
jupyter notebook reproduction_notebook.ipynb
```

Run the cells top to bottom. All pipelines use a fixed random seed (42). The tuned four-algorithm
pipeline that produces the manuscript tables uses the same preprocessing and temporal split shown
in the notebook; the deposited pipeline reproduces the reported headline metrics to within about
0.001 in MAE.

## Citation

If you use this code, please cite the paper and this repository. A DOI will be minted on deposit
(for example via Zenodo) and added here.
