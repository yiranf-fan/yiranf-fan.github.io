# Experimentation & Causal Inference Platform

## Status

**In Progress — active build (P2 mostly complete, P1 evolving)**

This project is a working system under active development.  
It already supports end-to-end experimentation workflows, with causal modeling and decision layers being incrementally integrated.

---

## Overview

A unified experimentation and causal inference platform designed to answer a central question:

> How do we estimate and act on intervention effects under uncertainty in a way that is both statistically rigorous and operationally practical?

The system connects experimentation infrastructure (A/B testing) with causal modeling into a single workflow that mirrors how real teams make decisions.

---

## Core Idea

The project connects the full lifecycle of decision-making:

```

Event data → Experiment metrics → Causal estimation → Policy decisions → Deployment

```

Instead of treating A/B testing and causal inference as separate workflows, this system integrates them into one pipeline for evaluating and acting on interventions.

---

## Context

Most data teams treat experimentation and causal inference as disconnected:

- A/B testing lives in one tool  
- Causal modeling lives in notebooks  
- Decisions happen elsewhere  

This fragmentation makes it difficult to move from:

- “Did the intervention work?”  
→ to  
- “Who should we treat, and what should we do next?”

This project is designed to bridge that gap.

---

## What Has Been Built (Current State)

### Experimentation Metrics Service (Most Mature)

A production-style backend that transforms raw event logs into decision-ready outputs.

**Implemented capabilities:**
- Experiment metrics (conversion rate, revenue, health outcomes)
- Treatment effect estimation with confidence intervals
- CUPED variance reduction
- Power / sample size calculations
- Segmentation with multiple testing correction (FDR)
- Data quality checks:
  - SRM detection
  - Missing data / duplication checks
  - Outlier detection
- Guardrail evaluation
- Recommendation output (`ship` / `hold` / `stop`)
- Multi-domain support (tech + synthetic healthcare)

**System design:**
- FastAPI service + DuckDB analytical backend
- Config-driven experiment specs + metric registry
- Structured logging and lightweight caching
- Dockerized local deployment
- Streamlit dashboard for exploration

This layer is fully functional and represents the core system.

---

### Causal Effect Estimation Toolkit (Partially Built)

A modular pipeline for estimating treatment effects beyond randomized experiments.

**Currently implemented:**
- ATE estimation (difference in means, regression)
- Initial dataset integration (Hillstrom + synthetic health)
- Basic reporting structure (assumptions, interpretation)

**In progress:**
- CATE / uplift modeling
- Policy targeting (who to treat)
- Diagnostics (overlap, placebo tests)
- Deeper integration with experimentation outputs

**Goal:**
Move from:
- “Did it work?”  
to  
- “Who should we treat and why?”

---

### Decision Layer (Emerging)

A lightweight orchestration layer that connects metrics and (eventually) causal outputs.

**Currently:**
- Rule-based recommendation using:
  - primary metric
  - guardrails
  - data quality checks
- Early experiment report generation (Markdown)

**Planned:**
- Structured decision memo
- Integration with causal targeting outputs

---

## How It Works (Current vs Target)

### Current working flow

```

Event logs
→ Metrics engine (A/B + CUPED + SRM + guardrails)
→ Recommendation (ship / hold / stop)

```

### Target full system

```

Event logs
→ Experiment metrics
→ Causal estimation (ATE/CATE)
→ Policy targeting
→ Decision memo

```

The system already supports the first half end-to-end, with the second half actively being built.

---

## Target Users

- Data Scientists running experiments
- Product / Growth teams making rollout decisions
- Healthcare / biotech analytics teams
- ML engineers building experimentation infrastructure

---

## What This Project Demonstrates

### Data Science

- Experimental design and metric interpretation
- Variance reduction (CUPED)
- Power analysis and sample size planning
- Multiple testing correction (FDR)
- Treatment effect estimation (ATE, CATE)
- Assumption validation and diagnostics
- Decision-making under uncertainty

### Engineering & ML Systems

- API-first analytics system (FastAPI)
- Local analytical backend (DuckDB)
- Modular, config-driven architecture
- Reproducible pipelines (CLI + Docker)
- Structured logging and caching
- Integration of statistical logic into production-style systems

---

## Design Philosophy

- One cohesive system, not disconnected notebooks
- Statistical rigor + practical usability
- Local-first, production-aware (not over-engineered)
- Focus on decision-making, not just metrics

Key tradeoffs:
- DuckDB instead of distributed systems (simplicity + speed)
- Local Docker instead of cloud infra (reproducibility)
- FastAPI for typed, modern service design

---

## Example Use Cases

- Should a product feature be rolled out globally?
- Which users should receive a marketing promotion?
- Which patients should receive a healthcare intervention?
- How large should an experiment be before making a decision?

---

## Why This Project Matters

Most real-world decisions are not just about estimating effects, but about:

> acting on them under uncertainty.

This project bridges:
- Experimentation (what happened)
- Causal reasoning (why it happened)
- Policy decisions (what to do next)

It is designed to reflect how modern data teams operate in both tech and healthcare settings.

---

## Scope & Positioning

This is best understood as:

> An **intervention intelligence system (v1)**

- Strong experimentation infrastructure (complete)
- Causal modeling and policy layer (in progress)
- Decision workflow integration (emerging)

It prioritizes realism and clarity over full production scale.

---

## Repository Structure (Simplified)

```

experiment_platform/   # A/B testing + metrics API (mature)
causal_toolkit/        # causal inference + policy modeling (WIP)
shared/                # schemas, config, utilities
infra/                 # Docker + environment setup

```

---

## Link

See full implementation for:
- API endpoints
- dashboard
- datasets
- metrics engine and causal pipeline

→ GitHub: https://github.com/yiranf-fan/intervention-effects-lab