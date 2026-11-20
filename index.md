---
layout: default
title: Camille Ryan — AI Engineer
---

I turn fuzzy goals into working LLM systems that are **tested, traceable, and cost-aware**. I bring 12 years of AI/ML and data science (MS in Statistics), most recently as Clarivate's sole data scientist on R&D projects. I'm based in Denver and open to AI engineer roles.

[GitHub](https://github.com/camille-ryan) · [LinkedIn](https://www.linkedin.com/in/camille-ryan/) · [Email](mailto:rdbrady@gmail.com)

## Bike Planner: a multi-agent bike tour planner

**The problem.** Planning a multi-week bike tour across several countries takes days by hand: choosing a route, splitting it into daily stages, and finding overnight stops near a train station in case plans change.

**What I built.** A chat agent on the Anthropic SDK that plans the tour through tool calls you can watch: routing between cities, finding rail stations along the way, splitting the trip into stages, and adding viewpoints near each day's ride. The map fills in as it works. Underneath is a custom routing engine over OpenStreetMap data for Austria, Czechia, Germany and Denmark, built on PostGIS and pgRouting. The same tools are exposed through an MCP server, so Claude Desktop can drive the planner too.

| Result | |
|---|---|
| Planning time | Days by hand, down to minutes |
| Cost per plan | About $0.50 |
| Routing latency | ~100 ms across 4 countries |
| Memory | 5 GB down to 300 MB with lazy LRU loading |
| Real-world use | Used to plan an actual multi-country tour |

**How I know it works.** A gold-prompt suite runs against the agent and a Claude judge scores each plan on a rubric, with results on a static dashboard. Reading the judge's rationales drove real fixes: one change to a tool description raised a rubric score from 2 to 4. Every request logs structured traces with token usage and per-tool latency, so cost per plan is a straight sum.

**Framework comparison.** I rebuilt the agent in LangGraph as a planner, router, parallel enrichers, composer and critic, then benchmarked it against the native SDK on the same prompt. The native version needed 233 lines of backend code and 14 tool calls; LangGraph needed 570 lines and 22 tool calls.

**What's next.** Covering a new country means a 3-hour preprocess on a large machine, and the MCP server is designed for splitting by region but doesn't do it yet.

[Read the code and design notes →](https://github.com/camille-ryan/bike-planner)

## Legally Distinct 4e: an AI-run tabletop RPG engine

I direct an autonomous Claude Code agent that builds a complete tabletop RPG rules engine: about 23,900 content entries, including ~2,500 monsters and ~10,000 powers, across 1,229 closed GitHub issues. When the agent hits a decision it shouldn't make alone, it files a "question"-tagged issue and waits for me. The story engine runs on local models with no API costs: Qwen 7B on a laptop voices the NPCs, and DeepSeek 14B on a desktop acts as the game master.

[View the repo →](https://github.com/camille-ryan/combat_engine)

## Highlights from work

| Where | What |
|---|---|
| Clarivate | Built an LLM citation-extraction pipeline that cut ingestion costs ~99% at vendor-level accuracy; Clarivate adopted it in place of the outside vendor. |
| Clarivate | Built the Academic Coach for Alethea, a chat-based AI study mentor kept on task by an overseer agent; 70% of surveyed students reported a better study experience. |
| Clarivate | Invented a chemical-structure search method, filed as patent application [US-20250239333-A1](https://patents.google.com/patent/US20250239333A1/en). |
| PG&E | Shipped the production pole-risk model for the 2019 wildfire safety program, scoring all 2M+ poles. |

## Other projects

| Project | What it does |
|---|---|
| [email_filter](https://github.com/camille-ryan/email_filter) | Sorts Gmail with a local LLM (Ollama): job-search mail gets labeled and promotional mail gets cleared. |
| [music_bot](https://github.com/camille-ryan/music_bot) | A music similarity graph plus tagging on audio embeddings, with an active-learning tagging app. |
| [planescapeRAG](https://github.com/camille-ryan/planescapeRAG) | A GraphRAG chatbot over Planescape lore. |
