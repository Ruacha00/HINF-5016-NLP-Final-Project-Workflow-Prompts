# HINF-5016 NLP Final Project — Workflow Prompts

This repository contains structured prompt templates for writing a course literature review on:

**”Early ICU Mortality Prediction Using Time-Series Data: Multi-Window Modeling and Cross-Dataset Generalization Evaluation.”**

Two workflows are provided — a **Human-Led** workflow where the user supplies evidence and controls each drafting step, and an **LLM-Driven** workflow where the model executes the full pipeline autonomously.

## Purpose

This repository supports a staged academic writing process for AMIA-style literature reviews by providing:

- section-specific writing prompts (Human-Led),
- synthesis-note generation prompts (Human-Led),
- an end-to-end autonomous skill prompt (LLM-Driven),
- a revision prompt for polishing LLM-generated drafts (LLM-Driven),
- strict constraints to reduce hallucination across both workflows,
- ordered workflow guidance from Methods through Abstract.

## Repository Structure

```text
├── Human-Led/
│   ├── section_writing_prompts.md    # Section-by-section writing prompts (Methods → Abstract)
│   └── synthesis_notes_prompts.md    # Cross-paper synthesis note generation prompt
├── LLM-Driven/
│   ├── run_skill.md                  # End-to-end autonomous literature review skill prompt
│   └── revise.md                     # Revision prompt for improving an existing draft
└── README.md
```

## Human-Led Workflow

The user supplies evidence from reviewed papers, and the model helps transform that evidence into publishable section drafts without fabricating claims.

- **`Human-Led/section_writing_prompts.md`** — End-to-end prompt set for drafting each section in recommended order:
  1. Methods
  2. Related Work / Results
  3. Discussion
  4. Introduction
  5. Conclusion
  6. Abstract

- **`Human-Led/synthesis_notes_prompts.md`** — Prompt template for generating cross-paper synthesis notes (themes, trends, tensions, gaps, future directions) from completed paper evaluation sheets.

### Steps

1. Complete your per-paper evaluation template (for all included studies).
2. Use `synthesis_notes_prompts.md` to generate structured synthesis notes.
3. Use `section_writing_prompts.md` section-by-section in order.
4. Review each generated section manually before moving to the next.
5. Finalize Abstract last, using finalized section openings.

## LLM-Driven Workflow

The model autonomously searches, screens, extracts, and drafts the full literature review in one pass. A separate revision prompt is then used to polish the output.

- **`LLM-Driven/run_skill.md`** — Project configuration that instructs the model to run the entire literature review pipeline: search log, candidate screening, structured extraction for 8 papers, and a complete draft (Abstract through References).

- **`LLM-Driven/revise.md`** — Revision prompt for editing an existing markdown draft into a stronger, course-ready literature review. Targets synthesis quality, Methods transparency, academic tone, and Vancouver-style references.

### LLM-Driven Steps

1. Submit `run_skill.md` to generate the initial full draft.
2. Paste the draft into `revise.md` and submit to produce a polished revision.
3. Review and finalize manually.
