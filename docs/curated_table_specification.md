# Curated Table Specification

This document defines the intended curated table structure for the Mollicutes
AMR genotype-phenotype benchmarking repository. It is a specification only and
does not contain biological records.

## Scope

Curated tables should separate source provenance, isolate metadata, MIC
measurements, marker observations, evidence grading, and benchmark-ready joined
records. A row in a source or curation table is not automatically a benchmark
observation.

## Table Families

### source_records

Tracks literature records, datasets, database exports, and other source
materials used during curation.

Required intent:

- preserve source provenance
- support deduplication and audit trails
- distinguish included, excluded, pending, and background-only sources

### curated_isolates

Stores isolate-level metadata after conservative curation.

Required intent:

- maintain one stable internal isolate identifier
- retain reported organism identity and curated taxonomic fields
- preserve source linkage and curation uncertainty

### curated_mic_measurements

Stores MIC or antimicrobial phenotype measurements linked to isolates.

Required intent:

- keep MIC values, operators, units, methods, and testing context separate from
  any derived interpretation
- avoid binary resistant/susceptible conversion unless a prespecified rule is
  recorded
- preserve source linkage for every measurement

### curated_marker_observations

Stores genetic marker calls or genome-derived observations linked to isolates.

Required intent:

- keep marker observations separate from marker interpretation rules
- record detection method, reference context, and curation uncertainty
- label transferred or candidate markers as hypotheses unless validated in the
  target organism and drug context

### curated_evidence_records

Stores evidence grading and extraction decisions for source-marker-drug
relationships.

Required intent:

- record evidence level using `docs/evidence_grading.md`
- track whether genotype and phenotype data come from the same isolate set
- distinguish benchmark-ready evidence from background or hypothesis-generating
  evidence

### benchmark_observations

Stores analysis-ready joined observations only after curation requirements are
met.

Required intent:

- link one isolate, one antimicrobial measurement, and one marker context when
  the evidence supports that linkage
- retain the source and rule identifiers needed to audit each benchmark row
- avoid treating marker absence as proof of susceptibility

## General Curation Rules

- Do not invent isolate metadata, MIC values, phenotype categories, marker
  calls, or evidence grades.
- Keep raw source files separate from curated outputs.
- Use stable internal identifiers for isolates, sources, markers, and rules.
- Preserve reported values when possible and document any normalized values.
- Record missing, ambiguous, or not-applicable fields explicitly under a
  documented missing-data policy.
- Keep aggregate summaries outside benchmark tables unless isolate-level linkage
  can be reconstructed and audited.
- Keep genome-only and phenotype-only sources outside complete
  genotype-phenotype benchmark rows.

## Minimum Benchmark Row Requirements

A benchmark observation should only be created when all required identifiers and
links are available:

- stable isolate identifier
- source record identifier
- antimicrobial measurement identifier or equivalent MIC row linkage
- marker observation identifier or documented marker context
- evidence level
- genotype-phenotype linkage assessment
- curation status
- interpretation rule identifier if any phenotype category is derived

## Review Expectations

Curated tables should be reviewed for:

- source traceability
- duplicate isolate or record handling
- unit and method consistency
- same-isolate genotype-phenotype linkage
- unsupported marker-rule transfer
- accidental binary interpretation without a documented rule
