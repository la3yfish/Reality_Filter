# Reality Filters

A collection of lightweight reality filters designed to reduce hallucinations, unsupported claims, and overconfident responses in AI assistants.

The repository contains three specialized filters for different AI use cases:

* **Reality_Filter** — for general-purpose chat assistants
* **Codex_Reality_Filter** — for coding agents and software development
* **RAG_Reality_Filter** — for retrieval-augmented generation (RAG) systems

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

---

# 1. Reality_Filter

General-purpose filter for chat assistants.

### Purpose

Reduce factual hallucinations and encourage transparent handling of uncertainty.

### Key Rules

* Do not invent missing information.
* Do not present unverified information as fact.
* Explicitly acknowledge uncertainty.
* Label assumptions and speculation.
* Prefer accuracy over completeness.

### Recommended Use Cases

* AI chatbots
* Customer support assistants
* Personal assistants
* General-purpose GPTs
* Business Q&A assistants

---

# 2. Codex_Reality_Filter

Specialized filter for coding assistants.

### Purpose

Reduce software-development hallucinations, especially around third-party libraries and frameworks.

### Key Rules

* Never invent APIs.
* Never assume methods or parameters exist.
* Verify library versions when possible.
* Distinguish verified code from pseudocode.
* Do not claim code is tested unless it was actually tested.
* Explicitly identify implementation uncertainties.

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

# 3. RAG_Reality_Filter

Specialized filter for Retrieval-Augmented Generation systems.

### Purpose

Prevent fabricated evidence, sources, citations, and document-grounded hallucinations.

### Key Rules

* Retrieved evidence is the primary source of truth.
* Separate evidence from inference.
* Never fabricate citations or sources.
* Never claim evidence exists when it was not retrieved.
* Explicitly acknowledge retrieval failures.
* Prefer incomplete but supported answers over unsupported conclusions.

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

# Design Philosophy

All filters follow the same core principles:

1. Accuracy over confidence.
2. Evidence over assumptions.
3. Explicit uncertainty.
4. No fabricated sources.
5. Prefer incomplete but correct answers over complete but unsupported answers.

The filters are intentionally lightweight and can be added directly to system prompts, custom GPTs, AI agents, coding assistants, and RAG pipelines.

---

# Repository Structure

```text
Reality_Filters/
├── Reality_Filter.md
├── Codex_Reality_Filter.md
├── RAG_Reality_Filter.md
└── README.md
```

---

# License

MIT License.
