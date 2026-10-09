---
title: "Modeling Close-Contact Human Embrace via Multi-Agent RL"
excerpt: "Two decentralized agents learning to hug, guided by a single real motion-capture clip"
collection: projects
permalink: /projects/decap-hug/
date: 2026-10-09
gif: decap-hug.gif
category: robotics
---

Decentralized human-like agents that make deliberate close-contact interactions with one another, as in an embrace, are hard to train with reinforcement learning. This project builds a testbed to study whether a hug between two people can be learned from real motion-capture data through **decaying action priors**.

Two decentralized agents act in the latent space of a motion VAE from egocentric observations. During Multi-Agent Reinforcement Learning (MARL), the latents of a recorded clip are blended into the agents' actions with a weight that decays to zero. The final policy therefore performs the interaction on its own rather than tracking a reference motion, unlike motion-tracking approaches to human-human interaction.

## Motivation

Robots that share space with people must eventually make safe, intentional physical contact: guiding, supporting, embracing. Close Encounters formulates this as decentralized multi-agent RL in the latent action space of a human motion prior, and finds that RL alone struggles on multi-contact tasks such as embraces. It works around this with demonstrations from a centralized trajectory optimizer.

Optimizer demonstrations need a differentiable environment and a solver run per task, and they are only as human as the reward that shapes them. Real recordings of two people interacting exist ([Inter-X](https://liangxuy.github.io/inter-x/)), but they come from other bodies, contain penetration, and were never optimized for the agent's reward. This project asks whether such a recording can still guide RL as a prior that is strong early in training and absent at deployment.

**Goal:** a single decentralized policy per person that embraces a partner it has never seen, from any start, acting only on what it perceives, learned from real recordings rather than optimizer demonstrations.

## Method

- **Agents and actions:** two SMPL agents act at 7.5 Hz. Each samples a 32-d latent that a frozen causal VAE decoder (trained on AMASS and Inter-X) turns into 4 frames of full-body motion.
- **Observations:** each agent sees, in its own heading frame, its 69 surface markers over the last two steps, the partner's markers inside a 120° cone around its head, and its previous latent. It never sees the partner's state or the reference motion.
- **Task from a clip:** the palm-to-partner contacts of one Inter-X recording. An episode succeeds when all contacts are within 10 cm, the torsos face each other, and no marker penetrates the partner beyond tolerance.
- **Penetration:** per-body-part $$32^3$$ signed distance grids, which agree with the exact posed-mesh distance on 97.6% of near-surface points (vs 83% for capsule proxies). Tolerances are set per body-region pair from the clip.
- **Decaying action prior:** the clip is encoded once into latents $$b_t$$, and the executed action is a blend
  $$\hat z_t = (1-c_n)\, z_t + c_n\, b_t,$$
  where $$c_n$$ falls linearly from 1 to 0 during training. Three variants are compared:
  - **PPO only:** the clip provides the start state only.
  - **Latent-only prior:** the blend, with PPO learning purely from reward (similar to APEX).
  - **DAPG:** the blend plus a decaying imitation term $$c_n\,\|\mu_\theta(o_t) - b_t\|^2 / 2\sigma^2$$ in the actor loss.
- **Optimization:** independent PPO with one actor-critic per agent (MLP 512-256-128) and 2048 parallel environments.

At deployment $$c_n = 0$$ and the actor acts alone.

## Results: a single hug

| Metric | PPO only | Latent-only prior | DAPG |
|---|---|---|---|
| Training success, iteration 500 | 0% | 73% | 99% |
| First hug by the actor alone | never | iteration 400 | **iteration 50** |
| Unseen starts: success, strict limits | 0% | **40%** | 4% |
| Unseen starts: success, lenient limits | 0% | **74%** | 44% |
| Arm-to-torso penetration, clip's start | 10.3 cm | **0 cm** | 4.6 cm |
| Planted-foot sliding (cm/s) | 26.6 | 27.3 | **18.9** |

PPO from rewards alone approaches the partner but never completes the hug from any start. Both prior variants learn it. They trade off robustness against naturalness: the latent-only prior is the most robust from 85 unseen starts, while DAPG produces the most human motion, with the agents stepping in and following the recorded style.

![The three final policies from the same unseen start](/images/decap-filmstrip.png)
*Top to bottom: DAPG, latent-only prior, PPO only, from the same unseen start.*

## Results: scaling to many hugs

Of Inter-X's 310 hug recordings, 67 are usable genuine hugs (54 train, 6 validation, 7 test). A goal-conditioned DAPG policy, with the target contacts added to each agent's observation, is trained on all 54. At iteration 1200, with the prior still at two thirds strength in training:

- The actor alone reproduces **91%** of the training hugs exactly.
- On validation clips it does not reach their exact contact points, but performs a valid embrace within strict penetration limits in **50%** of them (up to 83% at iteration 900, which matches what the references themselves achieve).

![Validation clips at iteration 1200](/images/decap-val.png)
*The six validation clips, actor alone (green: hug).*

## Future Work

- **Physics:** the environment is purely kinematic. Training in a physics simulator should correct artifacts such as foot sliding.
- **Egocentric video:** learning from abundant egocentric video converted to motion capture, to cover more scenarios and tasks.
- **Guardrails on contact:** explicit constraints, such as force limits and forbidden body regions, for contact that must never happen.

**NOTE: This is early work and is under active development.**
