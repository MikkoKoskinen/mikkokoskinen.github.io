[⬅️ Back to index](../README.md)

# Part E — Policies: DLP & Advanced Connector Policies

DLP posture should differ by zone. Sandboxes need to stay broad — makers need room to explore. Shared Dev and Production should be locked to approved data sources only.

- **Zone 1 (Sandbox)** — broader DLP posture; agents run in the maker's own context; zone-specific Advanced Connector Policies applied via PPAC.
- **Zone 2 (Shared Dev)** — teams share access to approved data sources only; zone-specific ACP plus Purview coverage.
- **Zone 3 (Production)** — locked to approved sources; ALM pipeline is the only path from Dev to Prod; IT-admin approval required to publish.

> [!WARNING]
> Advanced Connector Policies (ACP) govern at the **action level**, not just the connector level — the same connector can have different rules for apps vs. agents. ACP also governs which **MCP servers** an agent is allowed to call. That's the bridge between classic connector governance and the agentic era — treat external MCP servers and A2A connections as **untrusted by default**. Note: disabling an A2A connection can take up to **48 hours** to fully propagate, so plan incident response accordingly.

---

⬅️ [Part D — Environment architecture & PPAC configuration](04-environment-architecture-ppac-configuration.md)  ·  [🏠 Index](../README.md)  ·  [Part F — Governance tooling: Copilot Studio Kit](06-copilot-studio-kit.md) ➡️
