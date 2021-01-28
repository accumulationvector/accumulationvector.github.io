---
layout: post
title:  "Random GPT-3 Experiments Pt.1"
author: "accumulation-vector"
---

I recently was given the opportunity to play around with the GPT-3 beta API. My initial impression after spending a while with it is that a lot of the conversational/language-centric modes of text generation are as good as people claim. On non-language-centric completion, it falls completely short and was largely less impressive than I was honestly expecting.

I'm not going to list off a bunch of examples here, everyone online has already done that. The collection on [Gwern's site](https://www.gwern.net/GPT-3) is probably the best resource for examples I can point people to. I'm mostly going to just give some general impressions of the technology.

The main thing that was unimpressive about it was its inability to do program synthesis. A lot of people claimed this functionality was much more powerful than it actually was.

It was unable to handle my attempts at AI box experiments and was unable to handle natural language mathematical logic texts. It probably cannot be used for any sort of formal verification as it currently stands, though as of writing it looks like with some modifications it has now become [possible](https://syncedreview.com/2020/09/10/openai-gpt-f-delivers-sota-performance-in-automated-mathematical-theorem-proving/amp/).

When you feed it tasks where it has to be more rigorous it fails (probably because the various mathematics texts it trained on have confusing notational structures that get filtered as noise).

The logic exercises that the OpenAI team created themselves all work great. All of the chess examples in particular are astonishingly good. One of the reasons it succeeds at playing chess we can point out is that because there is more than one correct answer for each given position, it can improvise and still appear to play well.

There are so many interesting things that can be done with it, it was incredibly fun to play around with. The functionality of the game AI Dungeon, which is available to the public seems to be roughly equivalent from what I've heard. The game is essentially just a text input on top of the raw GPT-3 API and can do much of the same functionality. 

The AI dungeon game obviously is inferior because you can't alter any of the text generation parameters like you can with the real API as far as I know. It is still probably the best option available for most people who want to play with the API.

I'll also say I've gotten pretty good at prompt design through playing with the thing, so if anyone is interested in talking about this I have played and experimented with writing code for the API extensively. Message me if you are interested in discussing the subject.

## Writing alongside the GPT3

The most success I had was with generating continental philosophy texts. I got about 80k words worth of reasonably usable content out of it in the time I was using it. Most of what it produced is actually high quality, with some minor editing the results are approximately as readable as Derrida or Baudrillard at worst.

At their best, the text generated is really enjoyable to read and is as intelligible as good as any decent book. Be on the lookout for some cool stuff coming out of this. I want to use the results in some sort of experimental art project. 

Writing alongside the GPT-3 has been a borderline magical experience, I'm tempted to allow it to write the outline of this article for me right now. Having it as an assistant alongside your writing process is extremely powerful.

When you place your text into it, it is almost like a mutual conversation building off an infinite will of creativity. The machine pulling you in various directions, dancing around the curation you have designed for it is beautiful and poetic to watch.

Introducing in topics and thought modes it really feels as though it tries to anticipate your thoughts beyond simply prediction, it starts feeling anthropomorphic after a certain point. One second it can feel like it understands what I am saying and then the next it is giving me complete gibberish showcasing the ignorance.

You could describe the feeling it gives with lots of flowery language outside of this cycle of anticipation. You can say that it effectively hallucinates its response from the sounds of all that has ever been typed.

The distillation of humanity is what it is attempting to do. Trained on the minds of everyone it already enacts a stupid hivemind. It is not a coherent mind, it is more of a series of schizophrenic expressions without any one consciousness winning out from the flood of all thoughts it is trying to predict from.

A few thoughts bubble up to the top of the predictive feature set and are allowed to follow outwards from the mixture but they are not actually creating a collective computational mode.

The creative flow is one of the few things that most people think cannot be emulated by a machine. On the contrary, I predict the artistic movements of the future are going to be the most productive there have ever been. 

If you want to think and produce with an increased measure of speed there is no reason not to use text completion software to assist you in commentating your ideas. 

<ins>This section was written with the help of the GPT-3</ins>, it has a bit too much fluff in the middle for my taste though. Another problem you can probably see is that it has a distinct issue with jumping between many topics without a great flow.

## Critiques of GPT-3

Everyone online is creating conversations about what the impact of GPT-3 and the other GPT's that will come after will be. There are clearly several aspects of life around us that can simply be automated roughly enough from context without having a human touch involved. Generic content creation is probably going to be the hardest hit and will change the entire online marketplace for ads.

Recently an [entire article](https://adolos.substack.com/p/feeling-unproductive-maybe-you-should) that was written by a GPT-3 on productivity made it to #1 on the front page of [HN](https://news.ycombinator.com/item?id=23893817) with nearly 200 votes. Only a handful of people in the comments actually noticed that the content consisted of complete gibberish. It still sparked a relatively lively conversation and got thousands of clicks.

I've said on twitter that this really says more about how far the quality of discussion on HN has fallen from its peak than it says about GPT-3. People just don't read the articles much and only focus on the discussion threads that arise.

The author of the post had a [great writeup](https://liamp.substack.com/p/my-gpt-3-blog-got-26-thousand-visitors) about how the economics of using text generation for clickbait will impact online media. I largely buy this entire line of argument, but I wish more people would discuss other negative ways that GPT will be used.

People are talking about all sorts of negatives of GPT-3 but most of these are just economic negatives and basic scams. There isn't enough futuristic thought put being placed toward the long term psychological and sociological impacts this kind of software could have.

To be continued..