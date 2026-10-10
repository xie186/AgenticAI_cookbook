
# What Is Agentic AI?

The previous sections introduced the LLM as a reasoning engine and RAG as a way to ground that engine in current, verified information. Agentic AI takes the next step: instead of simply answering a prompt, the system is given a goal, and it works toward completing that goal autonomously, with minimal human guidance at each step.

This is the key distinction between a chatbot and an agent. A chatbot generates text in response to a prompt and stops. An agent can plan a sequence of steps toward a goal, take actions in the world (not just produce text), adapt when circumstances change mid-task, and ask for help only when it genuinely needs to — rather than at every turn.

## Why do we need Agentic AI?

* Autonomous workflow execution. Traditional generative AI requires a human to supply instructions step by step. Agentic AI instead takes a single high-level `goal`, builds its own plan, and executes that plan independently — turning a multi-step workflow into a single request.

* Tool integration and reasoning. An agent can reason about when it needs help beyond its own internal knowledge, and intelligently invoke external tools — search engines, calculators, databases, APIs — to gather information or perform actions a language model cannot do on its own.

* Process automation. By automating complex, multi-step sequences — research, coding, data processing, and similar workflows — agentic AI scales efficiency and reduces the need for manual intervention at each stage.

## The five components of an agent

An agentic AI system is generally built from five core components:

1. The Brain (LLM). The core intelligence of the system. The LLM interprets the user's goal, plans how to approach it, reasons through intermediate steps, and selects which tools to use.

2. The Orchestrator. The framework that connects the brain to everything else. It manages task sequencing, conditional routing, loops, and delegation — effectively acting as the agent's nervous system.
Tools. External functions, APIs, or databases that let the agent act beyond text generation — querying a database, running a calculation, calling a bioinformatics pipeline, or fetching a file.

3. Memory. Handles both short-term context (the current task's working state) and long-term persistence (chat history and state that carry over across sessions), so the agent doesn't start from zero each time.

4. Human-in-the-Loop (HITL). A control layer that lets the agent pause and ask for human guidance, feedback, or approval — particularly important when an action is costly, irreversible, or uncertain.

A closer look at the Orchestrator
Because the orchestrator is what turns a language model into a functioning agent, it's worth examining its responsibilities in more detail:

Task sequencing — determining the order in which steps must happen to reach the overall goal.
Conditional routing — deciding what to do next based on logic or feedback from the environment (e.g., did a tool call succeed or fail?).
Tool integration — connecting the LLM to external APIs, databases, or file systems, and deciding when each tool actually needs to be called.
Flow control — managing loops, retries, and delegation to sub-tasks so the agent can keep working autonomously rather than stalling.
Human-in-the-loop management — coordinating with the HITL layer to pause execution and surface a decision to a human when the task calls for it.

Why this matters for bioinformatics
A bioinformatics agent built on this architecture might take a goal as simple as "characterize this novel variant and summarize its likely clinical significance." The brain plans the approach; the orchestrator sequences the steps; tools query ClinVar, run a sequence alignment, or call a variant-effect predictor; memory tracks what's been found so far across a multi-step investigation; and HITL pauses the agent before it reports a clinically significant finding, so a human expert can review and approve it before it goes any further. Where a chatbot could only answer questions about a variant you described to it, an agent can go out, gather the evidence itself, and bring back a reasoned, sourced conclusion.

Want me to build a companion figure showing the five components as a loop (Brain → Orchestrator → Tools/Memory/HITL → back to Brain), styled to match the earlier LLM and RAG figures? That would give your chapter a consistent visual language across all three concepts.