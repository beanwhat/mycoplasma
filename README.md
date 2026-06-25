# Mollicutes AMR Genotype-Phenotype Benchmarking

This repository is for building a Mollicutes antimicrobial resistance (AMR)
genotype-phenotype benchmarking framework.

The initial focus is *Mycoplasma bovis* evidence. Later expansion may include
other Mollicutes, but species-specific evidence review and schema checks should
come before any rule transfer.

The project separates:

- literature evidence and extraction decisions
- minimum inhibitory concentration (MIC) data
- genetic marker observations
- benchmarking inputs, outputs, and reports

No fake biological data are included. Placeholder schemas and empty directories
are provided only to define the intended repository structure.

## Repository Layout

- `docs/`: project scope, evidence grading, inclusion rules, and limitations
- `data/raw/`: unmodified source data files
- `data/curated/`: cleaned analysis-ready tables
- `data/external/`: third-party reference files
- `schemas/`: placeholder data schemas
- `src/`: ingest, curation, benchmarking, and reporting code
- `tests/`: validation and regression tests
- `notebooks/`: exploratory analyses
- `reports/`: generated summaries and benchmark outputs
