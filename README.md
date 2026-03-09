# Data and Analysis

This repository contains the anonymized data and analysis code for the paper *["What Does AI Do for Cultural Interpretation? A Randomized Experiment on Close Reading Poems with Exposure to AI Interpretation"](https://doi.org/10.1145/3772318.3791727)*. 

---

## Repository Structure

```
├── README.md
├── data/
│   ├── Control_APPROVED.xlsx          # Control condition (n = 141)
│   ├── AI_Single_APPROVED.xlsx        # AI-Single condition (n = 115)
│   └── AI_Multiple_APPROVED.xlsx      # AI-Multiple condition (n = 144)
├── grades/
│   └── Grades.xlsx                    # Human-graded performance scores (n = 400)
└── Close_Reading_Main_Analyses.Rmd
```

---

## Data

### Experimental Conditions

Participants (N = 400) were randomly assigned to one of three conditions:

| File | Condition | n | 
|---|---|---|---|
| `Control_APPROVED.xlsx` | Control | 141 | 
| `AI_Single_APPROVED.xlsx` | AI-Single | 115 | 
| `AI_Multiple_APPROVED.xlsx` | AI-Multiple | 144 | 

Each file contains one row per participant. A full description of all columns is available in the [data dictionary](https://github.com/xxxxbrandieeee/close-reading-data-dictionary).

### Performance Scores

`Grades.xlsx` contains human-graded scores for each participant's interpretation task responses. Two trained graders assigned three scores per task: Feature Identification (0–1), Interpretation Quality (1–5), and Writing Quality (1–5). Each participant completed three tasks per poem across three poems, for 9 scored responses total.

---

## Analysis

### Requirements

R (≥ 4.1) with the following packages:

```r
install.packages(c("tidyverse", "readxl", "lme4", "lmerTest",
                   "ordinal", "broom.mixed", "knitr", "glue"))
```

### Analysis Script

**`Close_Reading_Main_Analyses.Rmd`**

Prepares analysis-ready data and fits the primary models:
- Loads and merges condition data with graded performance scores; Classifies participants as novice or expert based on humanities coursework experience
- Fits linear mixed-effects models (`lmer`) for the three performance outcomes: Feature Identification, Interpretation Quality, and Writing Quality
- Fits ordinal mixed-effects models (`clmm`) for the three subjective experience outcomes: Appreciation, Enjoyment, and Self-Efficacy
- All models include poem position, poem identity, and expertise as covariates, with random intercepts for participant.
