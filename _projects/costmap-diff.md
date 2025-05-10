---
title: "Costmap-Diffusion: Diffusing Latent Costmap Priors for Social Navigation."
excerpt: "Learning scene representations to condition a Diffusion policy to generate socially-compliant costmaps."
collection: projects
permalink: /projects/ICRA26/
date: 2025-04-28
gif: costmap_diffusion_arch.gif
category: robotics
---

This project is my solo effort towards **IEEE ICRA 2026**. It presents a **two-stage costmap prediction architecture** designed for **social navigation** in dynamic human environments. The architecture includes an **Autoencoder** and a **Conditional Diffusion Model** to generate future costmaps from past RGB image observations.

---

## Overview

The model is built around the idea of **decoupling spatial costmap representation learning from the temporal dynamics of human motion and social compliance**. It consists of the following stages:

1. **Autoencoder Pretraining** for learning compact costmap embeddings.
2. **Conditional Transformer** for future costmap embedding prediction.
3. **Conditional Diffusion** for generating social costmap embeddings from pure noise and reconstructing costmaps using a frozen decoder.

---

## Components

### 1. Autoencoder

**Objective**: Learn a discrete latent space for costmap reconstruction.

- **Input**: Ground Truth Costmap  
- **Encoder**: Maps the costmap to latent embeddings  
- **Vector Quantizer**: Discretizes the embeddings  
- **Decoder**: Reconstructs the costmap from quantized embeddings  
- **Loss**: Reconstruction loss 

This stage is trained independently to learn high-fidelity representations of spatial costmaps and is later **frozen** for downstream prediction.

---

### 2. Conditional Transformer Prediction 
**Objective**: Predict future costmap embeddings conditioned on RGB image sequences.

- **Input**:  
  - RGB image sequence from past *n* timesteps  
  - Ground truth costmap (for training only)

- **Transformer Block**:  
  - Converts RGB frames into tokens (e.g., via CNN feature extractor or patch embedding)  
  - Applies positional-encoding and self-attention 
  - Outputs conditional latent embedding vector


---

## Conditional Diffusion

Train a Diffusion policy conditioned on the transformer conditional embeddings. 
- **Noise Scheduler**:  
  - Gaussian noise is added to the GT costmaps until they become pure noise.

- **Reverse Diffusion**:  
  - Train U-Net model to learn to predict the noise.  
  - Transformer conditional embedding added to each U-Net layer via cross-attention.
  - Iterative noise removal to generate social costmap embeddings.

---

## 📈 Applications

- Socially compliant navigation in crowds  
- Predictive planning for assistive robots or autonomous vehicles  
- Human-aware motion planning

---

> **Note**: The project repository is still under development and remains private.