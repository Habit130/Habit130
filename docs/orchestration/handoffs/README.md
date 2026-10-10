# Orchestration Handoffs

This README and naming contract are tracked.
Frozen handoff bodies are local, gitignored owner-machine artifacts.

Names:
- AC-<issue>-v<contract>-a<attempt>-execution.md
- AC-<issue>-v<contract>-a<attempt>-acceptance.md
- ORCH-<scope>-<timestamp>.md

Publish repository-relative path and SHA-256 on the issue.
Never overwrite a file after publishing its digest.
Create a new version or attempt instead.

Acceptance handoffs pin the exact delivery head.
habit starts the fresh Acceptance session.
