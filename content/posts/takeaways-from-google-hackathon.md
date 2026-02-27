+++
date = '2026-02-27T15:45:23-05:00'
draft = false
title = 'Takeaways From Google Hackathon'
+++

# Intro

Throughout the month of January I worked on an ai agent that helps dementia patients with their reminiscence therapy. During this process I learned a lot about developement in the new era of AI. In this post I want to share some of my key takeaways from the experience and some of the things I learned along the way.

# 1. Coding with AI

In late November Anthropic released Claude Opus 4.5 and like many others, I believe this was a major turning point in software development or any knowledge based work. Throughout this project I utilized Claude Code and Google's Antigravity IDE to help me plan features and build them out. These tools are game changers for knowledge work because they can quickly retrieve information from documentation like the context7 mcp server, your codebase, or the internet. While have a better model does produce better results, the real trick is all about giving the model the best context possible. Using the context7 mcp server to give the model access to the documentation for the various apis I was using meant that I didn't have to spend time looking through the documentation for code examples or syntax and instead spend time architecting the application to meet my needs. So while coding with AI is clearly here to stay, these models can also be beneficial when creating a PRD or feature specs. The ability to quickly retrieve information about apis or libraries was very beneficial for me during the planning fase when I needed to compare two different options for a certain use. 

# 2. AI Accessibility
While many of my fellow coworkers are current on the latest AI tools and models, my target audience for this project is not. Throughout the design process I got feedback from caregivers that I knew and they had tons of questions about how the agent would work and how they would use it. Not only was it important to be transparent about how the agent works, but it was also important to design the agent to be incredibly user friendly and easy to use. Threw many variations of system prompts and user guides, I finally landed on a design that I think is pretty user friendly for non-technical users. The best way to go about this is honestly just having people try the product as soon as possible. If was doing this all again, I would get the core functionality working first and immediately get feedback from ideally your target audience and iterate from there. This gives you a good feel for product fit and you get to start building your product with the right foundation.

# 3. Audio Modality
One of the most exciting parts of this project was the audio only interface. I have done simple speech to text and then text to speech in the past, but this was my first time building a full fledged audio only agent. The models from google have the capability to handle audio streaming input and output. This means that the model can start generating a response while it is still listening to the user. This really brings the ai model to life makes it feel like you are talking to a real person. Streaming the audio over a websocket was easy, but I also had to give the model access to the current photos/videos and metadata associated with them. This was important for the project because users caregivers would label photos with who is in them, what is going on, and when it happened. The langchain framework was perfect for this use case and made the process of handling all of this informatino and messages about the user going to the next photo much easier. Overall I think the audio modality is the future of AI agents as it is more natural and intuitive than typing or using a GUI.
