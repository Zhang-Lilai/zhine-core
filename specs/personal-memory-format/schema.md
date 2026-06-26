# Personal Memory Format Standard (v0.1)

All ecosystem plugins interacting with the user's memory layer must serialize data matching this structural design[cite: 1]:

| Attribute | Type | Description |
| --- | --- | --- |
| `memory_id` | String | Unique identifier for the memory chunk[cite: 1]. |
| `type` | String | Enum: `profile \| episodic \| semantic \| procedural \| reflective \| preference \| goal \| value`[cite: 1]. |
| `confidence` | Float | Probability metric indicating state validity (0.0 to 1.0)[cite: 1]. |
| `permissions.local_only` | Boolean | True flags that this memory chunk can never leave the local environment[cite: 1]. |

*(Paste the JSON block from Appendix A.1 of Whitepaper v0.2 here as the technical validation reference)*[cite: 1]