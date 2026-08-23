# Local AI RAG Assistant

Fully local, private ChatGPT-style AI assistant using Ollama + Docker + RAG — no cloud, no data leaves the machine.

Part of my project portfolio.

## Why I Built It

IT and cybersecurity work means handling sensitive data every day — logs, configs, scripts. Sending that kind of data to a cloud AI service carries exposure risk. Instead of treating a local LLM as just a convenience tool, I wanted to treat it as infrastructure: deployed securely, kept offline, and used responsibly.

The goal was a fully local, private ChatGPT-style assistant running entirely offline, with no cloud involvement and no data leaving the machine.

## Stack

| Component | Tool |
|---|---|
| LLM runtime | Ollama, running llama3.1 (open-source LLM) |
| Containerization | Docker |
| Chat interface | Open WebUI |
| Retrieval | Retrieval-Augmented Generation (RAG) |
| Knowledge base storage | Repurposed 12TB HDD |
| Vector database | [add detail] |
| Embedding model | [add detail] |

## How It Works

At a high level:

- Ollama serves the local LLM (llama3.1).
- Docker runs Ollama and the supporting services.
- Open WebUI provides the chat front end.
- An old 12TB HDD is repurposed as a structured "knowledge warehouse" instead of passive cold storage — optimized for fast retrieval and clean embeddings, and focused on real-world IT & cybersecurity reference material.
- RAG pulls relevant context from that local knowledge base before the model generates a response, rather than relying only on the model's built-in knowledge.

[add detail: exact ingestion pipeline, chunking strategy, and embedding/retrieval implementation]

## Challenges & How I Solved Them

**Docker/Ollama integration issues.** Initially ran into compatibility problems getting Ollama running correctly inside Docker. Resolved by updating Docker and confirming Ollama and the model were running on compatible versions.

**Slow inference/response speed.** Initial response times were too slow to be practical. Improved by running inference on a GPU (RTX 3060) instead of CPU.

## What I Use It For Day-to-Day

- Analyzing Nmap scan output
- Troubleshooting Linux issues and logs
- Writing and explaining Bash / PowerShell scripts
- Learning cybersecurity concepts safely, without sending logs, configs, or scripts to a cloud service

## What I Learned

- Running open-source LLMs locally with Ollama, served through Docker
- Standing up a local chat interface (Open WebUI) on top of a self-hosted model
- The basics of a RAG pipeline — pulling context from a local knowledge base instead of relying on a model's built-in knowledge alone
- Diagnosing and resolving Docker/Ollama compatibility issues rather than reflexively reinstalling
- The practical difference GPU inference makes over CPU for local LLM response times
- Thinking about local AI as infrastructure to secure and maintain, not just a tool to run once

## docker-compose.yml

The repo includes a `docker-compose.yml` showing the general, standard Ollama + Open WebUI setup pattern. It's a representative example of this architecture (a well-documented public pattern), not my exact production configuration.

## Notes

This README documents the project using only the details confirmed so far. Sections marked `[add detail]` — vector database choice, embedding model, and the ingestion/chunking pipeline — will be filled in as that part of the build gets documented further.
