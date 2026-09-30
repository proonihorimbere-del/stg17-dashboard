# Indicateurs de la sécurité alimentaire

Tableau de bord bilingue (EN/FR) construit à partir de **9.0**, pages 1, 2.

Built during the STG17 technical workshop *Emerging Issues, Emerging Practice*
(African Development Bank / AU STATAFRIC), lab 02 — from a statistical document
to a public dashboard.

## What is in here

| File | What it is |
|---|---|
| `index.html` | the dashboard. One file, no build step, no server, no tracker |
| `data/dashboard_data.json` | the verified dataset behind the page |
| `data/verification_report.csv` | every automated check, for every cell |
| `data/glossary.json` | the EN/FR terminology used for the labels |
| `LIMITATIONS.md` | what these figures do not support |

## Method

1. Text extracted page by page with `pdfplumber`.
2. Each table read **twice and independently**: once by a rules-only reader, once by
   `openai/gpt-oss-120b`
   via Groq. Le modèle ayant lu chaque cellule est consigné
   dans `data/verification_report.csv`.
3. Every cell passed through five checks — page provenance, quoted evidence, unit and
   range, reconciliation with published totals, and agreement between the two readings.
4. Cells with no page evidence were **discarded**, not published. Cells failing another
   check are published with a visible “to review” flag.
5. Labels translated glossary-first, model second, with a back-translation check.

Results of the run that produced this page:

| Outcome | Cells |
|---|---|
| verified | 18 |
| published but flagged | 3 |
| discarded | 9 |

## Reproducing this

Open `02-Lab-From-Statistical-Document-to-Public-Dashboard.ipynb` in Colab, Kaggle
or Jupyter, point `SOURCE` at the same publication and run it.

## Citation

Cite **the source publication**, not this dashboard. This page is a presentation of
figures published by the institute; it is not itself a statistical publication.

## Maintainer

<!-- name, unit, email, and the date you will next refresh this -->
