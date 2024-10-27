---
title: "FPGA-based Dynamic Image Processing using Zynq 7010"
excerpt: "OV7670 Camera interfaced with Zynq 7010 FPGA to output TMDS data displayed on monitor"
collection: projects
permalink: /projects/img-proc/
date: 2024-10-20
gif: image_proc.gif
category: electronics
---

So after my internsip at IIT Madras, I became interested in Robotics Vision. I wanted to develop a fast image processing system that can essentially replace off-the-shelf cameras like RealSense and Oak-D. However, I was devoid of resources and funds to buy a cheap stereo camera, so I decided I will do it with what I have. I had only one monocular camera(OV7670) and I interfaced it with an FPGA to create a fast image processing logic.

This work was also accepted and published at [IEEE International Conference on Advances in Computational Intelligence and Communications 2023](https://ieeexplore.ieee.org/abstract/document/10435029) with me as the solo author.

## Features

- Uses two Video-Direct-Memory-Access channels instead of one two parallelize the read/write process.
- I wrote a custom Dynamic Clock Generator script on Verilog to replace the Digilent Phase-Locked-Loop IP to adjust frequency on the fly. This made the system latency free.
- This system can now also be used with two OV7670 monocular cameras to create stereo vision that is capable of replacing high-end cameras. This is project is also a testament to my desire to make robots economically feasible to everyone.

## Technologies Used

- Reconfigurable Computing
- Verilog
- Robotics Vision

[Link to Project Repository](https://github.com/yourusername/project-repo)\
[View the project on YouTube](https://www.youtube.com/watch?v=82h42gcCD0A)