---
layout: post
title: "The Braincraft Challenge by Nicholas Rougier - Computational Neuroscience's ARC AGI challenge"
date: 2025-07-06
tags: [braincraft, neuroscience]
---

[under construction]

Nicholas Rougier launched a [braincrafting challenge](https://github.com/rougier/braincraft) which, I find, shares quite some similarities with Francois Chollet's [ARC AGI challenge](https://arcprize.org/).

The first Braincraft task (of a series of presumably increasingly complex tasks) confronts researchers from computational neuroscience with a conspiciously simple problem: A simplified circular robot controlled by a neural network has to navigate a small figure eight-shaped maze where one side contains an energy source. The robot is constantly moving (as long as it's not hitting a wall) and needs to visit the energy source as often as possible to avoid running out of energy. Controls are simple as well: the robot can only steer left or right with a continuous control signal provided by the neural network. The network is made up of up to 1000 continuous rate-coded neurons which can receive input from an array of 64 distance sensors placed in the front of the robot, a binary signal indicating a wall collission, the robot's current energy level and a constant input. 

{% include figure.html
   src="/posts/img/braincraft_1.png"
   alt="Gameplay footage"
   caption="Fig. 1  The robot "sees" only in a relatively narrow band in front of it."
%}

The environment we are presented with appears very similar to rat mazes which have been used by experimental psychologists and later neuroscientists for over a [century](https://en.wikipedia.org/wiki/W._S._Small#Implications_of_maze_learning_and_rats). By using careful experimental design, ever more sophisticated brain imaging techniques, statistical models and simulations, neuroscience as a whole strives for understanding how neurons implement minds, but Rougier laments that "we still lack an integrated, functional mini-brain". By "Mini-brains", in this context, he does not refer to lumps of neurons grown in a [dish](https://doi.org/10.1016/j.neuron.2022.09.001) but neural network models *in silico*. Rougier attests (and I, for one, agree) that most models in computational neuroscience are too specialized and geared towards abstract settings and thus can't be employed in scenarios involving dynamical control and embodiment. Effectively, these models are neither integrated with a body nor a greater environment, but functionally isolated - they are build for solving a narrowly defined task, not for complex settings requiring flexible integration of multiple functions.

Now, how could this simple task pose difficulties for the status quo? While it's called the "Simple decision" - in reference to the choice between left and right - this task incorporates elements of dynamical control problems in the real world. First, the controller does not have perfect information - the robot lacks any immediate sense of orientation, the distance sensors are covering only the central 60° of the robot's front and the collision sensor does not inform about *where* the collision happend. This will lead to situations where the robot is close to a wall on its side where it won't have any sensory information of the wall and when it collides there will be no straight forward way to get unstuck, since it can not know where the wall is located. Thus, one major subchallenge is to give the robot a memory or a spatial representation of its surroundings so it can avoid obstacles that are currently not visible.

{% include figure.html
   src="/posts/img/braincraft_2.png"
   alt="Gameplay footage of cutting a corner"
   caption="Fig. 2  There's no way to tell from immediate sensory input whether the robot should turn left or right in this situation."
%}

Giving neural networks some spatial memory of course is not an excessive demand. In computational neuroscience, there are many models for navigation and spatial memory, and even one recent model exploring the coding limits of small networks consisting of "[a handful of neurons](https://doi.org/10.1038/s41593-024-01766-5)" for spatial navigation which can be examined in the living fruit fly, whose computational structure is [relatively well understood](https://doi.org/10.1016/j.conb.2021.12.001). However, as far as I can tell, these kinds of models have been rarely tested in settings where they are used to steer behavior and, even more importantly, they are mostly hardcoded. With the Braincrafting challenge, contestants are not allowed to directly submit a network but the *training procedure* for generating one. In a sense, developers need to play Evolution to come up with a mechanism for creating an adaptive system from scratch. Further, training time is limited to the equivalent of 100 seconds of compute on a 2020 MacBook Pro. Thus, the main challenge lies not in designing a network architecture that could solve this task with unlimited optimization time (through training on data or hand crafting), but finding one that is able to learn to solve the task with extreme efficiency. From my estimates, the training budget for this task will amount to no more than 60 short episodes or 10.000 state transitions. [Current RL appraoches](https://doi.org/10.48550/arXiv.2111.00210) seem to work with one order of magnitude more game play experience and much more elaborate neural architectures then what is allowed in Braincraft, so this will be challenging

This is were the comparison with the ARC AGI challenge comes to mind - at its core sits the formal (yet incomplete) [definition of intelligence by Francois Chollet](https://doi.org/10.48550/arXiv.1911.01547) as *the rate of information-to-skill transfer*. Under this definition, a system can be said to be intelligent if it is able to adapt to new tasks after minimal exposure. (More formally, Chollet invokes the idea of a "skill programm" - an artifact created by the intelligent system that interacts with the task). Conversely, task performance in itself is not necessarily a marker of an intelligent system, since it could also be due to extensive training or, more importantly, the intelligence of the creator of the system. With these insights in mind, Chollet build the ARC benchmark to point out the weaknesses of current machine learning approaches. In ARC, each task is a unique combination of simple concepts which need to be inferred from two to three demonstrations (see Fig. 3). While the first iteration of the ARC challenge was "solved" with massive amounts of compute by OpenAI models (they solved the tasks, but did so very inefficiently), the recently released second iteration seems to be extremely hard for current models which average a 2% success rate. Regarding the amount of available training data and adaptability, Rougier plays a similar game with computational neuroscience models.

{% include figure.html
   src="/posts/img/braincraft_3.png"
   alt="ARC task example from Chollet's paper"
   caption="Fig. 3  An ARC task involving the concepts of similarity and count."
%}

What can be gained from solving the Braincraft challenge? Is it even possible to find a meaningful solution to the "Simple" task given so little compute? Compared to ARC, Rougier's task runs the risk of encouraging "meta-overfitting" to the task at hand since there is only one task and not a diverse set (yet) - one route to success for contestants at this stage would be to find a brute force solution in an extended training regime and compress it by any means so it can be "unpacked" during training using training data as the decryption key (aprocess we could then call learning). When cast this generally, this appears to be the only solution available - since there is so little data available during training, the model cannot learn a "world model" from scratch - it will have to rely on strong inductive biases derived from human intuitions or prior training.

This would still leave us with an interesting race - human intuitions vs brute force optimization - whose solution is more suitable to being unpacked during training, and what are the techniques people will use for this?


current neural networks are not very intelligent, they are either trained on internet-scale data, with limited adaptation capabilities, or, as is often tha case in computational neuroscience, mostly handcrafted solutions to narrow problems which are not made for adaptability in the first place. 


whose fundamental purpose is to give us a better understanding of how the brain adapts to our complex environmentsto give good answers to the central question of adaptability.


While experimental (animal) psychology was largely superseded by neuroscience 
