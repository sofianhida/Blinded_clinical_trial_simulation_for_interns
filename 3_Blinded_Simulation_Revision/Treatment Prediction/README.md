## Overview

The Treatment Prediction Simulation (Blinded) is a controlled computational framework designed to evaluate prediction performance on anonymized and allocation-masked clinical profiles. The objective is to model treatment-response likelihoods while ensuring that no treatment-specific information is accessible during the generation or processing of the dataset.

All identifiers, treatment labels, and subgroup attributes have been fully blinded. The simulation operates exclusively on abstracted clinical variables and outcome targets that do not reveal any embedded treatment conditions.

---

## Objectives

* To construct a blinded dataset suitable for unbiased evaluation of predictive models.
* To estimate individual-level recovery probability using generalized statistical and machine-learning functions that are unaffected by treatment allocation.
* To establish a reproducible baseline framework that can later be compared with unblinded or partially unblinded predictive systems.

---

## Dataset Description

The synthetic dataset contains:

* n = 1,000 anonymized patient profiles
* 8–12 normalized clinical variables per individual (continuous + categorical)
* A single binary outcome target, generated using a stochastic logistic model with no treatment-dependent parameters
* Treatment assignment column masked to prevent leakage during training

All values were randomized within pre-defined physiological ranges and validated to avoid implausible feature combinations.

---

## Blinding Procedure

The blinding pipeline includes:

1. Independent variable generation using randomized sampling distributions.
2. Outcome synthesis via a probabilistic function that is not linked to treatment allocation.
3. Removal or hashing of treatment identifiers before model access.
4. Random shuffling of record order and index reassignment.
5. Independent verification to ensure zero correlation between features and hidden treatment labels.

---

## Modeling Framework

The simulation supports multiple predictive strategies:

* Logistic regression
* Regularized generalized linear models
* Ensemble-based classifiers (random forest, gradient-boosted trees)
* Nonparametric density-based estimators

All models operate under complete treatment blinding. Performance metrics are evaluated only on the binary outcome target.

---

## Evaluation Metrics

Primary metrics include:

* AUC (Area Under ROC Curve)
* Brier score
* Calibration error
* Prediction–outcome concordance metrics
* Distributional stability tests across cross-validation folds

Because treatment information remains inaccessible, no stratified analyses or groupwise comparisons are performed.

---

## Reproducibility

The repository includes:

* `treatment_prediction_blinded.py` – model construction + training pipeline
* `generate_dataset.py` – blinded dataset synthesis
* `docs/` – scientific report and descriptive notes

Use the `seed` parameter to reproduce dataset generation and model performance.

---

## Intended Use

This simulation is designed for researchers developing:

* baseline predictive models
* controlled validation protocols
* comparative workflows between blinded and unblinded modeling environments

It is not intended for clinical decision-making and should be used solely for methodological development.

---
