---
layout: post
title:  "Anonymous Delivery Mixnet Issues"
author: "accumulation-vector"
---

I recently stumbled onto a paper by AlTawy et al. titled 
[Lelantos: A Blockchain-based Anonymous Physical Delivery System](https://eprint.iacr.org/2017/465) which gave me a burst of ideas. I'm interested in discussing how mixnet protocols could be applied to physical objects and why some approaches seem to work while others don't.

>In this work, we present a blockchain-based physical delivery system called Lelantos that within a realistic threat model, offers customer anonymity, fair exchange and merchant-customer unlinkability. Our system is inspired by the onion routing techniques which are used to achieve anonymous message delivery.<br><br>Additionally, Lelantos relies on the decentralization and pseudonymity of the blockchain to enable pseudonymity that is hard to compromise, and the distributed consensus mechanisms provided by smart contracts to enforce fair irrefutable transactions between distrustful contractual parties.

I've previously seen arguments for similar ideas posted on cypherpunk discussion boards. It could be said that physical-world storage/delivery mixnets in various forms are an essential component of fictional crypto-anarchist sovereign zones. In the abstract, the concept poses a unique technical implementation challenge.

I won't summarize the paper here, but I'll make a few framing comments on the work. To summarize briefly, the Lelantos paper presents an interesting protocol that utilizes smart contracts to establish fair exchange within delivery nodes.

It uses an odd approach that I don't think I've seen anywhere else, but I will argue it doesn't achieve security that would satisfy the constraints of people who are obsessive about anonymity.

As a practical note, it is unclear to me how the author's approach could be turned into a workable startup company since it seems to require the bootstrapping a rather large user ecosystem from the very beginning in order to have even minimal proper functionality. It is not at all clear that demand for their system could be generated at the levels required to make it function properly, let alone profitably.

Putting the profitability of such a scheme aside, even in the abstract there are many details in this paper that are never considered, but that actually make up the core of the problem space. Not addressing them shows that this protocol can't really solve the general physical mixnet problem, only a neutered version of it.

There are also just many trivial implementation details that are not considered by the paper at all. We can imagine the customer $$ C $$ gets identified whilst they are picking up a package from $$ DC_n $$. In the paper, this is explicitly not addressed at all.

>In our model, we do not consider external attacks where an individual or a GPS device can be used to track the package or the use of cameras at pickup locations which can be utilized to identify customers.

The obvious way to eliminate this problem is by not having the delivery companies $$ DC $$ function as literal companies but instead having all interaction done by one centralized DAO on-chain. The mechanism would act more like a decentralized Uber than a protocol that various delivery service companies individually interact with. 

In the modification, I'd propose to fix this each $$ DC $$ in the protocol is an individual person using a phone app to accept delivery jobs on the fly. Each person in the delivery mixnet passes the package off to another delivery person in the chain via some mixnet routing procedure.

The last person (the customer), is indistinguishable from another delivery driver in the chain. The end customer can instead sign their key verifying final delivery of the package, and thus releases the contract payments held in escrow. What I'm saying is obviously an incomplete outline, but I hope is enough to give a general impression of what I'm saying.

In this kind of setup, there is no longer an issue with adversaries sitting on the company pickup location or tracking every single $$ DC $$ vehicle in the small ecosystem. Instead, we are creating a different problem, related to the accountability and reputation of different drivers in the system. Lelantos avoids this by having the domain explicitly be large visible delivery entities.

The Lelantos authors explicitly assume that there is some degree of out-of-protocol legal oversight and accountability for the delivery company. The individuals doing these package movements on the other hand presumably would be pseudonymous. They would not be tracked by GPS via some protocol mechanism as this would violate their pseudonymity.

There is a massive incentive for deliverers to steal packages or attempt to deviate arbitrarily from the protocol in some malicious way. When there is no longer legal accountability this requires the introduction of all the typical crypto-anarchist constructions. These could be reputation systems, escrow, collateral payments, or other mechanisms, essentially all the typical things.

In the paper, delivery cost upper bounds are set ahead of time via $$ \$MaxHopFee $$ and calculated by the contract prior to the initial acceptance by the customer.

 $$ \$ MaxDeliveryFee = n × \$MaxHopFee $$

I presume my modification here and the various extra collateral that it would require would increase the cost for senders, deliverers, and receivers engaging with the network. Such a price increase would (given what I think is a realistic assumption about market conditions) reduce the pool of mix users to the point that keeping strong anonymity would prove very difficult.

If we bracket off these issues for a second and assume that my proposed modification here could be constructed in an abstract setting. Specifically, if it was able to function in some way that would allow for anonymous mixnet delivery with multiple drivers handing off packages between one another, interesting ideas follow.

First, it should be possible if packages are not externally immediately identifiable and are stored for example in standardized metal safe deposit box containers, to keep the cycle of delivery going indefinitely with a large enough payment. As a remark though, this would require some protocol mechanism that would allow periodic releases of payments prior to end-delivery which could become an attack surface if incorrectly constructed.

To put this another way, such a delivery network could be used as a decentralized storage unit that continuously moves the storage around between drivers. It allows a user with a large amount of monetary resources to chain the package between delivery drivers as many times as they want to pay.

A simple analogy for this is a juggler who is constantly inserting and removing items in their cycle but keeps one up in the air continuously for several cycles without removal. All balls up in the air are in theory indistinguishable from one another. 

While I find this compelling to talk about, the issues with designing a protocol that can withstand cypherpunk standards for decentralization and anonymity of all participants are enormous. It is clear that everything I'm saying here is incredibly improbable to realize outside of an ideal functionality.

People in the subculture are obsessed with this abstract idea of decentralized purity and creating something that can exist in the form of a company. A lot of the trust incentives and the constructive nature of the original paper fall apart under their own weight when we want the drivers, senders, and receivers to be anonymous/decentralized nodes.

## House Storage Mixnets
 
What we have done here is essentially construct something which requires a very complicated machinery to function because of specific constraints. It includes anonymity, composability, and a series of collateral payments, all of which we are imposing to make it fit a theoretical ideal. When you look at it through this lens it seems monumentally infeasible.

The intriguing thing here is that examples of physical world storage mixing exist in the world today. Thinking about how this is done in practice can be illustrative, we can compare the cypherpunk model that doesn't exist to something that actually does.

I am going to look at the simple example of how drug gangs move around their contraband stashes between various houses in their neighborhoods. For this example, I'll talk in terms of a [fictional gang setup of this from the TV show The Wire](https://www.youtube.com/watch?v=pvRXP1yyQbg).

The characters control a delineated zone of territory that they deal drugs inside of. This is controlled in a sense by a dealer $$ D $$ , in the show, this is Avon Barksdale. He controls several zones and has a capo or manager control a set amount of contraband stored in the area under their management.

In this area, there is a subset of houses that are under presumably under the control of $$ D $$ by in a given zone. These are available for lower participants $$ P $$ to store contraband within. This is achieved by coercing the owners, payment of bribes to them, or the house is simply abandoned.

At any given time each package of contraband is located within a singular house from the fluid set that is under control. After an interval, the contraband is moved by couriers ($$ P $$), between various houses randomly so that the location of the contraband is secret. The movement of the couriers could be done randomly or following some set protocol.

The point of this model is to show that they have actually achieved the design of a non-cypherpunk physical storage mixnet. Not only is it feasible, but it is robust enough that it impedes police investigation and has been used in the real world by various formalized gangs.

So why does this model work, and arose organically in several areas across the world in response to law enforcement tactics, whereas the cypherpunk conception of physical storage mixnets has not? Let's look at the differences.

First, in this model, the $$ D $$ can see the entire house mixnet network state at any given time. The fictional Avon Barksdale can know where his items are if he wants to know and can figure out which $$ P $$ put them in which house. 

To say this more generally, the couriers aren't anonymous to the owner of the stored item. If they steal it or do something outside the protocol, $$ D $$ can attempt to penalize them monetarily or with aggression.

Another key difference here is the threat model is not the people engaging in the protocol. All concealment is only intended to be secure against some external entity that is attempting to find contraband. Various participants may or may not be able to gain information about where a given package is at a given time.

It seems obvious that this is actually pretty inferior to the protocol where nobody knows anyone else, and all penalties are assigned and agreed to upfront. In the housing mixnet model $$ D $$ does not establish any collateral with the participants other than the knowledge of their identity and residence. 

This contrasts sharply with a cypherpunk attitude where everyone is assumed guilty until proven innocent and forced to make monetary collateral for all potential penalties ahead of time. It is secure against participant robbery in this sense. Security against adversarial presence is also guaranteed or at the very least measurable. People in the network know almost nothing about global network state at any given point without making up a substantial percentage of the participants.

In the house mixnet model, law enforcement can infiltrate the gang with only a few nodes and possibly gain sufficient information from internal information leaks about the process for a warrant. They can use this information to build up a predictive heuristic-based around this information to identify stash houses.

If this model is so obviously worse, why does it function properly and exist while the cypherpunk models don't? It is entirely a matter of human psychology and market forces. People who are interested in low-level grey market gigs rather than normal jobs are mostly in it because they are broke and looking for quick cash. 

The main difference between the models is that one requires a market where people who would do this kind of work put up  collateral ahead of time. The other requires no collateral whatsoever even though the potential penalties are in fact steeper.

This is a general issue that pops up across all sorts of reputation and collateral based escrow crypto-anarchy systems. Simply put in our culture if you require collateral from people in order to do their job they will be repelled. 

People have time preferences that are an implicit part of their incentive psychology that are not altered very easily. In my opinion, the core failing of crypto-anarchist projects solely rest on portions of protocols that don't compose well with participant's psychological and cultural sensibilities.

In privacy and anonymity research circles there is a pervasive rigidity toward incentive structures that needs to be altered. One idea is structuring wrappers around protocols in such a way that these incentives are abstracted away from the end-user entirely.

Another core problem we can see here is when you define a threat model as being "everything and everybody" to create trustlessness there is an outward appearance of security. If this security requires massive technical apparatuses that nobody will follow or implement, containing improper incentives, this appearance of security is wholly vacuous. 

## Future of Delivery Mixnets

It should be immediately pointed out that the new paradigm of [dropgangs](https://opaque.link/post/dropgang/) I've neglected to mention throughout this post are a hybrid of the two structures. They have a top-down model where dealers can see network state but the participants and dealers are somewhat anonymous to one another.

The incentive structures were designed well enough that they have been implemented in the real world across several European countries. In a few years, we can probably come back and look at the experiment and see after several iterations what kinds of experiments they come up with.

For now, it is yet to be seen if the experiments will last and evolve from their current form or if the idea will die out over time. The coordination via telegram bot texting automation is definitely a setup worthy of study and is similar in subject to some recent [short fiction](https://archive.is/AqvYT).

Again though this is an example of tossing purity by the wayside in favor of creating actually implementable protocol structures that people like interacting with. 

Everything can be as technical or as well-engineered as people want it to be using as many instruments as possible, but if the human incentives in the equation are not correct it is all for naught.