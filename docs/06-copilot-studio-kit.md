[⬅️ Back to index](../README.md)

# Part F — Governance tooling: Copilot Studio Kit

## F1. The four tools

The Copilot Studio Kit is a free, open-source Power CAT toolkit ([github.com/microsoft/Power-CAT-Copilot-Studio-Kit](https://github.com/microsoft/Power-CAT-Copilot-Studio-Kit)). It has other components, but for governance and admin audiences these four are what matter. **Agent Inventory is a prerequisite for Compliance Hub** — install and run it first.

| Tool | Role | What it does |
|---|---|---|
| **Agent Inventory** | Tenant visibility | Tenant-wide agent catalog across all environments. Metadata: auth mode, knowledge sources, AI features. Dashboard + list view + export. |
| **Compliance Hub** | Automated enforcement | Continuous compliance monitoring post-creation. Configurable risk thresholds + SLA timers. Cases raised automatically on violation. |
| **Agent Review Tool** | Quality gate | Solution analysis for anti-patterns & security issues. Scores each component (lower = more issues). Covers Power Apps, Power Automate, and Copilot Studio. |
| **Agent Insights Hub** | Deep monitoring | Application Insights integration for production agents. Session-level telemetry and error tracking. Custom dashboards per agent. |

## F2. Agent Review Tool as a quality gate

The Agent Review Tool is not a blocking system on its own — **you define the gate**. It analyzes Copilot Studio custom agents (configuration issues, anti-patterns), Power Automate flows (security and performance concerns), and Power Apps components (bad practices).

Every finding is rated Info / Low / Medium / High / Critical, with remediation guidance linking to docs and step-by-step fixes, plus a drillable pie-chart health view.

### Using it as a production gate

1. **Developer packages the solution** — Agent is ready for promotion to production.
2. **Submit to Agent Review Tool** — Upload the solution file for automated analysis.
3. **Findings reviewed** — CoE / admin reviews the score and severity findings.
4. **Pass threshold?** — Define the minimum score required for promotion — recommended: zero Critical findings, no more than 2 High findings.
5. **Approve or return** — Approve → pipeline promotes to production. Return → maker fixes and resubmits.

> [!TIP]
> Recommended approach: require a review run as part of the ALM pipeline, set an explicit threshold, and make CoE sign-off **mandatory** before the pipeline runs the production deployment step.

---

⬅️ [Part E — Policies: DLP & Advanced Connector Policies](05-policies-dlp-acp.md)  ·  [🏠 Index](../README.md)  ·  [Part G — The production gate model](07-production-gate-model.md) ➡️
