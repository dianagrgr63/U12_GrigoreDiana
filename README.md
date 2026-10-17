# MEDE U12 · Statie × zi, Bucuresti, 2025

**intrebare:** Ce tipuri de zile poluate (PM10, NO₂) exista in Bucuresti in 2025 si cat le explica vremea?

**Surse**
- calitateaer.ro (RNMCA): PM10 si NO₂, valori orare, rapoarte „valori date" exportate per statie
- Open-Meteo Historical Weather API: temperatura, precipitatii, viteza vantului, orar

**Unitate de analiza:** statie × zi (si statie × ora)

## Rulare
```
pip install -r requirements.txt
jupyter notebook notebooks/01_load_align.ipynb   # Restart & Run All
```
Pune in `data/raw/` rapoartele orare de la calitateaer (`B3 orar.xls`, `B4 orar.xls`, `B6 orar.xls`) si fisierul Open-Meteo (`open-meteo*.xlsx`). Fisierele originale nu se modifica.

## Rezultate (`data/processed/`)
- `hourly_aligned.csv`: statie × ora (NO₂, PM10, T, P, W)
- `daily_aligned.csv`: statie × zi (zi valida = cel putin 18 din 24 de ore valide)
- `coverage_report.csv`, `coverage_by_season.csv`: raportul de acoperire

## Statii
B-3, B-4, B-6; maparea la `location_id`-urile Open-Meteo si coordonatele statiilor se completeaza aici si in `datacard_U12.md`.
