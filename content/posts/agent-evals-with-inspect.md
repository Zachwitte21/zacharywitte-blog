+++
date = '2026-10-17T12:00:00-04:00'
draft = true
title = 'Agent Evals With Inspect'
+++
# Intro

I have been building AI agents for a long time now, and for most of that time I tested them the traditional way: a hand-rolled suite of scripts, a pile of test cases, and a lot of manual checking to see if the agent still behaved after I changed a prompt or swapped a model. That works fine for a simple agent. It stops working once the agent runs for a long time, uses tools, or needs to be compared across several models.

Over the last couple of months I have been using the Inspect eval framework, both at work (that is all I can say about that) and in my free time on a Pokémon Emerald eval that I have been building and posting about on X. My short take is that if you are evaluating agents and still maintaining your own harness for it, Inspect is worth a look.

# What Inspect Gave Me

A few things that I used to build by hand, or never built at all:

1. **Checkpoint and resume.** Agent runs can be long and they do fail partway through. With Inspect I can pick a run back up from a checkpoint instead of paying for the whole thing again. In the Emerald eval I killed episodes on purpose to test this, and the resumed runs matched the ones I let finish.
2. **Model-agnostic runs.** Swapping models is a config change instead of a rewrite. That is what makes a leaderboard realistic, because comparing a handful of models should not mean maintaining a handful of integrations.
3. **Logs and a viewer.** Every run is logged, and Inspect View lets me read through what the agent actually did. I used to build my own scrappy version of this every time, and it was never as good.
4. **Scorers and sandboxing.** Grading lives in a structured scorer instead of scattered through my scripts, and the environment the agent runs in can be sandboxed. For Emerald, that means a Dockerized emulator that behaves the same on every run.

None of these are flashy on their own. Together they mean I spend my time on the eval itself (what should the agent be doing, and how do I score it) and less time on plumbing.

# The Emerald Eval

The Pokémon Emerald eval is my free-time project for putting this into practice. Models play the game and get scored on how far they get. I have been sharing progress on X, and I will go deeper on the details in future posts.

# What's Next

Later today I am posting the first leaderboard with a few models on it, and over the coming weeks I plan to keep growing it. If you want to follow along, I am on X at [@zachary_witte](https://x.com/zachary_witte).

– Zachary Witte
