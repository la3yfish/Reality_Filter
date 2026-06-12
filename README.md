## Reality Filters

A collection of lightweight reality filters designed to reduce hallucinations, unsupported claims, and overconfident responses in AI assistants.

The repository contains specialized filters for different AI use cases:

* **Reality_Filter** — basic, compact filter for chats
* **Reality_Filter_All-purpose** — for AI assistants, agents, and multi-purpose workflows
* **Reality_Filter_Code** — for coding agents and software development
* **Reality_Filter_RAG** — for retrieval-augmented generation (RAG) systems

## Why?
Large Language Models often generate plausible but incorrect information.

Common failure modes include:

* inventing facts
* presenting assumptions as facts
* hallucinating APIs and library methods
* mixing framework versions
* fabricating citations and sources
* claiming document support where none exists

These filters help enforce evidence-based behavior and explicit uncertainty handling.

## Design Philosophy
All filters follow the same core principles:
* Accuracy over confidence
* Evidence over assumptions
* Explicit uncertainty
* No fabricated sources
* Prefer incomplete but correct answers over complete but unsupported answers

The filters are intentionally lightweight and can be added directly to system prompts, custom GPTs, AI agents, coding assistants, and RAG pipelines

---

## 1. Reality_Filter
General-purpose filter for chat assistants.

### Purpose
Reduce factual hallucinations and encourage transparent handling of uncertainty.

### Key Rules
* Do not invent missing information
* Do not present unverified information as fact
* Explicitly acknowledge uncertainty
* Label assumptions and speculation
* Prefer accuracy over completeness

### Recommended Use Cases
* AI chatbots
* Customer support assistants
* Personal assistants
* General-purpose GPTs
* Business Q&A assistants

---

## 2. Reality_Filter_Code
Specialized filter for coding assistants.

### Purpose
Reduce software-development hallucinations, especially around third-party libraries and frameworks.

### Key Rules
* Never invent APIs
* Never assume methods or parameters exist
* Verify library versions when possible
* Distinguish verified code from pseudocode
* Do not claim code is tested unless it was actually tested
* Explicitly identify implementation uncertainties

### Prevents
* Non-existent methods
* Deprecated APIs
* Wrong SDK usage
* Incorrect imports
* Version mismatch errors

### Recommended Use Cases
* Codex
* Cursor
* Windsurf
* Cline
* Roo Code
* OpenHands
* AI software engineering agents

---

## 3. Reality_Filter_RAG
Specialized filter for Retrieval-Augmented Generation systems.

### Purpose
Prevent fabricated evidence, sources, citations, and document-grounded hallucinations.

### Key Rules
* Retrieved evidence is the primary source of truth
* Separate evidence from inference
* Never fabricate citations or sources
* Never claim evidence exists when it was not retrieved
* Explicitly acknowledge retrieval failures
* Prefer incomplete but supported answers over unsupported conclusions

### Prevents
* Fake citations
* Fake documents
* Invented page numbers
* Fabricated retrieval results
* Unsupported document summaries

### Recommended Use Cases
* Enterprise RAG
* Knowledge bases
* Document assistants
* Contract analysis
* OCR pipelines
* Business analytics systems

---

## 4 . Reality_Filter_All-purpose
Universal reality filter for general AI assistants, agents, and multi-purpose workflows

### Purpose
Reduce hallucinations, unsupported claims, hidden assumptions, and overconfident reasoning across chat, coding, retrieval, and tool-assisted tasks

### Key Rules
* Accuracy over completeness
* Evidence over assumptions
* Never fabricate facts, sources, APIs, or implementation details
* Explicitly label uncertainty and inference
* Separate observed evidence from conclusions
* Do not infer unstated intent or expand scope without request
* Acknowledge conflicting evidence instead of forcing a consensus

### Prevents
* Factual hallucinations
* Unsupported conclusions
* Hidden assumptions
* Fake sources and references
* Overconfident reasoning
* Scope creep and intent guessing

### Recommended Use Cases
* AI chatbots
* General-purpose GPTs
* Customer support assistants
* Business assistants
* Research assistants
* Agentic workflows
* Multi-tool AI systems

---
