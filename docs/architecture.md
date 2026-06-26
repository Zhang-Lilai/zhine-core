# System Architecture Concept

## 1. Conceptual Layering
Zhiné（知你）is structurally managed across the following functional planes[cite: 1]:
* **Governance & Control Plane**: Handles permissions, data classification, auditing, and asset rollbacks[cite: 1].
* **Personal Evolution Plane**: Manages experience extraction, skill upgrades, strategy optimization, and benchmark comparisons[cite: 1].
* **Cognitive Runtime**: Orchestrates perception, reasoning, tool routing, planning, and critical evaluation[cite: 1].
* **Personal Cognitive Assets**: The decoupled state of the user's Memory, Knowledge, Skills, and Strategies[cite: 1].
* **Model Execution Layer**: Resolves local execution (via Ollama/llama.cpp) and handles secure routing to Remote Teachers[cite: 1].

## 2. Model Routing Protocol Priorities
When a task is processed, the Model Router evaluates routing choices based on this immutable sequence:
`Security & Permissions > Explicit User Commands > Data Sensitivity > Task Complexity > Cost & Latency`[cite: 1]