# Reality Filter for LLMs

Large Language Models are incredibly capable, but they share a common flaw: they hallucinate. They invent APIs, fabricate citations, mix framework versions, and confidently present assumptions as facts. 

The **Reality Filter** is a set of strict, lightweight system prompts designed to force LLMs into evidence-based reasoning and explicit uncertainty handling. Whether you are building a RAG pipeline, a coding agent, or just want more reliable answers from your daily AI assistant, these filters eliminate the "plausible BS."

## Design Philosophy

These filters are built on a simple hierarchy of principles:
1. **Accuracy over confidence:** We prefer an incomplete but correct answer over a complete but unsupported one.
2. **Evidence over assumptions:** Never present assumptions as facts.
3. **Explicit uncertainty:** If the AI doesn't know or can't verify, it must say so clearly.
4. **Zero fabrication:** Never invent sources, APIs, or implementation details.

## What's Included?

This repository contains two versions of the filter, tailored for different context windows and use cases.

### 1. The Full Version (`Reality_Filter_Full.md`)
A comprehensive, rule-by-rule system prompt designed for complex agentic workflows. 
* **Best for:** Autonomous agents, coding assistants (Cursor, Copilot), complex RAG pipelines, and API-driven workflows.
* **Features:** 
  * Strict instruction hierarchy (System rules > Context > User prompt).
  * Deep technical constraints (schema verification, code classification).
  * Multi-step reasoning rules (weakest-link confidence).
  * Conflict resolution protocols.

### 2. The Concise Version (`Reality_Filter_Concise.txt`)
A highly compressed, plain-text version under 1500 characters.
* **Best for:** Custom GPTs, ChatGPT custom instructions, limited context windows, and standard chat interfaces.
* **Features:** Delivers the core epistemic rules, technical constraints, and conflict handling in a single, copy-pasteable block without any markdown formatting.

## How to Use

Using the Reality Filter is as simple as pasting it into your AI's system prompt or custom instructions.

**For Custom GPTs / ChatGPT:**
1. Go to your GPT's configuration.
2. Paste the **Concise Version** into the "Instructions" box.

**For API Applications (LangChain, LlamaIndex, OpenAI API):**
1. Set the **Full Version** as the `system` message at the beginning of your message array.
```python
messages = [
    {"role": "system", "content": reality_filter_full_text},
    {"role": "user", "content": "Does the library X have a function for Y?"}
]
```

**For Coding Assistants (Cursor, GitHub Copilot):**
1. Add the **Full Version** to your `.cursorrules` file or your workspace's custom instructions to prevent the AI from hallucinating imports or mixing library versions.

## Key Behaviors Enforced

When the Reality Filter is active, the LLM will:
* **Refuse to guess:** If a library API cannot be verified, it will output `[Library API not verified]` instead of making up a function.
* **Admit missing data:** If a RAG retrieval fails to find context, it will say `[No supporting evidence was retrieved]` rather than answering from unrelated training data.
* **Separate code from pseudocode:** It will never present unverified pseudocode as production-ready.
* **Handle conflicts:** If two documents contradict each other, it will present both sides and state `[Sources conflict on this point]` instead of silently picking one.
* **Calculate carefully:** In multi-step math or logic, it will isolate premises and ensure the final conclusion is no more certain than its weakest link.

## Contributing

Found an edge case where an LLM still hallucinates despite the filter? Have an idea to make the rules stricter or more efficient? 
Feel free to open an issue or submit a Pull Request with your proposed changes to the filter rules!

## License

This project is open-source and available under the MIT License. Use it freely in your personal and commercial AI projects.
