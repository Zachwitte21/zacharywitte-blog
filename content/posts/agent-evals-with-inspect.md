+++
date = '2026-10-17T12:00:00-04:00'
draft = false
title = 'Agent Evals With Inspect'
+++
# Intro

If you are evaluating agents with a hand-rolled test suite, try Inspect. I have been building agents for a long time, like the [disc golf agent](/posts/ai-agents-with-mcp/) and the [reminiscence therapy agent](/posts/takeaways-from-google-hackathon/), and I have always tested them with my own eval suites: a set of test cases, some manual checking, and a rerun after every prompt or model change. That works well but it takes a while to setup each time and make sure that I am tracking all of the information that I need.

Over the last couple of months I have been using the Inspect eval framework almost exclusively now. In my free time I have started a project, the Pokémon Emerald eval that I have been building and posting about on X.

# What Inspect Gave Me

Four things I used to build by hand, or never built at all:

1. **Checkpoint and resume.** Agent runs are long and they fail partway through. Inspect lets me resume from a checkpoint instead of paying for the whole run again. I killed Emerald episodes on purpose to test it, and the resumed runs matched the ones I let finish.
2. **Model-agnostic runs.** Swapping models is a config change, not a rewrite. That is what makes a leaderboard realistic.
3. **Logs and a viewer.** Every run is logged and Inspect View lets me read what the agent actually did. I used to build a rough version of this every time. It was never as good.
4. **Scorers and sandboxing.** Grading lives in a scorer instead of being scattered through my scripts, and the emulator runs in a Docker sandbox so every run starts the same.

None of these are flashy. Together they mean I spend my time on what the agent should do and how to score it, not on plumbing.

# The Emerald Eval

The Emerald eval is where I am putting this into practice. Models play the game and get scored on how far they get. I will go deeper on the details in future posts.

# What's Next

The first leaderboard goes up later today with a few models on it. I plan to keep growing it over the coming weeks. I post updates on X at [@zachary_witte](https://x.com/zachary_witte).

– Zachary Witte
