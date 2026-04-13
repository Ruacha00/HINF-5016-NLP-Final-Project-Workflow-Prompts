# HINF-5016 NLP Final Project — Human-Led Workflow Prompts

This repository contains structured prompt templates for writing a course literature review on:

**“Early ICU Mortality Prediction Using Time-Series Data: Multi-Window Modeling and Cross-Dataset Generalization Evaluation.”**

The prompts are designed for a **human-led workflow**: the user supplies evidence from reviewed papers, and the model helps transform that evidence into publishable section drafts without fabricating claims.

## Purpose

This repository supports a staged academic writing process for AMIA-style literature reviews by providing:

- section-specific writing prompts,
- synthesis-note generation prompts,
- strict constraints to reduce hallucination,
- ordered workflow guidance from Methods through Abstract.

## Repository Contents

- `section_writing_prompts.md`  
  End-to-end prompt set for drafting each section of the paper in recommended order:
  1. Methods  
  2. Related Work / Results  
  3. Discussion  
  4. Introduction  
  5. Conclusion  
  6. Abstract

- `synthesis_notes_prompts.md`  
  Prompt template for generating cross-paper synthesis notes (themes, trends, tensions, gaps, future directions) from completed paper evaluation sheets.

## Core Workflow

1. Complete your per-paper evaluation template (for all included studies).
2. Use `synthesis_notes_prompts.md` to generate structured synthesis notes.
3. Use `section_writing_prompts.md` section-by-section in order.
4. Review each generated section manually before moving to the next.
5. Finalize Abstract last, using finalized section openings.
