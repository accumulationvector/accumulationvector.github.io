---
layout: post
title:  "Time Tracking Under Quarantine"
author: "accumulation-vector"
---

For the past month because of government orders issued relating to the [COVID-19 pandemic](https://en.wikipedia.org/wiki/2019%E2%80%9320_coronavirus_pandemic) practically everyone is quarantined to their homes. Many people working from home are struggling with maintaining a proper sleep/wake cycle. 

Some people are reporting rapidly declining productivity, most people are reporting disrupted sleep patterns. I am currently on WFH so I have been having similar experiences. My sleep schedule is very odd right now, and I was having some mild trouble with productivity stuff.

I decided to use this occasion to do something that I'd never considered before, tracking my time. I am a huge fan of lists and my desk is cluttered with todo lists, Post-it notes of items to do, and my mirror is covered in whiteboard marker of things I need to work on currently.

These have been my main method for managing personal productivity, but I've never actually tried to measure my home productivity in any objective way. I usually just see how many items I can get crossed off and attempt to maximize that number. I never considered tracking how hard I'm working beyond that.

During lockdown, I'm only going to be working from my computer in one location (my home office). I plan on doing this for at least the duration of my state quarantine. If it works out, I might continue tracking after the quarantine ends also, who knows.

## Staying Home

I am incredibly thankful to have been living in a medium-sized house with a reasonable back/front yard during the quarantine, otherwise, my situation would be 10x worse. There are several days that I haven't gone outside at all, and I haven't really felt the need. Not sure how much impact any of this is going to have on my health, but I'm trying to keep up normal levels of exercise as much as possible.

It is surreal to see everyone wearing masks out in public all the time now, but I'm kind of liking the aesthetics of it and I hope it keeps up after the quarantine periods are over. The way they look is truly cyberpunk and using masks consistently will probably make everyone healthier overall in the long term.

Shortages are not something that I have experienced at all yet, everywhere in my area has been nearly fully stocked. I was able to see this coming well ahead of time when it was still going on in China, so I bought most of my supplies before the rush. When I first saw the numbers coming out of China I stocked up on necessities like canned food, basic survival supplies, and of course toilet paper.

Although this essentially turned out to be completely unnecessary as most restaurants didn't close, and most grocery stores haven't had any problems beyond the few days when everyone was panicking simultaneously. 

The virus has devastated the lives of many of my neighbors and people in my friend circles, so I am thankful that for the time being I have nothing major to complain about. The best thing less impacted people can do is try to find ways to help other people who are impacted.

This post in light of what other people are going through is about things that are pretty trivial in the grand scheme of what is going on right now. I have no political takes I desire to give on the situation.

One hidden benefit of all this is that I have been able to spend a lot more time with my partner over the course of the quarantine. At least this is possible when our sleep schedules remain in sync with each other.

## Time Under Lockdown

![Lockdown Meme](/assets/images/covid-meme.jpg)
_Alexander caught in a horrible time spiral_

My circadian cycle under lockdown rotated readily, and at first it kept getting away from me. The time drifts significantly, and I have found that the best thing is to fall into a pattern of only sleeping when you are dead tired. I get into fits of energy where I am on a roll and don't want to stop despite it being something like 7am.

Sleeping after working hard for an extended period feels great, it is nice to really feel tired at the end of a day. I wish I could experience sleep like this more regularly. 

My time-shifting was dramatic when the quarantine began but has largely settled into a noticeable pattern after about the first week. I found myself centering and coming back to a habit of going to bed at 5-7am and waking up at 1-3pm roughly. 

This has not caused any significant problems for me except for a regularly occurring Zoom call that I have at 11am on some days. I don't understand why my sleep has centered on this, attempting to correct it by force in either direction (going to bed earlier or later) does not seem to work.

## Rotating The Clock

Instead of trying to fight this pattern I was falling into, I decided instead to embrace it as much as possible and just shift my entire schedule around what my body was telling me.

What does this look like? I took my computer's internal clock and rotated it around so that 23:00-24:00 corresponds to when I end up going to sleep and 7:00-8:00 corresponds to when I wake up. I'm making the clock match my body for once, rather than making my body match the clock.

This rotation is more for fun than anything, I'm not sure what value it is truly providing me other than maybe a standardization of my day. It is a fun experiment to run regardless, and is certainly an interesting change from trying to tether myself to the local timezone.

I posted about this briefly on Twitter, but if anyone has any references to other people doing this outside of travel situations, please let me know. I would love to read about the results of similar experiments. 

The friction of this ends up being all the other people that I have to work and interact with daily. Outside of quarantine, this would be completely unviable as a technique. 

However, under the constraints of quarantine I can get away with running the experiment. I don't need to interact with people most mornings in my timezone, so it works out pretty well.

Working in the dead of the night when everything is quiet has been amazing for getting things done. All of my time tracking data I'll talk about next was collected in sync with these clock rotations.

## Time Tracking

![Hamster Interface](/assets/images/covid-hamster.png)
_The Hamster time tracking GUI example_

There is an overwhelming number of time tracking software options available, instead of trying to figure out the best software I just looked at the first three I saw that run on linux. I picked [Hamster](https://github.com/projecthamster/hamster) because it is graphical, has few features, and comes with a moderately compact interface.

In my configuration from the outset, I decided that I would only use the category feature. For this I created the categories work, not_work, chores, and sleep. 

I didn't want to even touch the activity or tagging systems at all, for the activity field I just put the name of the category. I knew if I made it much more complicated than this or tried to use the tagging system, I would just let the time tracking go by the wayside. 

If it took too long to create an entry, I would just do it sloppily or give up. This is supposed to just be for fun after all. If I tried to use the tagging system at the end of each day to tidy up the entries, this would just be time wasted.

For the description field I just put a single word or two of what it is that I'm doing. From these sentences if I wanted to use this for a larger project I could go back and tag all of this data properly.

It took a small amount of time to get the feel for what this would be like, but it ended up being a fun experience. It is more useful than I expected that it would be and a lot less of a hassle than I expected.

## Results

Overall, I was able to keep track of my time pretty well this first month of time tracking. There were only a few times when I seriously messed up the tracking. The amount of hours I accumulated missing was very low.

I thought it was going to be much harder than this to keep track of things, but it was easy to fall into a pattern of doing a few clicks between task switching. 

Most days I don't go back and forth a lot anyway, so it was just a matter of keeping track of huge multi-hour blocks. I only really lapsed a few days when I was exceedingly busy and pressed for time.

The results I collected are also consistent enough that I could do some analysis on it without a significant amount of preprocessing. The software saves every event logged in it to a csv file.

The data quality is high enough that after a few months there will probably enough data to draw some real conclusions about my activity patterns. For now, I don't know exactly how much there is that could be extracted from this comparatively small sample.

### Productivity

The technique seemed to help my productivity, although I don't have a baseline to measure from before the tracking started. I have never had these kinds of gains doing other productivity techniques like Pomodoro timers, so this was a very different experience. 

The most helpful thing was when I would look at the timer and see that I had been goofing off for much longer than I thought I had been. 

This minor reminder jolted me back into working when otherwise I would have let myself goof off for a much longer period. I'm shocked that was all it took to improve my numbers so significantly.

My productivity as measured by the time tracking is dramatically high, I tracked ~50hrs a week of working time. I used a strict definition for what work meant and often ended up under tracking a lot of busywork or clerical tasks like writing emails. 

My prediction while tracking was that my under tracking would cause it to be below 40hrs per week on average. During this lockdown I have been feeling lethargic and unenergetic, and I expected the results to reflect this.

It would be interesting for people who think being quarantined is causing a productivity slump to get an actual measurement to see just how much they are doing. For me, I was sure that I was slumping before I saw my results.

### Sleep

Several [other](https://www.gwern.net/Zeo) [people](https://guzey.com/science/sleep/14-day-sleep-deprivation-self-experiment/) have done experiments that involve tracking sleep, but here I've taken the opposite approach. Sleep is the least careful thing that I tracked, and almost all of my sleep counts are inflated. The point of this was mostly to track productivity, so this negligence was deliberate.

If I was doing a sleep tracking experiment, I would structure it entirely around sleep. Even in an experiment for fun like this, measuring the beginning and end of a sleep cycle was annoying. 

The main thing that made this difficult was that my tracker was on the computer and manually operated. I would start the timer and then do miscellaneous tasks like reading or looking at the news each morning and night.

When attempting to correct the counts I had little indication of how much time was genuinely asleep and how much was another category. I could have altered the sleep hours each morning to make the numbers closer to reality, but this seemed like a waste of time. 

My best guess about sleep during this period seems to have been pretty good. I have been consistently getting 7hrs of sleep a night except when I cut it shorter on purpose. 

### Zoom Calls

Many days under this tracking there are abrupt jumps in the tracking because of Zoom calls. There is a semi-regular call I have at 11am which is quite annoying for this sleep schedule. My sleep has lined up well with almost every other regular call that I have, but this one call kills me.

I don't particularly care for Zoom and wish that people were open to using other alternatives like [Jitsi](https://meet.jit.si/), but I know this is currently unrealistic.

There have been numerous critiques of the [security of Zoom](http://archive.is/5xqhk) in the past few weeks. I hope that all of this will cause people to end up gravitating toward other options.

## Conclusion

The post here was intended to be a short introductory writeup, but now it has spiraled into a long essay. 

In a follow-up post to this I plan to take the files, do some real data analysis, and create a few pretty seaborn graphics from them. Most of the ideas I have for this will be replications of standard data mining techniques. 

### Going Forward

Next month I want to slowly transition into tracking things into smaller categories of task types. Keeping track of smaller tasks while not adding too much complexity to the tracking itself will be an interesting tradeoff. 

The data here is for fun when it is all said and done, so if tracking the smaller tasks becomes too time-consuming I will just drop it.

I have yet to decide if I want to make the dataset I'm generating public or not. The data isn't personal, but I have some privacy concerns about posting it anyway. 

Please try something like this yourself and do a writeup on it! Experiments like this are really fun, even if they are not done to a rigorous standard.
