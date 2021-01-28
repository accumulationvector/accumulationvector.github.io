---
layout: post
title:  "False Data Injection Attacks on State Estimation"
author: "accumulation-vector"
---

This blog is in part serving as a kind of informal notebook for me that I use to keep track of technical facts and notes I'm considering. I'm working through these papers and evaluating them as I currently understand them.

Any critique I have of these papers should be seen through that lens and taken with skepticism. Comments are welcome, but I wanted to preface this post by stating that my interpretation of these papers is a learning process.

A popular attack topic in cyberphysical security journals lately has been variants on the idea of false data injection attacks on state estimation in smart power grids.

State estimation roughly speaking consists of a set of mathematical techniques for monitoring and drafting an estimate of state in an electric grid based on sensor measurements and power system models.

The process of monitoring like this is an attempt to automatically detect bad or incorrect measurements and adjust the current estimation model. Altering the measurements of the grid system can be used potentially as a component in a wide variety of attacks, those causing general disruptions, and more passive attacks.

One interesting attack that people sometimes discuss in this area is the concept of stealing electricity via false data injection attacks on infected sensors/meters. The core idea here is simple, if an attacker alters the measurements of a specifically chosen subset of sensors in a way such that the state estimation is thrown off, they can effectively cloak the usage levels of large amounts of electricity within a limited area of the grid.

It wouldn't make sense to do this sort of attack as an individual (someone trying to not pay their bill), but there are pretty clear usecases for such cloaking in the realm of larger criminal enterprise operations.

The most obvious example would be using stolen electricity to set up an illicit cryptocurrency mining operation. If an attacker could get enough free electricity to run a large mining operation undetected for any period of time this could be a huge source of profit.

Another obvious example would be any illicit factory where the main cost of operation is electrical. If an attacker was running some large scale manufacturing operations whilst doing so on a much smaller electrical bill than their competitors you can easily get a lot of market advantage.

Their margins will be significantly better than their competitors. Even if the attacker only performed the attack intermittently it would reduce their costs slightly.

Finally, probably the most realistic example that has happened in some form in the wild is when attackers attempt to alter electrical hookups to cloak the electrical signature of an illicit drug operation.

