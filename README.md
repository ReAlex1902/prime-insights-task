# PrimeInsights: Predicting D14 In-App Spend

Case study notebook: predicts `iap_usd_d14` for each install and analyzes
which traffic sources produce valuable vs low-value users.

Funnel modeled: `impression → click → install → playtime / IAP events`.

## Repo contents

```
.
├── primeinsights_case_study_en.ipynb   # the analysis (start here)
├── schema.png                          # table-relationship diagram used in §1.1
├── data/                                # all source tables (see below)
├── requirements.txt
└── .gitignore
```

## Setup

Requires **Python 3.11+** (tested on 3.12.3).

```bash
git clone <this-repo-url>
cd <repo-folder>

python3 -m venv .venv
source .venv/bin/activate      # Windows: .venv\Scripts\activate

pip install -r requirements.txt
```

## Running the notebook

```bash
jupyter notebook primeinsights_case_study_en.ipynb
```

or open the folder in VS Code / JupyterLab and run all cells. The notebook
reads data with the relative path `data/...`, so **run it from the repo
root** (don't move the notebook out of this folder without moving `data/`
and `schema.png` alongside it).

Running top-to-bottom takes a few minutes (LightGBM training with a few
seeds) and, on the last steps, writes `submission.csv` in the repo root —
this file is git-ignored since anyone can regenerate it.

Verified: a fresh `pip install -r requirements.txt` + full run of all 119
cells completes with zero errors on Python 3.12.

## Data

The `data/` folder contains 10 CSV/CSV.GZ tables (installs, offerwall
clicks/impressions, devices, offers, reward tiers, publisher apps, and
playtime events) making up the analytical funnel. Nothing needs to be
downloaded separately — everything the notebook reads ships in this repo.
