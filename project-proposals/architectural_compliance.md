# Architectural Compliance

## What is AC

The process of verifying that a system's integration meets established criteria, such as:

- Architectural or subsystem patterns
- Communication and data flow protocols and restriction
- Aligns with stakeholder quality attributes
- Aligns with organisational goals / enterprice architecture

## Deliverables

A tool + method to specify intended architecture (modules, allowed dependencies, layering rules) and automatically measure/police conformance as systems evolve.

## Predicted Issues & Questions

- system partitioning granularity
- translating patterns vs specific restrictions
- static vs dynamic
- in the beginning of program development or life-time devops tool

## Draft research questions (RQs)

RQ1.
How can you effectlively translate system architecture into a verifiable program-understandable language

RQ2.
How accurately can static analyses detect architecture violations compared to a something else ? ((curated “ground truth” of intended design - wtf ever this means))

RQ3.
Which compliance metrics (e.g., rule-violation density, drift rate, design-rule centrality) best predict system quality issues (bugs, regressions, costs of maintainance, modification/change request costs, etc)?

## Prior work & gaps

Architecture conformance checking and architecture erosion have a long literature: reflexion models (classic), accuracy of static ACC tooling, and recent systematic mappings on erosion and countermeasures.

What’s missing: a lightweight spec language + CI-first workflow with empirical validation on modern polyglot repos and longitudinal “drift” metrics.

Useful anchors: a 2022 mapping of architecture erosion research (73 studies) that catalogues detection/mitigation techniques; studies on ACC accuracy and reflexion-model variants.