Many police busts of underground weed or drug operations have been accomplished by police [audits of electrical usage](https://archive.is/wIbKS) on specific lots. If a law enforcement officer monitors a property that appears near abandoned or rarely used that they note is consuming vast quantities of electrical current, they can achieve standards for reasonable suspicion.

Marijuana operations have also been tracked via the [light frequency emission signatures](https://archive.is/GxlI6) or 
[heat signatures](https://archive.is/l7knd) of lamps used in such operations. This is done via various methods but one such method is [spying on you via your smart meter](http://archive.is/5zcsj).

With current meter and sensor technology, it is possible to tell approximately everything about what specifically is running inside your home. These kinds of techniques have severe privacy implications for normal users, to say the least. The point being that abnormal users who are potentially criminal have a wide variety of motives for wanting to inject false data into smart electrical grid systems.

What makes the attack even more curious is that many people in the industry have characterized this field of smart grid security as pure academic delusion. 

It seems as though there was a bit of a debate on whether the internal systems for error correction in smart grid systems were strong enough already to deal with malicious false data injections.

The first paper (as far as I am aware) to show that the general bad measurement correction model used by most grid systems was not strong enough to deal with these kinds of attacks was [False data injection attacks against state estimation in electric power grids](https://dl.acm.org/doi/10.1145/1653662.1653666) by Yao et al. I'd like to take a bit to talk about this paper and the specific claims it makes.

## False Data injection attacks against state estimation in electric power grids

The main purpose of this paper is to show that previous methods that have been developed for detecting and correcting bad measurements are inadequate in the face of advanced threat actors. The paper argues that theoretically, an attacker can consistently inject false data into the state estimation monitoring system calculation without being detected by any of the current techniques.

The reason their technique works is because most bad measurement detections hinge on a [difference of squares](http://home.engineering.iastate.edu/~jdm/ee553/SE1.pdf) calculation which is actually very primitive. The way the authors get around this is by compromising a minimum number of sensors and introducing bad measurements semi-evenly across subsections of the grid bus. 

The mathematics in the paper is pretty straightforward so without repeating it the core idea is that as long as the attacker is aware of the threshold limits within the system they can remain under them.

The authors use a set of IEEE testbeds to demonstrate two separate attack scenarios with different constraints. One of which limits access to only a certain subset of sensors the attacker can compromise, while the other puts a ceiling on the number of sensors overall the attacker can compromise. The result being that both are susceptible to targeted false data injection attacks and as well as random false data injection attacks.

It is not immediately clear how practical this is for an attacker in the system to weaponize this to actually do damage. The authors don’t go into detail about how this kind of attack could be leveraged into say, stealing electricity or causing damage, they just present it purely as a method for overcoming bad measurement correction equations in the abstract sense.

The attack could conceivably be used in an isolated attack on the electric grid but it would realistically be a smaller component of a larger threat model somehow if it was useful for at all, the authors don’t discuss this. 

They also don’t really discuss what it would actually take for the threat model to work physically. There is an implicit assumption within the threat model about the practicality of the attacker going out and actually accessing these specific meters in the field. 

The paper justified the problem and is foundational for a lot of the papers that came afterwards even if this specific method of data injection for state estimation equations is now considered dated. 

Most papers that come afterwards are all attempts at detecting this kind of false data injection attack. One specific example is [Real-Time Detection of False Data Injection Attacks in Smart Grid: A Deep Learning-Based Intelligent Mechanism](https://ieeexplore.ieee.org/document/7926429) by He et al., which is typical of the kind of solution papers people have come up with.

## Real-Time Detection of False Data Injection Attacks in Smart Grid: A Deep Learning-Based Intelligent Mechanism

The objective of their paper was to use deep learning to detect these false data injection attacks on state estimation measurements in real-time. The authors claim that they are the first to model false data injection attacks for electrical theft with a real-time detection mechanism.

This system acts as an internal classifier and not as a predictor. For this paper's threat model the attacker has knowledge of the system topology, as well as access to load profiles, and the state estimates themselves. The authors artificially generated all of the compromised data themselves internally.

To test the detection mechanism they completed four separate test scenarios. These were done on IEEE test beds one of which was a 118-bus grid and the other was a 330-bus grid. 

For their results, the authors evaluated three scenarios showcasing various aspects of their detection model with the fourth test case putting all of it together with more practical constraints.

The paper falls into a similar problem as previous bad measurement solutions in that, the model assumes that the attackers in many of these cases are going to trip over a certain threshold limit as part of their attack strategy. It is non-obvious if the attacker profiles as described are in any way based on realistic assumptions. 

It seems very possible that the attackers should simply alter their model to go under the threshold limit set by the detection mechanism. If they have the amount of system parameter knowledge that is laid out in the papers threat model they should be able to understand what the thresholding is.

Other than that the results, in general, are kind of questionable and often hard to understand intuitively. First off, the fourth scenario which was supposed to be the real world case performed worse than the other scenarios overall. 

The fourth test scenario does not involve the full 330-bus test model like the other scenarios do. It is unclear why the authors chose to use a smaller bus system for what was supposed to be their real world test model.

The authors' evaluations for their other cases hinged on training data based on several compromised load profiles, environmental noise, and the threshold value of the SVE. It is unclear from the paper if the training data was actually produced in a realistic way, especially the attack training data.

Finally, there is a point that I don't understand that might be a misreading of how accuracy is calculated and measured in the papers model. 

Contrary to what is intuitive, it is not readily apparent why the accuracy of the model goes up as the number of infected busses the attacker has compromised goes up.

The more the attacker is able to alter and control in most state estimation models the more power they have to alter the overall estimate covertly. 

Instead in the authors' model, the accuracy level of the detection rises when the adversary infects more nodes. After looking closely over the paper, it is still completely unclear to me why this is the case.

The point isn't really to showcase the potential issues with this specific paper though or the former paper but just to give some examples of the kind of work being done in the field. It is still a fairly young area of research and there may be fundamental problems with how the threat model people are defending against is structured.

## Is this a real problem?

One thing that is useful to mention to bring this whole conversation back into the realm of reality is discussing whether this problem actually has real world value. It is not at all obvious to me that this problem is actually real from the perspective of a grid electrician.

If this threat model is realistic and something an attacker might want to attempt, is it happening? Is there any evidence of this happening and can we cite examples of these sorts of attacks in the wild? 

The core idea of someone altering state estimation to steal electricity is interesting but in the specific academic formulations of this, it doesn't seem like a viable threat model for defending against.

Can a person actually go out and compromise this many sensors, how long can that many sensors reasonably remain compromised? If you can't be sure that they will remain compromised for a year or more is the attack actually worth much?

There are just so many issues with the defense structure against this threat as well. If an attacker has a 0-day for a meter or sensor, why would they only infect a subset of the grid? It seems clear to me that if the adversary is smart they would just infect all of them and wouldn't risk only working with a smaller amount. 

Does the attacker in most of these threat models have too much information about how the grid works? Does the attacker have an unrealistic amount of information on the system and how state estimations are calculated?

## Extra References

[Security of State Estimation in the Smart Grid](https://www.cse.wustl.edu/~jain/cse571-14/ftp/smart_grid_security/index.html)

[Power System State Estimation](https://www.kth.se/social/upload/518a08d3f27654786295ca51/Lecture_15_StateEstimation.pdf)
