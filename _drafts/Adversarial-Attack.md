---
layout: post
title: "Adverserial attacks"
author: "Damian Bogunowicz"
categories: blog
tags: [AI, hidden markov model, tutorial, python, programming, psychology]
image: face-recognition.jpg
---
self driving cars,
no longer need human drivers in the loop
identify human faces airports
security systems that can identify people present on the company ground
adverserial attack

 $$\mathcal{L}=\alpha\mathcal{L}_{in}(x,x')+\beta\mathcal{L}_{out}((f(x'),f(x))+\gamma\mathcal{L}_{s}$$
 
The loss function in general consists of three components. Let's take a look at each of these separate losses.

## Perturbation loss

The goal of the adversarial attack is to take an original, benign input $$x$$ and produce a malicious image $$x'$$ by adding some noise (perturbation) $$\eta$$ to it. In other words $$x'=x+\eta$$. It would be great to fool a network while keeping the noise added to the image to the minimum. This means that one of the primary goals of the adversarial network is to minimize the difference between the original image $$x$$ and the perturbated image $$x'$$. The mathematical formulation of this condition is:

$$ \underset{\eta}{\operatorname{argmin}} \mathcal{L}_{in}(x,x')$$

This means that we manipulate the noise in such a way, that it minimizes the loss function, i.e. a malicious input has possibly close pixel values to the original image. 

Let's take an autonomous vehicle as an example. Let's step into shoes of a villain, who wants to attack a convoy of autonomous cars.  Perturbation loss would be a crucial element of a physical attack on a network. 

##

The authors of the paper Adversarial Generative Nets: Neural Network Attacks on State-of-the-Art Face Recognition    In impersonation (or targeted) attacks, the adversary attempts to be misclassified as a specific other person.
-	In dodging (or untargeted) attacks, the adversary attempts to be misclassified as some other person. 

autonomous car sees sign as something different
impersonate a person using physical artifact lie 




Term               | Definition              |          
--------------------- | :-------------------: | 
a benign image $$x$$                | original input to the network            | 
an adversarial image $$x'$$  | an image that has been altered in order to fool the classifier | 
non-targeted attacks | an attack where the attacker desires to be missclassified by any means|
targeted attack | an attack where the attacker tries to get missclassified to a specific target class |
white box | yfftftffffghf|
black box attack | when the attacker has the access to the model's architecture (parameter |
physical attack/digital attack |ygfyfyyf/|



ine learning models that an attacker has intentionally designed to cause the model to make a mistake; they?re like optical illusions for machines. In this post we?ll show how adversarial examples work across different mediums, and will discuss why securing systems against them can be difficult.

 Explaining and Harnessing Adversarial Examples:  panda image
 
<em>Source of the cover image: http://www.bleum.com</em>
