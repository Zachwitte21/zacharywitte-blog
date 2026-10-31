+++
date = '2026-10-31T06:00:00-04:00'
draft = false
title = 'When the Model Already Knows the Map'
description = 'My Pokémon Emerald eval has a leaderboard leader that mostly won by remembering the game from training data instead of exploring it, and what that means for game-based agent evals.'
+++

# Intro

The first leaderboard for my Pokémon Emerald eval has been up for a couple of weeks, and one result bothered me enough to dig into the logs. Gemini 4 Argon finished first, and the more I read its run, the less it looked like a model figuring out a game and the more it looked like a model recalling one. This post is about how I checked that, what I found, and what it means for any eval that uses a well-known game.

If you missed the setup, I wrote about the framework in [Agent Evals With Inspect](/posts/agent-evals-with-inspect/). The short version: a model starts a new game and has to reach the first gym badge, and progress is graded from the game's RAM, so the model cannot just say it got the badge. Each turn is one tool call like `navigate_to`, `press`, `battle`, or `advance_dialog`.

# The First Turn in Rustboro

The harness shows the model its own position and nothing about where doors or exits are. That matters, because it means a model has to explore to find the Gym.

On Argon's first turn in Rustboro City, standing at (19,59), it pathed to (27,20). That is the exact tile of the Gym door, 39 tiles away and far off screen. It was inside the Gym two turns after reaching the city. Muse Spark 1.3 took 88 turns to do the same thing.

It was not a one-off:

- **Petalburg Woods:** on entering, it wrote the north exit into its notes and pathed toward it five times, with a wild battle interrupting each attempt.
- **Route 103:** it pathed straight to where the rival stands.
- **Petalburg City:** it pathed straight to the Gym from the edge of town.

# Measuring It

One impressive moment is an anecdote, so I counted. For every walking target in a run, I checked whether that tile had ever been on screen. The model's view is roughly 15 by 10 tiles centered on the player, so a target outside that window at every point in the run is a blind target.

| Model | Walks aimed at tiles never on screen |
|---|---|
| Gemini 4 Argon | 52% (14 of 27) |
| Muse Wonder | 32% (24 of 74) |
| Claude Haiku 5.5 | 17% (14 of 83) |
| Muse Spark 1.3 | 13% (19 of 149) |
| GPT-6 Luna | 8% (45 of 547) |

Every model aims at the unknown sometimes, and that is fine. "Go 30 tiles north" is a reasonable way to explore. The difference is in where the targets land. The other models' blind targets look like guesses. Argon's land on the exact tile it needs.

# It Was Not Hallucinating

When I think of a model "knowing" something from training, I expect a mix of right and wrong. This was cleaner than that:

- Every coordinate it remembered worked.
- Its notes had the correct story beats, like the rival's Level 5 Treecko and the Pokémon Center in Petalburg, which Spark got wrong.
- Its plan for after the badge was correct too, covering Rusturf Tunnel, Peeko, and Mr. Stone at Devon Corp. None of that is in the prompt.

I did not find a single hallucination in its run, but there is a catch. Argon never called `verify_objective`, the tool for checking its own progress, even once. Spark called it 11 times. That saves Argon turns, and it also means there were no claims in its run for me to grade. It also barely narrated, writing 21k output tokens against Spark's 110k.

# What This Means for the Eval

Argon's lead is mostly memorized map knowledge, not navigation skill. Under my own rules, that is fair: the model's own ability counts and nobody gets play hints. But it means this eval partly measures how well a model remembers Pokémon Emerald, and I want to be upfront about that whenever I post the leaderboard.

Two caveats on my own analysis:

- Argon's reasoning is encrypted, so I cannot prove where the coordinates came from. I am inferring it from behavior, and the behavior is hard to explain any other way.
- The on-screen test assumes a 15 by 10 view, so the percentages are approximate. I ran it on the first five runs, before the later ones were added.
- It is one game per model, so treat this as a data point and not a ranking.

# Lessons for Game-Based Evals

A famous game is a convenient eval because the goal is clear and the grading is objective. It is also a game that is all over the training data. A few things I am taking from this:

1. **Measure contamination instead of arguing about it.** The blind-target count took an afternoon and gave me something concrete to say. Any eval that gives a model partial information can run a version of it.
2. **Memory and skill are different things.** A model that recalls the map and a model that reads the screen can finish in the same number of turns. If you care about the second one, the eval needs to separate them, for example with maps or content the model could not have seen.
3. **Tool use is a signal too.** Argon skipped self-verification entirely. A model that is confident from memory behaves differently from a model that is working it out, and that shows up in which tools it reaches for.

This is the same lesson I keep relearning from my other agent work. In [AI Agents With MCP](/posts/ai-agents-with-mcp/), I grounded a small model with curated data so it would not rely on whatever it happened to remember. In an eval, the problem flips: what the model happens to remember is exactly what I need to account for.

# What's Next

I am thinking about how to add a variant of the eval that a model cannot have memorized, and about whether to report both scores side by side. I will post what I settle on, and I keep the running results on X at [@zachary_witte](https://x.com/zachary_witte).

– Zachary Witte
