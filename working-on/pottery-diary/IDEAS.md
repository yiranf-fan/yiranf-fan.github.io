# Pottery Diary — Project Thinking Log

## 1. Project Overview

This project is an evolving digital system to document, analyze, and plan pottery experiments. The goal is to create a personal tool that captures the full lifecycle of ceramic work, from clay selection to glaze layering to final firing outcomes.

Unlike a static notebook, this system is designed to support:
- Iterative experimentation
- Pattern recognition across past work
- Decision support for future pieces

This document captures the **thinking process behind the project**, not just the implementation.

---

## 2. Core Problem

In a studio environment, pottery experimentation is:
- Highly variable (clay bodies, glaze chemistry, firing conditions)
- Poorly documented (notes are inconsistent, fragmented, or missing)
- Hard to recall (visual memory does not scale with volume)

### Key Pain Points

1. **Loss of information**
   - Cannot reliably reproduce successful results
   - Cannot diagnose failed outcomes

2. **Lack of structured comparison**
   - Difficult to answer:
     - “How does celadon behave on different clay bodies?”
     - “What layering combinations produce consistent results?”

3. **Planning friction**
   - No easy way to reference past experiments when designing new work

---

## 3. Design Philosophy

### 3.1 First Principles

- **Visual-first, data-backed**
  - Pottery is inherently visual, but needs structured metadata

- **Low friction in a “dirty-hand” environment**
  - Minimal typing
  - Mobile-friendly
  - Fast logging

- **Experiment-centric, not piece-centric**
  - Focus on learning outcomes rather than finished objects

---

### 3.2 Mental Model

The system is built around the idea of:

> “Each pottery piece is an experiment composed of variables.”

#### Variables include:
- Clay body
- Glaze(s)
- Layering order
- Application method
- Firing conditions

---

## 4. Core Entities

### 4.1 Piece

Represents a physical object created.

Attributes:
- Name / ID
- Date
- Clay body
- Form (bowl, cup, plate, etc.)
- Notes

---

### 4.2 Glaze Application

Represents how a glaze is applied.

Attributes:
- Glaze name
- Number of layers
- Application method (dip, brush, pour)
- Thickness (qualitative)

---

### 4.3 Layer Stack

Represents glaze combinations.

Example:

```
Layer 1: Celadon
Layer 2: Chun
Layer 3: Iron wash
```


This is critical for:
- Understanding interactions
- Reusing successful combinations

---

### 4.4 Firing

Attributes:
- Cone (e.g., Cone 10)
- Atmosphere (oxidation, reduction)
- Position in kiln (optional)
- Notes

---

### 4.5 Outcome

Attributes:
- Final images
- Observations:
  - Color
  - Texture
  - Flow/run
  - Defects (crawling, pinholing)
- Food safety notes (if applicable)

---

## 5. Key Features (MVP)

### 5.1 Experiment Logging

- Create a new “Piece”
- Add:
  - Clay body
  - Glaze layers
  - Firing details
- Upload photos (before/after firing)

---

### 5.2 Visual Gallery

- Grid view of past pieces
- Filter by:
  - Clay body
  - Glaze
  - Firing type

---

### 5.3 Layering Lookup

- Query:
  - “Celadon + Chun”
- Return:
  - All past results with this combination

---

### 5.4 Experiment Comparison

- Side-by-side view:
  - Same glaze on different clay bodies
  - Same clay with different layering

---

## 6. Differentiation from Existing Tools

### Existing Tools Focus:
- General note-taking
- Kiln logs
- Inventory

### This Project Focus:
- **Glaze interaction intelligence**
- **Layering as a first-class concept**
- **Cross-experiment pattern discovery**

---

## 7. System Architecture (Early Thinking)

### Frontend
- Simple web interface
- Mobile-first design

### Backend
- Lightweight API (e.g., FastAPI)

### Database
- Relational structure:
  - Pieces
  - Glazes
  - Layer stacks
  - Firings

### Storage
- Image storage (local or cloud)

---

## 8. Future Directions

### 8.1 Intelligent Features

- Suggest glaze combinations based on past success
- Detect patterns:
  - “This glaze runs on porcelain but not stoneware”

---

### 8.2 Visualization

- Heatmaps of glaze performance
- Layer interaction maps

---

### 8.3 Studio Integration

- Shared database across studio members
- Community knowledge base

---

## 9. Risks and Considerations

### Overengineering
- Risk of building too complex a system early
- Mitigation:
  - Focus on MVP logging + lookup

### Data Quality
- Garbage in → garbage out
- Need:
  - Structured input
  - Consistent tagging

### User Adoption (Self)
- Must be faster than writing in a notebook

---

## 10. Current Focus

Short-term priorities:

1. Define minimal schema
2. Build logging interface
3. Enable basic filtering + lookup
4. Upload and display images

---

## 11. How to Visualize This (For Design Agent)

### Suggested Design Directions

- **Aesthetic**
  - Organic, tactile, ceramic-inspired
  - Neutral tones (clay, glaze colors)

- **Layout**
  - Card-based gallery
  - Layer stacks shown visually (stacked blocks)

- **Interaction**
  - Tap to expand piece details
  - Filter chips for quick exploration

### Key Screens to Illustrate

1. Experiment entry page
2. Gallery view
3. Layer combination lookup
4. Piece detail page

---

## 12. Guiding Principle

> This is not just a logging tool.
> It is a system for learning from material experimentation over time.