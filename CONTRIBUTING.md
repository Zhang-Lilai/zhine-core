# Contributing to Zhiné（知你）

Thank you for helping build an open personal cognitive infrastructure! When submitting Code or Specifications (Specs), please adhere strictly to these principles:

1. **Layered Openness**: In the initial stage, we prioritize debating and standardizing the schema formats in `specs/` (Memory Schema, Skill Card, etc.) before rushing into massive code implementations[cite: 1].
2. **Local First Integration**: Any new capability must run locally and offline by default. Remote calls must include explicit, granular user authorization and data anonymization layers[cite: 1].
3. **Rollbackable by Design**: Any code modification affecting personal assets (e.g., updating memories or expanding skills) must be accompanied by an execution path for generating an `Evolution Log` and its inverse rollback function[cite: 1].

### Pull Request Steps
1. Fork the repository.
2. Create your feature branch: `git checkout -b feat/cognitive-runtime`
3. Verify that your local runtime test data or personal diaries are NOT captured in your git staging area.
4. Submit the PR and link it to an open Issue tracker.