# PBS Antibiotics project
PBS Antibiotics — Australia (2015)
Beginner-friendly analysis of antibiotic prescribing using Australian PBS (Pharmaceutical Benefits Scheme) data and ABS population to compute scripts per 1,000 people and plot simple trends.

Skills I practised: data cleaning from messy CSVs, date parsing, grouping/aggregation, and clear visualisation with pandas + matplotlib.


Data
PBS ATC 2015 (national) — public release with ATC classifications and services.
Dataset page: Pharmaceutical Benefits Scheme (PBS) – Anatomical Therapeutic Chemical report on [https://data.gov.au/data/dataset/pharmaceutical-benefits-scheme-pbs-anatomical-therapeutic-chemical-report/resource/2eab7fa1-2a7b-4e32-ad7a-6188f6762fc5]

ABS population (ERP) — national Estimated Resident Population time series.
Dataset page: National, state and territory population on [https://www.abs.gov.au/AUSSTATS/abs@.nsf/DetailsPage/3101.0Sep%202015?OpenDocument]

To keep the repo light, I don’t commit large raw CSVs. Place your downloads locally under data/raw/ before running.

What I did
Loaded ABS population CSV, detected the ERP (Australia) column and monthly dates, and extracted 2015 ERP (auto-scaling if values were reported in thousands).

Loaded PBS 2015 CSV, parsed month/year, and identified antibiotic classes (ATC codes starting with J01).

If J01 wasn’t clearly labelled, the notebook falls back to all PBS rows in 2015 so charts still render.

Calculated scripts per 1,000 people using the 2015 ERP.


Plotted:

Average scripts per 1,000 by month (2015)

Top 5 antibiotic classes (2015, scripts/1,000)

Cumulative scripts per 1,000 (2015)


How to run the notebook
Option A — Jupyter Notebook
python -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate
pip install jupyter pandas matplotlib
jupyter notebook
# In the browser, open notebooks/analysis_simple.ipynb and Run All

Option B — VS Code
Open the folder in VS Code → install the Python + Jupyter extensions.

Select your .venv interpreter, open notebooks/analysis_simple.ipynb, and Run All.

Place your raw CSVs before running:

data/raw/pbs-atc-2015.csv
data/raw/population_sample.csv
Outputs:

Cleaned CSVs → data/cleaned/

Figures → figures/

Notes & assumptions
ABS ERP can be reported in thousands; the notebook auto-scales to persons when needed.

If J01 antibiotics cannot be detected from the PBS file, charts use all PBS rows for 2015 (a clear note is printed).

This is a learning project; figures are illustrative, not official statistics.


License / attribution
Code: MIT.
Data belongs to ABS and PBS — please refer to the original dataset licences.

PBS Antibiotics — Australia (2015)
Beginner-friendly analysis of antibiotic prescribing using Australian PBS (Pharmaceutical Benefits Scheme) data and ABS population to compute scripts per 1,000 people and plot simple trends.

Skills I practised: data cleaning from messy CSVs, date parsing, grouping/aggregation, and clear visualisation with pandas + matplotlib.



Data
PBS ATC 2015 (national) — public release with ATC classifications and services.
Dataset page: Pharmaceutical Benefits Scheme (PBS) – Anatomical Therapeutic Chemical report on [https://data.gov.au/data/dataset/pharmaceutical-benefits-scheme-pbs-anatomical-therapeutic-chemical-report/resource/2eab7fa1-2a7b-4e32-ad7a-6188f6762fc5]

ABS population (ERP) — national Estimated Resident Population time series.
Dataset page: National, state and territory population on [https://www.abs.gov.au/AUSSTATS/abs@.nsf/DetailsPage/3101.0Sep%202015?OpenDocument]

To keep the repo light, I don’t commit large raw CSVs. Place your downloads locally under data/raw/ before running.

What I did
Loaded ABS population CSV, detected the ERP (Australia) column and monthly dates, and extracted 2015 ERP (auto-scaling if values were reported in thousands).

Loaded PBS 2015 CSV, parsed month/year, and identified antibiotic classes (ATC codes starting with J01).

If J01 wasn’t clearly labelled, the script falls back to all PBS rows in 2015 so charts still render.

Calculated scripts per 1,000 people using the 2015 ERP.

Plotted:

Average scripts per 1,000 by month (2015)

Top 5 antibiotic classes (2015, scripts/1,000)

Cumulative scripts per 1,000 (2015)


Edit
# 1) Create & activate a virtual environment
python -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate

# 2) Install deps
pip install -r requirements.txt  # pandas, matplotlib

# 3) Put your raw CSVs here (not tracked by git):
#    data/raw/pbs-atc-2015.csv
#    data/raw/population_sample.csv

# 4) Run the script
python src/antibiotics_2015_viz.py
Outputs:

Cleaned CSVs → data/cleaned/

Figures → figures/

Notes & assumptions
ABS ERP can be reported in thousands; the script auto-scales to persons when needed.

If J01 antibiotics cannot be detected from the PBS file, charts use all PBS rows for 2015 (a clear warning is printed).

This is a learning project; figures are illustrative, not official statistics.

Next steps
Add per-state comparisons.

Normalise by age group if available.

Replace the fallback with a full ATC code map for more accurate antibiotic detection.

License / attribution
Code: MIT.
Data belongs to ABS and PBS — please refer to the original dataset licences
