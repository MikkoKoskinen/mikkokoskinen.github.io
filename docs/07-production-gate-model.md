[⬅️ Back to index](../README.md)

# Part G — The production gate model

Not every agent needs this — apply it to agents classified as **business-critical or important**. Gate trigger: high user volume, sensitive data, organization-wide reach, or financial/regulatory impact.

| # | Gate | What happens |
|---|---|---|
| 1 | Build & test | Developer builds in a Zone 1/2 personal or team environment. Automated tests pass (Kit test automation). |
| 2 ⭐ | Agent review | Solution submitted to Agent Review Tool. CoE reviews the score. Zero Critical / High findings required. |
| 3 | Compliance check | Compliance Hub confirms the agent meets all configured risk thresholds before promotion is allowed. |
| 4 | CoE approval | CoE sign-off via Power Platform Pipeline approval step. Agent classified, owner confirmed. |
| 5 ⭐ | Insights Hub setup | Agent registered in Agent Insights Hub. Azure App Insights connection configured and validated. |
| 6 | Production deploy | Pipeline promotes to the production environment. Agent added to Agent Inventory with a 'Production' tag. |

> [!NOTE]
> Gates marked ⭐ (2 and 5) are what the Copilot Studio Kit adds beyond a standard ALM pipeline — a mandatory quality gate, and mandatory production telemetry registration. Everything else is standard ALM practice.

---

⬅️ [Part F — Governance tooling: Copilot Studio Kit](06-copilot-studio-kit.md)  ·  [🏠 Index](../README.md)  ·  [Part H — Monitoring & threat protection](08-monitoring-threat-protection.md) ➡️
