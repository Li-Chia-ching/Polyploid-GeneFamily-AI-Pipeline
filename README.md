# Polyploid Gene Family Analysis & Seamless Cloning Pipeline (AI Agent Skill)

## Overview
This repository contains a specialized AI Agent prompt (Skill) designed for plant genomics researchers. It automates polyploid gene family identification, candidate prioritization, genome-aware sequence validation, and error-resistant seamless cloning primer design.

Optimized for complex polyploid genomes (such as *Medicago sativa*), this pipeline ensures absolute sequence fidelity from genome annotation to wet-lab primer synthesis. 

## Core Principles
The Agent strictly adheres to a central dogma of sequence validation. It will **never** design primers directly from a gene name, annotation description, or phylogenetic ranking result. 

`Gene Symbol → Genome Gene ID → Transcript ID → CDS Sequence → Protein Sequence → Validated ORF → Cloning Primer`

If any intermediate information is missing, the pipeline halts immediately to prevent downstream experimental failure.

## Key Features
* **Gene Identity Lock:** Mandatory generation of a `Gene_ID_Record` to ensure the exact transcript and physical location are targeted.
* **CDS Validation Gate:** Automated sequence checks for Start (ATG), Stop codons, and ORF integrity (length % 3 == 0) prior to primer design.
* **In-Fusion Boundary Verification:** Accurate, structural assembly of `[Vector Homology Arm] + [Gene Specific Sequence]`.
* **Vector Compatibility:** Intelligent handling of target gene stop codons based on Native vs. C-terminal fusion tag strategies.
* **Primer Audit Gate:** A comprehensive pre-output checklist preventing qPCR contamination and accidental UTR amplification.

## Usage
Import the `prompt.md` into your local Agent framework (e.g., Dify, FastGPT, Coze, or LangChain) as a System Prompt or AI Skill. 

## Output Deliverables
The Agent is programmed to generate four standard, structured reports:
1. `Gene_ID_Record.tsv`
2. `CDS_validation_report.tsv`
3. `Seamless_Primers.tsv`
4. `Primer_Audit_Report.tsv`

---
*Disclaimer: AI-generated homology arms and primers must always be cross-referenced with your specific laboratory vectors and transcript sequences before synthesis.*
