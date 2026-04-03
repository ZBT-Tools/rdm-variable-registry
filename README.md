# RDM Variable Registry

This repository contains a versioned reference registry for canonical variable names, units, metadata semantics, and source-specific aliases used in research data management workflows.

Its purpose is to provide a shared and machine-readable vocabulary that helps harmonize heterogeneous data from simulations, experiments, instruments, scripts, databases, and data platforms.

## Why this repository exists

In practice, the same physical quantity or metadata concept is often represented in many different ways depending on the source system, software tool, institute, project, or researcher.

Examples:

- `T`, `Temp`, `temperature`, `Temperature [K]`
- `p`, `P`, `pressure`, `static_pressure`
- `RH`, `rel_humidity`, `relative_humidity`
- `U`, `velocity`, `flow_velocity`
- `sample_id`, `sampleID`, `specimen_id`

Without a common reference vocabulary, such variation makes data integration, automated ingestion, comparison, reuse, and long-term interpretation unnecessarily difficult.

This repository defines a controlled canonical layer that allows source-specific names and conventions to be mapped to a stable internal representation.

## Goals

The registry is intended to support:

- consistent naming across projects and tools
- semantic clarity for variables and metadata fields
- harmonized unit handling
- reproducible data ingestion and normalization
- interoperability between software systems
- easier reuse of data across teams and time

The goal is not to replace source-specific terminology in raw data, but to provide a common interpretation layer on top of it.

## Scope

This repository is intentionally domain-agnostic.

It can be used for variables and metadata originating from, for example:

- laboratory instruments
- experimental datasets
- simulation software
- postprocessing scripts
- databases and data lakes
- electronic lab notebooks
- research data platforms
- custom import or parser pipelines

The registry can cover both:

- **measured or simulated quantities**, such as temperature, pressure, voltage, concentration, or flow rate
- **metadata concepts**, such as sample identifiers, operator names, timestamps, device names, methods, or process steps

## Core idea

The registry distinguishes between:

1. **Canonical concepts**  
   The agreed internal identifiers and definitions used as the reference vocabulary.

2. **Aliases**  
   Alternative names used by source systems, legacy conventions, software tools, or local habits.

3. **Semantic attributes**  
   Additional information that defines what a concept means, such as units, quantity kind, data type, qualifiers, and optional ontology references.

This makes it possible to preserve the original source naming while still normalizing data into a consistent structure.

## Guiding principles

The registry follows these principles:

- **One canonical concept, many aliases**  
  Different raw names may map to the same internal concept.

- **Source data is preserved**  
  Original names and units should remain traceable.

- **Normalization is explicit**  
  Mappings should be transparent, reviewable, and versioned.

- **Semantics matter more than strings**  
  A variable should not be identified only by its label, but by its meaning, unit, context, and qualifiers.

- **Versioning is essential**  
  The registry evolves over time and changes should be documented.

## Repository structure

A typical repository structure may look like this:

```text
registry/
  variables.yaml
  metadata.yaml
  aliases/
    internal_legacy.yaml
    instrument_a.yaml
    simulation_tool_b.yaml
schemas/
  registry.schema.json
docs/
  naming_rules.md
  contribution_guidelines.md
tests/
  test_registry_consistency.py
  test_alias_resolution.py
CHANGELOG.md
