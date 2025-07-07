---
layout: post
title: "The Braincraft Challenge by Nicholas Rougier - Computational Neuroscience's ARC AGI challenge"
date: 2025-07-06
tags: [braincraft]
---


Nicholas Rougier launched a little [challenge](https://github.com/rougier/braincraft) which I find shares quite some similarities with Francois Chollet's [ARC AGI challenge](https://doi.org/10.48550/arXiv.1911.01547).

The Braincraft challenge mainly asks researchers from computational neuroscience to find a solution to a conspiciously simple task: A simplified circular robot controlled by a neural network has to navigate a small figure 8 shaped maze where one side contains an energy source. The robot is constantly moving (as long as it's not hitting a wall) and needs to visit the energy source as often as possible to avoid running out of energy. Controls are simple as well: the robot can only steer left or right with a continuous control signal provided by the neural network. The network is made up of up to 1000 continuous rate-coded neurons which can receive input from an array of distance sensors placed in the front of the robot, a binary signal indicating a wall collission, the robots current energy level and a constant input. 

{% include figure.html
   src="/posts/img/braincraft_1.png"
   alt="Gameplay footage"
   caption="Fig. 1  The robot "sees" only in a relatively narrow band in front of it."
%}


