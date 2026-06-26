# Security Policy

## Reporting Vulnerabilities
Because Zhiné（知你）handles highly sensitive personal cognitive assets (memories, preferences, documents)[cite: 1], **DO NOT use public GitHub Issues to report privacy leaks, prompt injections, or malicious tool escalations**[cite: 1].

Please securely report all vulnerabilities directly to: `support@oneasy.cc`

## Core Security Boundaries
1. **Data Classification**: Modules interacting with a cloud-based `Remote Teacher` must strip personally identifiable information (PII) before transmission unless explicit authorization is granted[cite: 1].
2. **Tool Governance**: High-risk tool invocations (e.g., file system modifications) must stall by default and await physical human confirmation[cite: 1].