---
layout: page
title: cv
permalink: /cv/
description: >
  CV of Utsav Verma — Senior Database Architect, Data Platform Leader &
  Applied AI Engineer. 21+ years in SQL Server, data platforms, DataOps, and
  applied AI. 2 AI patents filed.
nav: true
nav_order: 3
---

<div class="d-flex justify-content-center mb-4">
  <a href="https://1drv.ms/w/c/e7ee95718edb5e82/IQCCXtuOcZXuIIDn0jkAAAAAAV5g4qXEYIoaoTEOrYCkXyc?e=RiItJK" target="_blank" rel="noopener" class="btn btn-primary">
    <i class="fa-solid fa-file-word"></i> Download / View Full CV
  </a>
</div>

## Summary

Database Architecture leader with **21+ years** designing, optimizing, and migrating enterprise-scale SQL Server data platforms for gaming and loyalty systems, combined with hands-on applied AI engineering experience. Led architecture and migration of a 4–5B+ row data warehouse (nVision), cutting migration time and risk by 60–70% through a balance-delta-driven ingestion strategy. Filed 2 patents for a reusable AI content and video generation framework, and built production applied-AI systems spanning offline/on-device LLM rule engines, AI-powered player-facing help content, and AI-driven engineering automation. Combines deep RDBMS and data warehouse architecture expertise with practical experience in RAG, AI agents, prompt engineering, and LLM integration using Azure OpenAI, GCP, Claude API, and OpenAI APIs. Outside work, designs and operates two fully automated YouTube channels on a self-built, topic-agnostic content pipeline that scripts, renders, voices, and publishes video without manual intervention.

---

## Core Skills

**Data & Database Architecture**
SQL Server (2005–2025, incl. 2019 / 2022 / 2025), Data Warehousing & Dimensional Modeling, Large-Scale Data Migration & Reconciliation Frameworks, DataOps (DevOps for Databases), Performance Engineering & Optimization, Azure, AWS (RDS), SSIS, SSRS, MicroStrategy, C# & ASP.NET, PowerShell, Agile Methodology

**Applied AI & AI Engineering**
Retrieval-Augmented Generation (RAG), AI Agents & Agentic Workflows, Prompt Engineering, AI Integration Patterns, LLM Deployment (cloud & offline/on-device), Azure OpenAI, OpenAI API, Claude API, Google Cloud Platform (GCP), Agent Development Kit (ADK), GitHub Copilot, Codex CLI, Ollama, Python, LiteLLM, ChromaDB & Vector Stores, Multi-Agent Orchestration, MongoDB, FastAPI, Playwright, MoviePy

**Leadership & Delivery**
Technical Mentoring (10+ engineers), Cross-functional & Multi-national Team Leadership, Internal Training Delivery (10+ sessions), Stakeholder & Delivery Management, Code Review Standards, High-Level Design (HLD) Ownership, Emotional Intelligence, Product Mindset

---

## Key AI Projects & Initiatives

### Reusable AI Content & Video Generation Framework *(Patent-Filed)*
- Designed a domain-agnostic AI engine for script, audio, image, and video generation
- Reused the same framework across multiple unrelated domains with minimal changes
- Applied for 2 patents based on the framework architecture and implementation

### Agentic PRD-to-PBI Generation System (Google ADK) — Working POC
- Built a multi-agent system that ingests a Product Requirement Document and produces ready-to-work PBIs, compressing a breakdown that consumed ~2 weeks of analyst and product-owner effort into ~2 days
- Architected on Google ADK: an orchestrator delegates to a planner agent that extracts keywords and composes targeted search queries, then retrieval subagents fan out across Confluence, TFS (historical defects and PBIs), and existing product documentation, and their findings are consolidated into a single working context
- Added a clarification agent that interrogates the consolidated context from a junior engineer's perspective, forcing every PBI to answer the questions a new team member would actually ask before writing code
- Questions the product-owner agent cannot resolve are flagged as BLOCKER and routed to a human through a web UI (Teams bot planned), so requirement gaps surface during grooming rather than mid-sprint
- A memory agent persists human answers and completed runs in ChromaDB, so a later PRD covering similar ground is served from prior work instead of re-running the full retrieval — the system gets cheaper and better-informed with every PRD it processes

### AI-Powered Audio-Visual Help for EGMs
- Applied the AI framework to convert text-heavy EGM help screens into audio-visual explanations
- Enabled EGMs to explain features to players using audio and visuals
- Improved player comprehension and engagement without hardware changes

### Offline AI Rule Builder for Loyalty Systems
- Built a natural-language rule engine using an offline ~1B parameter LLM deployable on CPU-only systems
- Enabled secure rule authoring without cloud or GPU dependency
- Accelerated rule rollout while reducing infrastructure cost and platform risk

### AI Scrum Master for Engineering Execution
- Built a Python-based AI system to parse Zoom call transcripts/emails and extract discussed work items
- Enriched items using Git metadata to generate executive summaries and action items
- Eliminated manual sprint reporting and improved execution transparency and accountability

### AI-Generated Migration Automation Utility
- Used AI to design and generate a complete migration automation framework
- Compressed development timelines from ~2 months to ~1 week
- Demonstrated AI as a practical engineering productivity multiplier

---

## Personal Projects

