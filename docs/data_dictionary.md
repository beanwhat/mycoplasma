# Data Dictionary

This data dictionary defines intended field names for curated data tables. It
contains field definitions only and no example records.

## Common Identifiers

| Field | Applies To | Definition |
| --- | --- | --- |
| `source_record_id` | all curated tables | Stable internal identifier for a literature record, dataset, export, or other source material. |
| `isolate_id` | isolate, MIC, marker, benchmark tables | Stable internal identifier for a curated isolate. |
| `marker_id` | marker, evidence, benchmark tables | Stable internal identifier for a marker definition or marker observation, depending on table context. |
| `rule_id` | evidence, benchmark tables | Stable internal identifier for a documented interpretation or marker rule. |
| `curation_status` | all curated tables | Current review state of the row, such as pending, extracted, reviewed, excluded, or background-only. |
| `curation_notes` | all curated tables | Free-text curation notes, uncertainty flags, and audit comments. |

## Source Record Fields

| Field | Definition |
| --- | --- |
| `source_record_id` | Stable internal source identifier. |
| `citation_key` | Bibliographic handle assigned during curation. |
| `source_type` | Type of source material, such as paper, dataset, database export, or supplementary file. |
| `source_locator` | DOI, PMID, accession, URL, file path, or other source locator when available. |
| `title` | Source title as reported or curated. |
| `authors` | Author string or structured author field when captured. |
| `publication_year` | Publication or release year when available. |
| `journal_or_provider` | Journal, repository, database, or provider name. |
| `export_date` | Date the source was exported or downloaded. |
| `deduplication_key` | Internal key used for source deduplication. |
| `deduplication_status` | Deduplication state assigned during source review. |
| `inclusion_status` | Include, exclude, pending, or background-only decision. |
| `exclusion_reason` | Conservative reason for exclusion when applicable. |

## Isolate Fields

| Field | Definition |
| --- | --- |
| `isolate_id` | Stable internal isolate identifier. |
| `source_record_id` | Source record from which isolate information was extracted. |
| `reported_isolate_name` | Isolate, strain, or sample identifier as reported by the source. |
| `organism_reported` | Organism name as reported by the source. |
| `organism_curated` | Curated organism assignment when supported by the source. |
| `species` | Species-level assignment when available. |
| `host` | Host or source category when reported. |
| `sample_type` | Sample or specimen category when reported. |
| `disease_context` | Clinical or sampling context when reported. |
| `country` | Country or region of origin when reported. |
| `collection_year` | Year of isolation or sample collection when reported. |
| `sequencing_accession` | Genome, read, or assembly accession when available. |
| `isolate_linkage_notes` | Notes about duplicate isolates, aliases, or uncertain identity. |

## MIC Measurement Fields

| Field | Definition |
| --- | --- |
| `mic_measurement_id` | Stable internal identifier for an MIC or phenotype measurement. |
| `isolate_id` | Linked isolate identifier. |
| `source_record_id` | Source record for the measurement. |
| `antimicrobial` | Curated antimicrobial name. |
| `antimicrobial_reported` | Antimicrobial name as reported by the source. |
| `mic_operator` | Reported comparison operator when present. |
| `mic_value` | MIC value as extracted or normalized under a documented rule. |
| `mic_unit` | MIC unit. |
| `mic_method` | Susceptibility testing method. |
| `testing_medium` | Medium used for MIC testing when reported. |
| `incubation_conditions` | Incubation time, temperature, atmosphere, or related method details when reported. |
| `replicate_handling` | How replicate MIC values were handled when reported. |
| `interpretation_rule_id` | Rule used for any derived phenotype category. |
| `phenotype_category` | Derived category only when a prespecified rule is recorded. |
| `mic_notes` | Measurement-specific curation notes. |

## Marker Observation Fields

| Field | Definition |
| --- | --- |
| `marker_observation_id` | Stable internal identifier for a marker observation. |
| `marker_id` | Stable marker identifier. |
| `isolate_id` | Linked isolate identifier. |
| `source_record_id` | Source record for the marker observation. |
| `marker_type` | Marker class, such as variant, gene presence, allele state, or copy context. |
| `gene` | Gene or locus name as reported or curated. |
| `locus` | Genomic locus, region, or target when available. |
| `reference_sequence` | Reference sequence or coordinate system used for position reporting. |
| `reference_position` | Position under the stated reference system. |
| `observed_variant` | Reported variant, allele state, or marker state. |
| `detection_method` | Method used to detect the marker. |
| `allele_copy_context` | Allele copy number or copy context when relevant. |
| `rule_status` | Marker interpretation status, such as candidate, transferred hypothesis, or validated rule. |
| `marker_notes` | Marker-specific curation notes. |

## Evidence Fields

| Field | Definition |
| --- | --- |
| `evidence_record_id` | Stable internal identifier for an evidence assessment. |
| `source_record_id` | Source record supporting the assessment. |
| `organism` | Organism or species context for the evidence assessment. |
| `antimicrobial` | Antimicrobial or drug class context for the evidence assessment. |
| `marker_id` | Linked marker identifier when applicable. |
| `evidence_level` | Preliminary evidence level defined in `docs/evidence_grading.md`. |
| `isolate_set_linkage` | Assessment of whether genotype and phenotype data are from the same isolate set. |
| `phenotype_data_available` | Whether MIC or other phenotype data are available. |
| `genotype_data_available` | Whether marker or genome data are available. |
| `same_isolate_support` | Whether source data support same-isolate genotype-phenotype linkage. |
| `evidence_decision` | Curated decision for benchmark use, exclusion, pending review, or background-only status. |
| `evidence_notes` | Evidence-specific curation notes. |

## Benchmark Observation Fields

| Field | Definition |
| --- | --- |
| `benchmark_observation_id` | Stable internal identifier for a benchmark-ready joined row. |
| `isolate_id` | Linked isolate identifier. |
| `mic_measurement_id` | Linked MIC measurement identifier. |
| `marker_observation_id` | Linked marker observation identifier. |
| `evidence_record_id` | Linked evidence assessment identifier. |
| `antimicrobial` | Curated antimicrobial name used for benchmarking. |
| `marker_id` | Marker identifier used for benchmarking. |
| `evidence_level` | Evidence level carried into the benchmark row. |
| `interpretation_rule_id` | Rule used for any derived interpretation in the benchmark row. |
| `benchmark_inclusion_status` | Whether the row is eligible for benchmark analysis. |
| `benchmark_exclusion_reason` | Reason a joined row is excluded from benchmark analysis. |
| `benchmark_notes` | Benchmark-specific curation notes and audit comments. |

## Missing Data Policy Fields

| Field | Definition |
| --- | --- |
| `missing_reason` | Reason a field is unavailable, not reported, not applicable, or unresolved. |
| `uncertainty_flag` | Flag indicating ambiguity, partial reporting, or unresolved curation uncertainty. |
| `review_required` | Indicator that a row needs additional review before benchmark use. |
