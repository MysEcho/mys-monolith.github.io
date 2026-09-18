---
title: "Imagine-TAMP: Imagination-Guided Task and Motion Planning in Partial Observability"
collection: publications
category: conferences
permalink: /publications/imagine_tamp
excerpt: ''
date: 2027-09-15
venue: 'IEEE International Conference on Robotics and Automation(ICRA)'
slidesurl: ''
paperurl: 'https://arxiv.org/pdf/2609.20396'
citation: 'Antareep Singha, Shivaram Kumar, Yoonwoo Kim, and Yoonchang Sung'

---

Robots operating in cluttered environments must often manipulate objects whose locations are only partially observable. A central challenge is deciding whether to acquire another observation or to first manipulate objects that may occlude the target. Conventional task and motion planning (TAMP) approaches typically make this decision using symbolic action costs or expensive geometric planning, neither of which adequately captures how likely an observation is to reveal an
occluded target. We introduce IMAGINE-TAMP, an interleaved planning and execution framework that uses semantic and geometric imagination to compare alternative task-level strategies under partial observability before committing to expensive motion planning. A vision-language model shapes a particle belief over target locations using commonsense relationships between the target and visible objects, while a generative scene model estimates plausible geometry in unobserved regions. Given a target hypothesis and imagined scene, IMAGINE-TAMP generates multiple symbolic plan skeletons and assigns nonunit costs that approximate both manipulation effort and target visibility from sensing actions, distinguishing a short but poorly informative observation strategy from a longer strategy that first manipulates an occluder to better expose the target. The selected skeleton is then refined into a feasible continuous plan and executed, with new observations updating the belief and triggering replanning when necessary. Experiments show that imagination-guided evaluation improves observationversus-manipulation decisions: in viewpoint-constrained shelf scenes, non-unit geometric evaluation increases success from 46.0% to 84.0%, while semantic belief shaping further reduces manipulation and replanning. On a real-robot, the complete system reduces planning time by 32% relative to a geometryonly ablation.