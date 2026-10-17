# MEDE U12 · Stație × zi, București, 2025

**Întrebare:** Au toate anotimpurile (iarna, primăvara, vara, toamna) aceleași tipuri de zile poluate (PM10, NO₂) în București în 2025?

**Surse**
- calitateaer.ro (RNMCA): PM10 și NO₂, valori orare, rapoarte „valori date" exportate per stație
- Open-Meteo Historical Weather API: temperatură, precipitații, viteza vântului, orar

**Unitate de analiză:** stație × zi (și stație × oră)

## Rulare
```
pip install -r requirements.txt
jupyter notebook notebooks/01_load_align.ipynb   # Restart & Run All
```
Pune în `data/raw/` rapoartele orare de la calitateaer (`B3 orar.xls`, `B4 orar.xls`, `B6 orar.xls`) și fișierul Open-Meteo (`open-meteo*.xlsx`). Fișierele originale nu se modifică.

## Rezultate (`data/processed/`)
- `hourly_aligned.csv`: stație × oră (NO₂, PM10, T, P, W)
- `daily_aligned.csv`: stație × zi (zi validă = cel puțin 18 din 24 de ore valide)
- `coverage_report.csv`, `coverage_by_season.csv`: raportul de acoperire

## Stații
B-3, B-4, B-6; maparea la `location_id`-urile Open-Meteo și coordonatele stațiilor se completează aici și în `datacard_U12.md`.