### Automated YouTube Content Engine — Two Live Channels *(Self-Initiated)*
- Built and run two fully automated YouTube channels end to end, with no manual step per video: [Jyotishi Bhai](https://youtube.com/@JyotishiBhai) — Hindi weekly horoscope Shorts, and [WordSlay HQ](https://youtube.com/@WordSlayHQ) — English word-of-the-day Shorts
- Designed a single topic-agnostic Python engine in which each channel is a pluggable agent plus one YAML block; the shared pipeline runs content fetch → LLM script generation → Playwright HTML slide rendering → GCP Text-to-Speech → MoviePy video assembly → YouTube Data API upload with scheduled publish times
- Model-agnostic LLM layer via LiteLLM (Vertex AI, Google AI Studio, OpenAI, Anthropic, local Ollama) with per-section model routing, so a single high-value prompt section can be broken out onto a cheaper, faster model and re-rolled independently of the rest of the script
- Externalized prompt templates with placeholder substitution and two-tier caching (disk plus MongoDB), making re-runs near-zero-cost and allowing any one section to be regenerated in isolation
- Unattended scheduling on macOS LaunchAgents: 19 upload slots per day for word-of-the-day and a weekly Monday build of all 12 sun signs with a fixed publish time; per-topic state, backlog catch-up, idempotent re-runs, and an upload ledger that prevents republishing the same content
- Per-slide narration segmentation keeps voice-over and on-screen text in sync; 84 slide templates (12 sun signs × 7 weekdays) are generated from shared parts and verified by a build-time consistency check
- Companion FastAPI service delivers audience-personalized variants of the same content to a public site, published as static JSON and HTML through the GitHub Contents API and a CDN
- Tech: Python, LiteLLM, Playwright, MoviePy, Google Cloud TTS, MongoDB, FastAPI, YouTube Data API, launchd scheduling

---

## Professional Experience

### Sr. Database Architect / Sr. Manager — Aristocrat Technologies India
**Project: nVision (Data Warehouse)** · **Jun 2024 – Present** · Gaming / Loyalty
- Led end-to-end architecture and migration delivery of a multi-billion-row (4–5B+) data warehouse for a large-scale loyalty platform
- Cut migration time and risk by 60–70% using a balance-delta-driven ingestion strategy instead of full reloads
- Ensured 100% balance accuracy across legacy and next-gen systems via automated reconciliation frameworks
- Delivered production-grade performance testing and rollout despite missing synchronized backups, unblocking the program
- Owned migration strategy, validation framework, performance readiness, cross-team dependency management, and technical risk mitigation
- Rebuilt team trust and delivery momentum for a group impacted by prior organizational layoffs, while resolving broken data lineage from source refactoring
- Tech: SQL Server 2022, SSIS, MicroStrategy, PowerShell

### Database Architect / Sr. Database Architect — Aristocrat Technologies India
**Project: Loyalty Suite** · **Mar 2017 – Present** · Gaming / Loyalty
- Promoted to Senior Architect; organization-wide leader for day-to-day innovation and quality
- Conceived and launched the master data management framework
- Built a data-migration-based DataOps framework enabling automated build and deployment (MakeDb)
- Contributed to new product acquisitions and spearheaded load testing of the entire 36-product suite
- Mentored and groomed 10 senior database developers on technical skills and professional attitude
- Introduced UT frameworks and code review processes; led implementation of new technologies (SQL Server 2022 upgrade path, AWS Cloud, AWS RDS)
- Provided technical leadership to database and front-end teams across an acquired product suite with legacy performance issues
- Tech: SQL Server 2022, SSRS, C# & ASP.NET

### Associate Database Architect — Aristocrat Technologies India
**Project: Oasis 360** · **Jun 2014 – Mar 2017** · Gaming
- Optimized a large, tightly coupled system spanning 30+ products while rapidly ramping up in a new domain
- Collaborated with business and delivery teams to identify system dependencies and propose efficient, defect-free designs
- Performed performance analysis and code validation, resolved production issues, and led change/impact analysis
- Helped delivery heads establish technical protocols; coordinated with US counterparts using SQL Server, SSIS, SSRS, and C#/ASP.NET

---

### Consultant Engineer — GlobalLogic
**Mar 2011 – Jun 2014** · CRM domain

### Analyst — Royal Bank of Scotland, India
**Jan 2009 – Mar 2011** · Investment Banking domain

### Developer (Band S2) — Satyam Computer Services
**Oct 2007 – Jan 2009** · Car Finance domain

### Senior Software Engineer — Nucleus Software
**Jun 2006 – Oct 2007** · Banking domain

### Software Engineer — UBICS Enterprise Solutions
**Jan 2005 – Jun 2006** · e-Governance domain

---

## Publications

{% assign articles = site.data.articles %}
{% if articles %}
<ul>
  {% for article in articles %}
  <li>
    <a href="{{ article.url }}" target="_blank" rel="noopener">{{ article.title }}</a>
    <br><em>{{ article.platform }}</em>
  </li>
  {% endfor %}
</ul>
{% endif %}

---

## Achievements

- 2 patents applied for AI implementation (Reusable AI Content & Video Generation Framework)
- 7 technical articles published on SQLServerCentral.com
- Won multiple awards worth ₹15+ lakhs, including Employee of the Year
- Winner, internal innovation competition
- Contributed to new product acquisitions
- Delivered 10+ internal training sessions
