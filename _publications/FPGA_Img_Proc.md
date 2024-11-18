---
title: "An FPGA based Real-Time Video Processing system on Zynq 7010"
collection: publications
category: conferences
permalink: /publications/FPGA
excerpt: 'Real-Time Image Processing involves the transformation of incoming signals, primarily from a camera, into a format that can be readily interpreted by a display device. This process is heavily reliant on precise timing constraints, demanding efficient hardware execution. This paper proposes an innovative method for interfacing the OV7670 Complementary Metal Oxide Semiconductor (CMOS) Camera with an FPGA-based Real-Time Image Processing system on a Zynq 7010 platform, using the open-source Digilent Dynamic Clock Generator. The architecture is characterized by it’s parallel processing capability of both controlling the camera output signals and processing the signals and converting them from RGB to DVI format on the fly. In lieu of the traditional PLL based clocking wizard, which provides a fixed clock signal, the open-source Dynamic Clock Generator has been incorporated in the architecture to generate the essential pixel clock, meeting the real-time clocking requirements. The RGB to DVI(Digital Visual Interface) block has been coded in VHDL to convert the output from AXI4-Stream to Video Out Xilinx IP Core to TMDS (Transition-Minimized Differential Signaling data, to be interpreted by an HDMI compatible monitor.'
date: 2023-12-13
venue: 'Published at IEEE ICACIC'
slidesurl: 'https://ieeexplore.ieee.org/document/10435029'
paperurl: 'https://ieeexplore.ieee.org/document/10435029'
citation: 'Antareep Singha.'
---

This project has been one of my most challenging ones. I had worked with FPGAs before at IIT Madras and I knew that if I could integrate cheap FPGAs with robotics, deployment will be much easier. The problem that intrigued me while working at IIT Madras was when I saw other PhD students at the OCEAN lab on image processing. Of course they had Zynq Ultrascale and other high end devices but I wanted to start off where I had left. So, I used all of my stipend from IIT Madras and purchased a Zynq 7010 device. 

Reading FPGA literature, I realized that most architectures used clocks that were Digilent IPs, including PLLs. A great starting novelty brownie point for me was identifying that a custom clock tailored specifically to adjust to run-time frequency fluctuations. I created the logic for a Dynamic Clock Generator using VHDL. Another area of novelty was the fact that Video Buffer read/write operation happened serially which was a bottleneck. I parallelized it with two Video Direct-Memory-Access channels and voila! My very own Image Processing System was ready.

I documented my project and sent it to the IEEE International Conference of Advances in Computational Intelligence and Communication 2023, upon being advised by my professor. Two months later, I got the acceptance and I had my first chance at presenting my work and having a publication.