#  Cardiac Phase Space Collapse 
**An Edge-AI Early Warning System for Arrhythmia Using Topological Data Analysis**

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Knightscape95/cardiac-phase-space-tda/blob/main/Med_Fixed.ipynb)
[![YouTube Video](https://img.shields.io/badge/YouTube-Watch_Pitch-FF0000?logo=youtube&logoColor=white)](https://youtu.be/kyueGY_AyLc?si=iYdjVv2UpG45g3Um)
[![MedGemma Challenge](https://img.shields.io/badge/Kaggle-MedGemma_Impact_Challenge-blue.svg)](https://www.kaggle.com/competitions/med-gemma-impact-challenge)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

> **83% Manifold Collapse Detected | 15-Minute Early Warning | $0 Cloud Cost | FDA SaMD Viable**

 **[Watch the 3-Minute Pitch on YouTube](https://youtu.be/kyueGY_AyLc?si=iYdjVv2UpG45g3Um)**

## Overview
Modern large language models demonstrate remarkable diagnostic reasoning, but their adoption in critical care faces three insurmountable hurdles:
1. **The Black Box:** Clinicians cannot trust non-deterministic LLMs without a mathematical verification layer.
2. **Latency & Connectivity:** Streaming high-frequency, 360 Hz ECG data to cloud APIs introduces dangerous latency.
3. **Data Privacy (HIPAA):** Patient telemetry cannot legally leave the hospital's localized network.

This repository contains the code and methodology for **Cardiac Phase Space Collapse**. Powered by the Px1 framework for advanced signal analysis, this hybrid white-box pipeline translates raw ECG waveforms into pure geometry, running entirely on local edge hardware.

---

##  The Geometric Insight
According to Chaos Theory and Takens' Embedding Theorem, a healthy heart operates as a highly complex, chaotic attractor in 3D phase space. As the heart transitions toward fibrillation or arrhythmia, it loses this variability and collapses into rigid periodicity.

<p align="center">
  <img src="assets/takens_embedding.png" width="800" alt="3D Phase Space Attractor Comparison">
  <br>
  <em>Figure 1: 3D attractor reconstruction of healthy sinus rhythm vs. pre-arrhythmia using the Px1 signal processor.</em>
</p>

We measure this collapse using **Topological Data Analysis (TDA)**—tracking 1-dimensional persistent loops ($\beta_1$). Their disappearance signals a physical **Manifold Collapse** minutes before a cardiac event occurs.

<p align="center">
  <img src="assets/tda_persistence.png" width="800" alt="Topological Data Analysis Persistence Diagram">
</p>

---

##  Hybrid Edge Architecture
We engineered a two-layer, fault-tolerant clinical pipeline designed for local hospital hardware:

* **Layer 1 (The Mathematical Proof):** A deterministic, white-box TDA engine extracting Betti numbers ($\beta_0, \beta_1, \beta_2$) and persistence entropy from raw PhysioNet ECGs. 
* **Layer 2 (The Clinical Translator):** A locally deployed, 4-bit quantized MedGemma LLM (`google/medgemma-1.5-4b-it`). It acts strictly on the mathematical state, translating the topological collapse into an actionable clinical protocol.

---

##  Empirical Results (MIT-BIH Record 207)
Evaluated exclusively on real clinical recordings from the PhysioNet MIT-BIH Arrhythmia Database (zero synthetic data).

| Phase | $\beta_1$ Count | Observation |
| :--- | :---: | :--- |
| **Healthy Baseline** | 24–30 | Rich topological diversity — complex chaotic attractor |
| **Early Pre-Crisis (T-15 min)** | ~14 | First statistically significant loop loss detected |
| **Late Pre-Crisis (T-5 min)** | 6 | **83.33% decay — Definite Collapse triggered** |

**Edge Latency Benchmarks (End-to-End < 10s):**
* **TDA Processing (5000 samples):** ~0.65s
* **MedGemma Inference (4-bit nf4):** ~8.4s

<p align="center">
  <img src="assets/latency_terminal.png" width="700" alt="Terminal Output showing Edge Latency">
</p>

---

##  Quick Start & Reproducibility

### 1. Requirements
```bash
pip install wfdb ripser scikit-tda transformers bitsandbytes torch
