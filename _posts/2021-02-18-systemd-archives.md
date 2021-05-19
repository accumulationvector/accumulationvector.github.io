---
layout: post
title:  "Operating Systems Without Systemd"
author: "accumulation-vector"
---

I recently noticed that the original [without-systemd.org](https://web.archive.org/web/20190218081523/http://without-systemd.org/wiki/index.php/Main_Page) site is down. It seems, from what I can tell, to have been replaced entirely by a less substantial site called [nosystemd.org](https://nosystemd.org/). 

Whether you agree or disagree with the message of these sites, there was lots of incredible material collected on without-systemd. 

One resource that I found to be exceptionally useful for several years was the curated lists of operating systems with non-systemd init systems. These lists are still available in archival form.

[Linux distributions without systemd](https://web.archive.org/web/20190208034948/http://without-systemd.org/wiki/index.php/Linux_distributions_without_systemd)

[Operating systems without systemd](https://web.archive.org/web/20190207214904/http://without-systemd.org/wiki/index.php/Operating_systems_without_systemd)

I'm unsure who originally wrote them, but they are good enough that they shouldn't be lost in an archive somewhere. These lists opened my eyes to several obscure distributions that I never would have heard of otherwise.

I hope that more people start creating long-form distribution lists similar to this. I've seen a few lists like these crop up, like the one on [sysdfree](https://sysdfree.wordpress.com/2019/10/12/135/) for example. Despite this, there are surprisingly few high-quality lists on the topic. 

 There is however an excess of clickbait Top-10 Linux distro spam blogs that clog up any search on the subject. Lists that actually contain some content about systems that everyone isn't familiar with are a breath of fresh air. 

Compare these simple lists that give you just as much information as you need, to roughly the same list shown through an interface like [DistroWatch](https://distrowatch.com/search.php?ostype=All&category=All&origin=All&basedon=All&notbasedon=None&desktop=All&architecture=All&package=All&rolling=All&isosize=All&netinstall=All&language=All&defaultinit=Not+systemd&status=Active#simple) for example. The rawer lists are actually a much more pleasant entry point for people trying to explore the weirder edges of operating systems.

Here I'm just going to mention a few operating systems that I personally have found interesting. A few of these I originally encountered because of the lists above.


## Void

Void is hands down my current favorite operating system and it is what I'm using for my daily driver. Several years ago it was more of a hidden gem, but the secret is out and at this point everyone knows about it. 

It is quickly rising in popularity, and I can't recommend it enough. The package manager xbps is outstanding, it is very similar to pacman in many ways.

The operating system as a whole is very similar to Arch (it is also rolling release), but I find it nicer to use personally. The custom init system is also just very simple and easy to use.

What initially lead me to trying it out was a friend recommending it to me because it has a musl edition, and I have used it ever since.

[Void Linux](https://voidlinux.org/) -[Archive](http://archive.vn/SjTTU)


## HelenOS

HelenOS is a multiserver/microkernel operating system. If you have ever experimented with GNU Hurd you will probably find it to be extremely similar in many ways, and different in others.

Pretty much everything here is implemented completely from scratch, almost nothing gets pulled in from other sources. It isn't actually usable for anything as it exists currently. The aim of the project is more to be an experiment aimed at OS enthusiasts. 

There are tons of [research projects and papers](http://www.helenos.org/wiki/Documentation) written about HelenOS and its components. Almost every component has been built in an interesting or experimental way that varies from other operating systems. It is one of the best hobby project operating systems I've encountered. It encompasses an incredible number of interesting experiments concurrently.

[HelenOS](http://www.helenos.org/) -[Archive](http://archive.is/4Dwum)


## Calculate Linux

Calculate is a Gentoo derivative with everything set up very similarly. It is a rolling-release setup that is very popular in Russian-speaking countries. 

It is similar overall but makes very interesting changes that improve upon Gentoo in significant ways. The system update system is a great improvement on the common Gentoo method, and the kernel installation is much less difficult than on Gentoo.

Essentially, I would say it is Gentoo but with very precise optimizations added on that allow you to take advantage of what the OS has to offer more easily. 

If you are a fan of Gentoo, I urge you to give this distribution a shot, as it is Gentoo-style with some very interesting changes.

[Calculate Linux](https://wiki.calculate-linux.org/about) -[Archive](http://archive.is/ElZ8Q)


## CRUX

CRUX is an interesting operating system that several of my friends use religiously. It is an incredibly lightweight operating system that focuses on simplicity. 

It uses a tar based package system, BSD-esque initscripts. The ports system for packages is exactly like BSD from what I can tell. 

The main thing everyone seems to report is that it runs extremely fast, and this has been my experience as well.

[Crux](https://crux.nu/) -[Archive](http://archive.is/YL1uJ)

[Handbook](https://crux.nu/Main/Handbook3-5) -[Archive](http://archive.is/6F6Ii)


## Redox

An interesting project with the goal of building an operating system that is completely written in Rust. The project is a microkernel that takes inspiration from Plan9 and Minix. 

Almost everything here is written completely from scratch with almost nothing outside pulled in. It is a great experiment in designing an operating system from scratch with a modern language like Rust. Few other examples of this kind of project even exist. 

The project mostly exists in an experimental stage. It does not have many packages available, but is growing steadily. It isn't ready for general use just yet, but unlike a lot of other similar experiments it is almost on its way there.

If you are interested in a cool community working actively on a project with a unique design philosophy, I definitely recommend checking out Redox.

[Redox](https://www.redox-os.org/) -[Archive](http://archive.is/9gsy9)

[Docs](https://doc.redox-os.org/book/) -[Archive](https://web.archive.org/web/20200226083815/https://doc.redox-os.org/book/)


## Bedrock Linux

Bedrock is a very odd operating system with a unique philosophy. Build your own thing however you could possibly imagine literally, by mixing and matching very disparate components from other distributions seamlessly.

You can do odd combinations with other distributions possibly, but the Bedrock system makes the process much less work for the user. The distribution includes tools that allow these choices to be made in several potentially odd or convoluted mixtures with comparatively little work on the users part.

It is for people who want to experiment with their setup in potentially weird ways. I don't know why you would need or desire some of the combinations that this distribution is capable of, but it is there should you ever want such things.

[Bedrock Linux](https://bedrocklinux.org/) -[Archive](http://archive.is/k67Bh)


## Haiku

The modern continuation of the OpenBeOS project. The first thing everyone always says about it is that it is one of the most beautiful operating systems alongside things like [ElementaryOS](https://elementary.io/). If you are interested in 90's user interface design, you have to check it out.

I'm not certain about usability, as it seems to have a limited set of packages available in the HaikuDepot package manager. Community ports are available for many things, but I haven't explored how much is available.

It states as a goal that it wants to be an operating system for personal computing, and it seems to fit this pretty well. If you don't want to use your computer for much more than surfing the internet or writing text it seems ideal.

[Haiku OS](https://www.haiku-os.org/) -[Archive](http://archive.is/nj6dH)


## GuixSD

GuixSD is a system distribution built on the Guix package system. It uses a [functional package manager](https://arxiv.org/abs/1305.4584) that is very similar in design to [Nix](https://nixos.org/nix/). It is one of the few operating systems that has been designated as free by the [Free Software Foundation](http://archive.is/gBDtc).

If you like the way Nix works and are a fan of Scheme, this is worth trying out. It is a neat project with some unique features, but it is more fun as an intellectual curiosity than as something practical.

My interest in this operating system has been solely based on my love of all things Scheme. If you are interested in Scheme, you have to try it out, everyone else probably won't enjoy it.

[GuixSD](https://guix.gnu.org/) -[Archive](http://archive.is/JXiTg)

[Guix Documentation](http://archive.is/https://guix.gnu.org/manual/en/html_node/index.html#SEC_Contents) -[Archive](http://archive.is/ycoRm)
