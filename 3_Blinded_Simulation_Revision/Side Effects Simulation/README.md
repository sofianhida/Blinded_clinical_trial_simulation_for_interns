## 1. Overview

This document describes the methodology, dataset structure, and analytical approach used in the *Side Effects Simulation – Blinded Model*.
The purpose of this simulation is to estimate the incidence of adverse events in a synthetic patient cohort while maintaining a fully blinded allocation process. No deterministic mapping exists between treatment variables and outcome labels.

## 2. Study Objective

The primary objective is to construct a neutral baseline model of side-effect distribution in a randomized population.
The simulation is intentionally blinded to prevent the algorithm from exploiting direct associations between treatment dose and side-effect outcomes. This setup mirrors early-phase experimental conditions in clinical research where only aggregated outcomes are available.

## 3. Methods

A synthetic dataset was generated consisting of randomized patient profiles. Each entry includes demographic features and blinded allocation into one of three treatment groups.
Side-effect outcomes were produced using a probabilistic function combined with stochastic noise to avoid deterministic predictability. No manual tuning or group-specific assumptions were introduced at any stage.

### Data Fields

* `patient_id` — numerical identifier
* `age` — integer value (years)
* `bmi` — continuous, one-decimal precision
* `dose_group` — categorical: Low / Medium / High
* `side_effect` — binary: 0 = no adverse reaction, 1 = adverse reaction

## 4. Analysis

Only aggregated summaries were computed to preserve blinding.
No inter-group comparison tests (e.g., χ², logistic regression) were performed, as these would break the blinded design.
Visualizations used non-parametric counts and distributions to characterize overall side-effect patterns without implying causal relationships.

## 5. Blinding Integrity

To ensure strict blinding:

* Outcome generation included random perturbation.
* No variable in the dataset serves as a deterministic predictor of side effects.
* Analytical procedures were intentionally limited to descriptive statistics.

This approach restricts the model from inferring dose-related behavior and mirrors constraints found in early exploratory pharmacovigilance simulations.

## 6. Intended Use

The simulation is intended as a baseline safety-signal exploration model.
It can serve as a preliminary layer before:

* unblinded efficacy assessment,
* dose-response modeling,
* or real-world post-market safety evaluation.

## 7. Files Included

* `side_effects_blinded_simulation.py` — main simulation script
* `side_effects_dataset.csv` — generated blinded dataset
* `fig1_side_effect_distribution.png` — aggregated adverse event count
* `fig2_bmi_vs_side_effects.png` — demographic distribution figure
* `README.md` — scientific documentation

## 8. Notes

This simulation is not intended to approximate real clinical incidence rates.
Its purpose is methodological—demonstrating safe, blinded data generation for early-stage AI validation environments.
