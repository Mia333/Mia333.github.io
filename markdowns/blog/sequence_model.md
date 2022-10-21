---
layout: info
title: Sequence model
permalink: /blog/sequence_model/
---


In this blog, I summarize some Paper, focused on topics, Conditional VAE and Probabilistic Movement Primitives, Human-Robot Interaction.


# 1. Accurate and Diverse Sampling of Sequences based on a "Best of Many" Sample Objects

[[paper]](https://arxiv.org/abs/1806.07772) [[github]](https://github.com/apratimbhattacharyya18/CGM_BestOfMany)

 2018 CVPR paper from Corporation of Max Planck Institute for Informatics and Saarland Informatics Campus. This paper applies the CVAE combined with LSTM in trajectory prediction and with Conv-LSTM in image sequence prediction problem.

Accurate and Diverse Sampling of Sequences based on a "Best of Many" Sample Objects.



**Dataset**: MNIST stroke completion, containing 60000 for training dataset , 9984 for test dataset

x_data (60000,10,2)  y_data(60000,107,2)

<img src='/assets/imgs/MNIST.png' width='440'/>




<img src='/assets/imgs/MNIST2.png' width='440'/>



* **CVAE**  

empirical lower bound using Monte-Carlo Sampling

<img src='/assets/imgs/CVAE_MC.png' width='440'/>





* **Many Sample objective**

encourages the diversity in the generated samples, since has multiple chances to draw samples. has numerical stability issue. 

<img src='/assets/imgs/MS.png' width='440'/>



* **Best of Many Samples**

  approximate the sum with maximum 

<img src='/assets/imgs/BSM.png' width='440'/>



* **Model architecture** for structured trajectory prediction

<img src='/assets/imgs/model_architecture.png' width='440'/>




* **Result of BMS**

fix initial stroke length at 10, generate diverse samples from LSTM-BMS model. clustered using k-means

<img src='/assets/imgs/BMS_result.png' width='640'/>

# 2. Learning and Inferring Movement with Deep Generative Model

This paper is from Tshinghua University. They propose CMP(Contextual Movement Primitives), which effectively generates trajectories for specific context and task in an end-to-end manner.

Problem in learning and inference movement:
* high dimensionality
* dependency

formulate motion planning problem as learning on a directed graphic model and deep generative model.

directed graphic model introduce the probabilistic representation of trajectory.
deep generative model make it possible to perform learning and inference on the probabilistic motion planning model from demonstrations.

* 1. incoporates the task descriptors and context information for long-term planning
* 2. combine dynamic systems for robot control
	-- robust to pertubation
	-- trajectory feasible 
	-- goal-convergence
CMP(Contextual Movement Primitives) 

### directed graphic model:
introduce the probabilistic representation of trajectory
### generative model

* contextual information: RGB image of working scene
* task descriptor: one-hot tensor

* Dynamic Control System
represent and learn the force space trajectory instead of position trajectory, which allows robot control through a dynamic control system.


## Model architecture
* 1. CMP generator (CMPG) 
input: contextual information c and task descriptor t. perform an inference on the learned graphical model to produce a representation w of the trajectory.
* 2. localization network (LN)
explicitly predict the position information d of object-of-interest as the goal constraints g in MCS.  Contextual information c with task descriptor t as input, predict objectiveness map.
* 3. motion control system (MCS)
(1). MCS: represent trajectory of position
(2). MCS as a dynamic control system: compute the probabilistic representation of force space trajectory w from a demonstrated trajectory of position tau,


##  Probabilistic Movement Primitives 
Pro MP describe a probability distribution over trajectories.

it parameterizes the trajectory distribution by the distribution of weight and a fixed variance.

The probability of observing a trajectory yao given weight vector w is given as a linear basis function model.



# 3. Multimodal Probabilistic Model-Based Planning for Human-Robot Interaction
[[paper]](https://arxiv.org/abs/1710.09483)
[[github]](https://github.com/StanfordASL/TrafficWeavingCVAE)

Recurrent CVAE

learn human action policy conditioned on interaction history and a candidate robot future action sequence







# 4. Multimodal Probabilistic Model-Based Planning for Human-Robot Interaction

[[paper]](https://arxiv.org/abs/1710.09483) | [[Github]](https://github.com/StanfordASL/TrafficWeavingCVAE) | [[Video]](https://www.youtube.com/watch?v=R5ByqhDer8I)



2018 ICRA paper

* **Dataset** : **TrafficWeavingBag**


