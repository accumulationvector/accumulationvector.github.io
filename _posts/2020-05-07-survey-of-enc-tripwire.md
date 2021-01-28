---
layout: post
title:  "Survey of Encryption Tripwire Techniques"
author: "accumulation-vector"
---

For many years now, security researchers have talked about various side-channel attacks on full disk encryption. There have now been replications of several key recovery attacks, and [cold boot attacks](https://www.usenix.org/legacy/event/sec08/tech/full_papers/halderman/halderman.pdf) showing that many variations are valid and semi-reliable.

That said, as far as is publically known, these techniques have never been used in practice by any country as part of a criminal investigation. The technique most commonly used by law enforcement on record to bypass full disk encryption has not relied on any sophisticated techniques. 

They have simply been able to consistently get at the target's computers in a fully unlocked state. The typical method is for agents to create a diversion of some sort when they are certain that the target computer is unlocked. 

In the process of creating a diversion, agents can confuse and disarm the target before they can lock their encryption or know what is going on. There are several notable examples of this, the most famous recent example being the arrest of Ross Ulbricht.

>As soon as Der-Yeghiayan could confirm that Ulbricht was logged into the site, FBI agents entered the library. <br><br>
Two plainclothes FBI agents, one male and one female, walked up behind Ulbricht and began arguing loudly. This staged lovers' tiff caught Ulbricht's attention long enough to distract him from his laptop.<br><br>
As soon as Ulbricht looked up, the male agent reached down and slid the computer over to his female colleague, who quickly snatched it up and handed it over to Kiernan for further investigation. Understandably alarmed, Ulbricht stood up sharply, Kiernan told the jury.<br><br>
But he did not resist arrest, and Kiernan was able to access the computer — a Samsung 700z — to collect evidence almost immediately. Kiernan recalled taking his "brand new USB" and extracting all of the files from Ulbricht's laptop before taking photos of the computer with his FBI-issued Blackberry.

<cite>&mdash; [The FBI staged a lovers' fight to catch the kingpin of the web's biggest illegal drug marketplace](https://www.businessinsider.com/the-arrest-of-silk-road-mastermind-ross-ulbricht-2015-1) -[Archive](https://archive.is/nuWTW)</cite>

This is the archetypal case for the method. Agents make sure that the target is logged in, they stage some sort of incident, and then disarm the target quickly before they know what happened. 

Another case following this pattern is the arrest of Alex Cazes. For this, the FBI created a scenario in which they crashed a car into Cazes' house to get him to come outside in a hurry.

>Officials from the Federal Bureau of Investigation, Drug Enforcement Administration and Royal Thai Police crashed a squad car into the front gate of Cazes’ Bangkok mansion to lure him into reach before he could encrypt or wipe digital evidence connected to the crimes.<br><br>
That evidence – administrative accounts logged into AlphaBay forums and servers along with text files identifying password credentials for AlphaBay website and hosting services – was located on an open laptop police found in Cazes’ bedroom while conducting a search and entry raid of his home.<br>

<cite>&mdash; [US Government Seizes Lambo and Crypto Millions from Dead Dark Web Kingpin](https://www.coindesk.com/us-court-seizes-lambo-and-crypto-millions-from-dead-dark-web-kingpin) -[Archive](https://archive.is/qbzeq)</cite>

Finally, there are a few notable examples of successful encryption by a target being arrested. In the arrest of Jeremy Hammond he was able to successfully encrypt his laptop before his arrest. It should be noted that he only did this by making a mad dash away from agents, just barely making it to his computer in time. 

In this case the agents were still able to decrypt his computer, not through a sophisticated technique, but via a basic brute force attack. Hammond used an extremely simple password that was easily cracked.

>When agents armed with assault rifles raided his home in 2012, the hacktivist dashed to his bedroom to slam shut his encrypted Mac laptop.<br>

<cite>&mdash; [FBI’s most wanted cyber criminal caught out](https://www.telegraph.co.uk/news/worldnews/northamerica/usa/11229241/FBIs-most-wanted-cyber-criminal-caught-out-by-pet-cat-password.html)
-[Archive](https://archive.is/0PAvD)</cite>

These techniques are becoming the consistent playbook of the FBI and other global agencies in dealing with full disk encryption. In response to these incidents there have been several software and hardware based solutions to hobble this category of law enforcement methods. 

Most of these approaches take some form of a tripwire which triggers a shutoff or some series of actions. Tripwires have been shown to be highly successful as a full disk encryption activation solution in a few notable arrests.

>It appears as if Ackroyd’s computer was “set up to trigger a wire” that erased the drives and data on his computer when triggered. This is exactly what happened when police raided his home and attempted to confiscate his computer.<br><br> The report noted that as he was being arrested, Ackroyd kept trying to kick over his tower computer. When the computer was moved, a small tripwire caused the computer to turn off erasing all the sessions running on his computer.<br>

<cite>&mdash; [Court document provides rare glimpse into the lives, minds, and activities of the arrested LulzSec hackers](https://www.geekslop.com/2012/court-document-pcmh-lives-minds-activities-of-lulzsec-hackers) -[Archive](https://archive.is/UV3AR)</cite>

In the case of kayla's arrest the hacker was able to successfully trigger a tripwire which eliminated evidence. Here I'm going to outline the many methodologies that have been developed for these types of security threats and propose some initial groundwork of a few novel solutions. 

This is purely intended to be security research. In many areas of the world (UK, France, Australia, etc) refusing to give up your password is [considered a crime](https://en.wikipedia.org/wiki/Key_disclosure_law) in and of itself.

## Software Based Solutions

Software based solutions have made up the majority of approaches thus far. All of these methods should work in theory, although to my knowledge there has never been a case where someone was arrested with any of the following anti-forensic software configured.

The basic principle these solutions use is that you have a process monitoring a specific aspect of the operating system, that when altered runs a script to either shutdown the computer or perform some anti-forensic task. 

The thing that is monitored can essentially be anything you might want, you could monitor [ACPI Modules](https://wiki.archlinux.org/index.php/ACPI_modules), or anything that generates a [udev event](https://wiki.archlinux.org/index.php/Udev). The scripts can be modified to trigger any desired routines, like erasure of files or other obfuscating measures. 

One way of using these programs is whitelisting. The idea is that if an adversary grabs an unencrypted laptop and attempts to copy its contents by plugging in some unknown USB device, the script will detect a non-whitelisted device and trigger the script. 

This could also be used to disabling common forensic tools like the Jiggler. The [Jiggler](https://archive.is/dwGWT) is a hardware tool used by law enforcement to keep a computer awake while they are attempting to do a forensic investigation. 

These are essentially mouse emulators in the form of a small USB device. They can be programmed to do a series of repetitive mouse movements or various actions.

The scripts can also be configured to do the opposite, that is, when a specific device or cable is removed, the script performs some action. The process is continuously checking that a specific device or cable is in a specific port. If the USB device is removed, the script immediately runs anti-forensic routines. 

As a simple example a USB plugged in could be attached to a laptop owners wrist with a cable. If the laptop was jerked away like in the Ulbricht case, the script could then trigger a shutdown. These methods can in theory be set to trigger for any action that generates a udev event.

Most of the methods I'm about to list here involve USB removal events as a trigger, but as attackers become wise to these methods, in the future more obscure triggers will probably become common. 

One example could be unplugging an AC charging cable, which generates a udev event that could be listened for. You can write a complex set of udev event triggers listening for lots of different types of events.

One popular solution that is the [USBKill Project](https://github.com/hephaest0s/usbkill). The software is easy to use and can be configured for a wide variety of the things mentioned above, even more. Here is a [Youtube demonstration of USBKill](https://www.youtube.com/watch?v=768feMQjJTI), showing how to configure the script. It is a very simple script, but seems to work as advertised.

Another proposal is [BusKill](https://archive.is/R7tMD) which nearly the same solution as USBKill in principle, but done manually using a magnetic breakaway cable, possibly attached to the target's wrist via a lanyard. They are essentially just buying a magnetic breakaway adapter and setting a single udev rule to lock the screen when the magnets break contact. The script they provide here is essentially how you would probably want to go about writing udev triggers for this kind of thing in my opinion.

A non-USB solution is [Blueproximity](https://github.com/Thor77/Blueproximity) which again works on the same principle, but here the trigger is bluetooth proximity. The idea here is that if a bluetooth device moves a specific distance from the designated computer, a script is then triggered. 

This solution is probably less interesting than the former two for the threat model used in this article. It could be thwarted by the attacker not moving the target's body away from the computer when they are trying to extract data from it.

This is trivial for a state actor initiating arrest to accomplish, as they can just hold the target down where they are at. The target would have to possibly toss the Bluetooth device this is paired with across the room in the event of arrest, or would have to dash away from their laptop. 

Both scenarios seem unrealistic, and even if the target was able to toss their bluetooth device, bluetooth as a protocol is notoriously unreliable. The Blueproximity method has tons of issues that make it unreliable but could easily be used as a redundancy alongside other methods mentioned.

The [Daytripper Laser Tripwire](https://github.com/dekuNukem/daytripper) method is exactly what it sounds like. When a small hardware motion detector reports being triggered, a script runs a series of routines. I put this as a software solution because although it uses interesting hardware as a switch, the anti-forensics tasks themselves are software scripts.

Daytripper brings an interesting perspective to the table, but like Blueproximity, it is probably best used alongside another software method as a redundancy. It is intended as a toy for office workers to pull one over on their boss by default, but it could bring a lot to the table for this threat model. 

The security of daytripper is solely dependent on the attacker not knowing it is there. If they know about it, it is likely to be trivial for them to just avoid it. 

Daytripper for this reason, seems more useful for a stationary home office setup. It could be used in conjunction with security cameras on a closed system, as an alert system combined with the triggering of anti-forensics processes.

All of these software based solutions leave a lot to be desired, and could theoretically be thwarted by a resourceful attacker in the proper conditions. 

It is easy to imagine a scenario where an attacker is able to bypass most of these software methods if they know ahead of time what is running on a target's computer.

The fact that these solutions rely on the functionality of the underlying operating system gives attackers a lot of room to be careful and creative about their approach. 

Any software based solution in my opinion should be treated with extreme skepticism, and the user should assume that these methods are probably susceptible to circumvention by a state actor with a reasonable budget.

The software solutions mentioned above are under somewhat active development. While the currently released scripts could definitely not be considered robust, several communities are working hard to improve upon existing solutions.

Next I'm going to discuss several ways of characterizing how we can think about purely mechanical tripwire methods.

## Hardware Based Solutions

Personally I find power [kill switch methods](https://en.wikipedia.org/wiki/Kill_switch) that rely on fully mechanical principles more elegant than software solutions. While the software solutions script things like "$ sudo shutdown -P now", this is no replacement for ripping the battery out of a laptop by force.

The most pleasing solution seems to be developing multiple redundant systems of layered physical security involving both hardware and software shutoffs. The combination of methods is the key to hardware security against an adversary attempting to rob a target of their laptop in an unencrypted state.

## Remove the Battery

The obvious solution that comes to mind when people start thinking about this problem is, why not just remove the battery? Physically removing the laptop battery and forcing yourself to run only the cable can in theory act as a tripwire just fine by itself. This solution is free and requires no thought or complicated engineering whatsoever.

The thought here is essentially that if someone tries to rip the laptop away from a target, in the process one of the parties is very likely to unplug it in the struggle. It takes barely a split second to react and unplug a laptop cable, and for the ultra paranoid a wrist lanyard or cable of some sort could be attached to the cable for extra protection.

This seems like a good idea, but is it actually feasible to do in practice? If you are like me, and have had a laptop battery that won't charge properly you already know the answer. Operating solely on cable power can be fine, but finding a plug in public spaces is rather annoying.

The problem with this is that it violates a basic security rule, it makes things tedious and difficult. I spent a few weeks living out this scenario by choice recently, and it is incredibly annoying. 

To make a long story short, if a user has other options besides doing this, they will cheat and won't put up with how annoying this is. If you really like using your battery power, and attempt to do this you won't keep up with it unless you throw all your batteries in the trash.

The main problem here is not the cable itself or finding a spot to plug in, it is the fact that it forces the user to essentially have to start up and shut down the computer constantly. 

Most people hate doing this, it seems silly to constantly be shutting down every application, closing all the tabs, and winding down whatever they were in the middle of. In reality, this is actually the best scenario for someone attempting to force good security practices on themselves. 

By being cable-tethered with no battery, the user is forcing themselves to FDE anytime they aren't actively using the computer. So moving from home to coffee shop, not having a battery forces them to enforce encryption during all transit-states.

I would argue that if a user isn't encrypting and decrypting their laptop every time they walk from place to place with it in a bag, the threat model is incredibly weak anyway.

### Issues With Removing The Battery

There are a couple more technical problems with this model that came up when I tried to test it. First, a surprising amount of modern computers simply don't have the ability for you to remove the battery without taking the case apart. This can void warranties and cause other issues for some people. It would be nice if everyone just loved old Thinkpads like I do, but this is a wishful assumption.

For some people this might actually be a blessing in disguise, as removing the internal battery doesn't give a visual cue that anything is odd about the computer. An adversary that sees a laptop without a battery in the slot may take this to be an indicator the laptop is criminal.

Putting a piece of electrical tape or rubber over the battery terminals so a connection cannot be made seems to work fine. This won't work for every brand of laptop but it allows some creativity, just don't short the battery. After doing this on Thinkpads the battery sticks out slightly but it would not be noticeable unless someone was seriously examining the laptop. 

Another problem is in the actual replication of the adversaries grab for the computer. The power cord of most laptops has a lot of sideways tension inside the power socket. Where a user is typically sitting while using a laptop gives the incorrect angle of attack for pulling the cord out. 

By this I mean if the cord is behind the screen instead of off to the side, you need to be pulling the cord away from yourself to unplug it. Turns out this is a very unnatural gesture, and in my replications with another person playing the attacker on an old laptop, it was pretty unsuccessful.

It flat out doesn't work unless the computer model has the power cord coming out the side of the laptop instead of the back. Even with a lanyard or some other form of cable attached to your wrist, across several experiments it became clear that this method only has a slight chance of success on an unmodified laptop. So what can be done about this? 

It should be noted that older Mac laptops don't have this issue, and this can actually point us toward our solution. 

On older Macs this solution is more viable because the cables have a [magnetic breakaway system](https://en.wikipedia.org/wiki/MagSafe) that should make the original solution work extremely well. They are shallow, on the side, and magnetic breakaways, and can be disconnected quickly with a pull.

So fear not, as there have been modification designs for power cables to transform them into Apple Magsafe cables just like a Mac. For Thinkpads there is the [ThinkSafe](https://archive.is/uDZgt) which is what I tested out. The instructions are self explanatory, and it works great although I used weaker magnets than this tutorial recommends.

For other types of laptops there are [similar tutorials](https://archive.is/SVVAM) for making magnetic breakaway power cables. I haven't tried this with anything but Thinkpad laptops so I'm sure some people will have an easier or harder time of this. Most cables now seem standardized to this shape though, so this should be a viable solution for 90% of users. 

Making these magnetic power cables look like something other than a sloppy, conspicuous mess (like my attempt ended up), I leave as an exercise for the reader.

## Battery Pull String

Now, for all the people who can't stand to go without their battery, I will discuss my attempts at making a battery pull string. I could not find any references to other people attempting these things with laptops, so if anyone has seen someone doing something similar let me know.

I'll say at the outset that these experiments as I attempted them were unsuccessful but gave me several ideas about what could work in future experiments. The methods I attempted were simple in design, and it is clear from their failures that to make this kind of setup work would require more planning.

### Loose Batteries

For these experiments I was using two computers, both of which have battery access as a bar on the back of the laptop. I tried to think of how this would work on laptops that have the battery as a square in the middle underside of the laptop. 

Laptops with this kind of design could probably use some sort of hook-and-loop fastener attached to the battery as a design. I couldn't figure out a good way to make this work with the old Dell laptops I had.

The first requirement for ripping a battery from the laptop is that the battery hooks/latches be removed. The battery needs to be able to slide in and out of the computer without touching the locking switch. 

To accomplish this, I cut the latches off several of my batteries to test with. Please excuse my photo quality these were taken in an undisclosed extremely humid location I was traveling in.

![Clipped Hooks](/assets/images/tripwire-cuthook.png)
_Battery with clipped off hooks_

My initial assumption was that that the batteries would end up being too loose and would end up constantly falling out. To stop this, I tried out using cut pieces of ultra thin no-slip foam rubber material to secure the battery in place. This turned out to be completely incorrect. The batteries on the three laptops I tried this with were not loose in the slot at all.

When I added the rubber wedges, this just made them extremely tight. The batteries would not fall out even when I held the laptops upside down and shook them lightly. 

This turned out to be a core issue with this method, the batteries even after removing the rubber wedges still had this issue, they fit into the slot too tightly.

When the batteries start to come out, they come out at a very slight angle that causes the friction of the sides of the battery slot to hold them in place. 

This is surprisingly strong. After applying a slight amount of lubricant they seemed to come out fine. Even after this point though when I hold them upside down without applying any back/forth movement, the batteries stay wedged. 

This problem was more significant with the ASUS computer I was working with, but was less a problem with the Thinkpad. The grip of the battery onto the sides of the slot ended up causing most of my further battery experiments to end in failure.

### Attaching Cables

To get this to work, I wrapped the cables around each battery to form a pull cord I could then rip on to pull out the battery. 

I tried a couple of different ways to tie these to the battery, nothing interesting except to note that different battery shapes impact how you should tie the loop.

![ASUS Cable](/assets/images/tripwire-spread.png)
_A cable that is even and functioning correctly_

Batteries with a raised middle section were conducive to doing this. The cables stayed off to the sides and made for an even pull. Batteries without a raised middle section were less successful. 

The cable tended to move inward over time until it almost got to where the battery terminals were. To fix this, doing some kind of drilled through-hole attachment at either end of the battery would probably be necessary. 

When I attached these to my wrist, I tied the cable onto a metal watch. I was irrationally paranoid that I might end up shocking myself through some convoluted means.

![Thinkpad Cable](/assets/images/tripwire-slid.png)
_A cable about to short the battery out_

The best materials for this are about what you would expect, metal fishing line, guitar strings, piano wire, etc. To experiment, I took several different types of wire to try to find the bare minimum of what works.

The battery has only a very small window of clearance and getting anywhere near it causes the battery to get stuck. My results were that basically anything between 26 gauge and 32 gauge will probably work. Most metal cables looked very conspicuous and stuck out like a sore thumb.

![Materials](/assets/images/tripwire-cablematerials.png)
_Several different materials and gauges_

Ordinary thread does not work even slightly, the pressure from the battery friction is too much and it just snaps instantly without the batteries budging. 

Thick upholstery thread on the other hand works just fine and doesn't snap after several tries. The interesting thing about upholstery thread is that it doesn't clang around while you are trying to type, and does not look abnormal. All the metal examples clang when you are using the computer and generally make a lot of noise.

### Issues With The Pull String

The idea here is fundamentally a failure because the angle of the pull is just wrong. There is no way to get this to work properly because the battery has to be pulled straight away from the person using the computer. This is the same problem with having a non-breakaway plug. 

I sufficiently convinced myself through several trials that this kind of method is just stupid and is not worth attempting further. 

If you pull at the wrong angle or the attacker is able to pin down your hands, or come up on you from behind it is difficult to move your arms in the correct direction to remove the battery. 

In a situation with two or more strong adversaries it is just not plausible for this to work. One issue I found is that I kept making the cable too long, to pull properly I had to move my hand far forward in an awkward way. 

When I made the cable shorter, so this was less of a problem, my normal hand movements at the computer were too constrained by the cable.

Remark: One place where this would be useful is if a target were travelling with a messenger bag with the computer on inside of it. The angle of the pull would be correct and would function perfectly. 

The adversary walks up and the target discretely pulls a cable turning off the laptop inside their bag. In a strict threat model though as I noted before, the laptop should already be off if it is being carried down a street.

## Epoxying The Ports

Here I would just like to briefly mention that using epoxy on all unnecessary physical ports could give the target a huge advantage over an attacker. This topic could be the start of another conversation entirely about setting up secure air-gapped computers, but this post is already too long.

I usually only use a few ports on my computer and for the rest there is no reason why they should exist, so there is no reason not to epoxy over them. This tactic is commonly employed in the US by federal agents and security contractors. 

The only warning I would say is that laptop cooling is sometimes designed with the assumption that certain holes will exist. Plugging up these holes can cause your laptop to start overheating and potentially damage it, so be thoughtful before trying this.

## Conclusion and Future Work

This survey and these experiments are all just fun preliminary thoughts on the topic.  My goal here was to attempt to put some fraction of my notes up in a timely manner. It is not a completed project. I plan to suppliment this with new posts of my further experiments and further writeup/pictures on those I've already undertaken.

This will take more experimentation, and possibly some fabrication. As soon as I can get my thoughts collected, take more photos, and purchase more batteries to work with, I plan on checking into several other topics.

One area I've completely neglected in this post is desktop setups. I'm not sure if it is redundant to talk about desktop setups or not. A post about this would mostly consist of thinking of ways to turn off surge breakers and cut power that way.

I have not done enough background research on what types of attacks adversaries could use to thwart the software based methods, I mostly just handwave over this point.

In the references below, I point to a couple of older exploits relating to udev. I'm certain that this kind of thing has been accomplished previously and is probably well documented.

This is my current stopping point for the project until I can experiment with designing and fabricating an enclosure for battery cells to move this further. 

The obvious next step is to attempt a more serious construction with prototypes and a lot more thought. In the future I will outline a generalization of the scripts mentioned above I'm currently trying to clean up.

In my next post I'm also hoping to explore taking apart battery packs and inserting a switch between the battery and the computer. It seems like it should be possible to do an inverse of those [plastic battery pull tabs](https://archive.is/QFd9v) that often come packaged with electronics.

In this experiment, the tab instead would be metal and complete the circuit between the laptop and the battery. The pull string would then create a gap-switch when pulled that would break the circuit and cut power to the laptop. This on most battery packs would maybe require some sort of fabrication to the battery cell housing.

I am currently looking into aftermarket battery packs for laptops. The problem with them I'm running into is that they cram the cells in so tightly there is no extra room in the housing for things to be added. 

I'm considering creating custom 3D printed battery cell housing to put cells in, but making this look normal will be challenging.

I would love to hear any new suggestions. Please check back for updates soon.

# Resources and References

 [0] [Dead Man's Switch](https://en.wikipedia.org/wiki/Dead_man%27s_switch)

 [1] [Royal Yachting Association: Boating Kill Cord](https://archive.is/qhktS)

 [2] [FBI Shows Arrest Video Of Dark Web Kingpin Who Died By Suicide in Police Custody (2018)](https://www.vice.com/en_us/article/59wwxx/fbi-airs-alexandre-cazes-alphabay-arrest-video) - [Archive](https://archive.is/chCQR)<br>

 [3] [McGrew Security RAM Dumper for Cold Boot Attacks (2008)](https://archive.is/MZUBq)

 [4] [TRESOR: TRESOR Runs Encryption Securely Outside RAM](https://www.cs1.tf.fau.de/research/system-security-and-software-protection-group/tresor-trevisor-armored/) - [Archive](https://archive.is/Ul6b1)

 [5] [Writing udev rules](http://www.reactivated.net/writing_udev_rules.html) - [Archive](https://archive.is/2gPYB)<br>

 [6] [Udev Spoofing Exploits (2009)](https://www.linux-magazine.com/Online/News/Local-Root-Exploit-in-Udev) - [Archive](https://archive.is/C36X2)

 [7] [Frozen Cache: Mitigating cold-boot attacks on FDE (2009)](http://frozencache.blogspot.com/) - [Archive](https://archive.is/wwnvB)

 [8] [Practical Cold Boot Attacks (2014)](https://swizec.com/blog/week-12-practical-cold-boot-attacks-that-will-make-cryptonerds-shit-their-pants) - [Archive](https://archive.is/iI2tA)

 [9] [BusKill HN Discussion](https://news.ycombinator.com/item?id=21935359)<br>

[10] [Blueproximity Guide](https://www.daniloaz.com/en/automatically-lock-unlock-your-screen-by-bluetooth-device-proximity/) - [Archive](https://archive.is/3V67U)

[11] [Breaking Full Disk Encryption from a Memory Dump (2018)](https://blog.appsecco.com/breaking-full-disk-encryption-from-a-memory-dump-5a868c4fc81e) - [Archive](https://archive.is/6ECvK)

[12] [When Full Disk Encryption Goes Wrong](http://spaceisdisorienting.com/when-fulldisk-encryption-goes-wrong) - [Archive](https://archive.is/l9nl5)

[13] [Frost: Forensic Recovery of Scrambled Telephones (2013)](https://www.cs1.tf.fau.de/research/system-security-and-software-protection-group/frost/) - [Archive](https://archive.is/GkzNK)

[14] [LUKS Support for Hashcat (2017)](https://hashcat.net/forum/thread-6225.html) - [Archive](https://archive.is/ZjHAe)

[15] [The Human Tripwire For A LUKS Nuke Partition](https://defplex.wordpress.com/2018/08/15/the-human-tripwire-for-a-luks-nuke-partition/) - [Archive](https://archive.is/6QjW4)

[16] [Cracking LUKS/dm-crypt passphrases (2019)](https://diverto.github.io/2019/11/18/Cracking-LUKS-passphrases) - [Archive](https://archive.is/I1Vs8)

[17] [Unlocking Thinkpad Battery Firmware](http://zmatt.net/unlocking-my-lenovo-laptop-part-1/) - [Archive](https://archive.is/zjY6g)

[18] [Battery Firmware Hacking (2011)](https://media.blackhat.com/bh-us-11/Miller/BH_US_11_Miller_Battery_Firmware_Public_WP.pdf)