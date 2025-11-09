+++
date = '2025-11-09T15:22:12-05:00'
draft = false
title = 'AI Agents With Mcp'
+++
Goals for this post. 

Over the past few months, I’ve been diving deep into the world of Artificial Intelligence. With a background in cloud services like AWS and Microsoft Azure, it’s been a natural fit to use Azure as my main AI hub. One of my favorite recent projects involves building an AI agent for some friends’ disc golf website. The goal is to help players find the right discs based on experience level, throwing style, and the typical courses they play.

This has been an exciting challenge because disc golf isn’t a field I knew much about initially. I had to research the game and learn what factors really influence disc selection. In the first version of the agent, I used a simple system prompt and let the model handle user recommendations based on its default knowledge and search. I chose the GPT-5-mini model through Azure for its cost efficiency, which was ideal for an MVP build. Even so, I quickly noticed that larger models provided more refined responses.

That’s where my experience with MCP servers came in. At DCS, I’ve been collaborating with subject matter experts in the CBRN field to construct a secure knowledge base that Azure-hosted AI models can use. This approach helps overcome the limitations of general models, which often can’t access or safely share sensitive domain-specific data. Inspired by that success, I began developing a similar MCP-based knowledge server for the disc golf agent. This server grounds the agent’s responses in curated, trustworthy data—helping GPT-5-mini provide more accurate and context-aware recommendations. Early results have been promising, showing that a small, well-grounded model can outperform larger ones, while remaining cost-effective and secure.

Meanwhile, I’ve been continuing my formal AI education through the Microsoft Learn AI Engineer path. I passed the first certification exam last month and now feel confident and well-prepared for the final Azure AI Engineer Associate exam. The combination of professional experience, hands-on projects, and structured learning has truly accelerated my understanding of Azure AI tools and their real-world applications. My next goal is to complete the certification later this month and round out my Azure AI journey.

– Zachary Witte