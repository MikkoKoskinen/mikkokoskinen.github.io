[⬅️ Back to index](../README.md)

# Part H — Monitoring & threat protection

## H1. Microsoft Defender & Purview in practice

Real-time runtime protection plus data security and compliance for AI agents.

### Defender — detect: automatic agent discovery
- Auto-detects all custom Copilot Studio agents — including ones IT did not know about
- Feeds the AI agent inventory and advanced hunting / XDR
- Audit-log collection, continuous monitoring for suspicious activity

### Defender — protect: real-time runtime protection
- Built-in defense against UPIA (user prompt injection) and XPIA (cross-domain) attacks
- Flow: agent forwards a planned action to Defender — roughly 1 second to decide block/allow
- If no decision arrives in time, the agent defaults to Allow or Block per your configuration

### Purview — DSPM for AI: discover & investigate data risk
- One place to discover and investigate every AI interaction across Copilot Studio, M365 Copilot, and third-party agents
- Oversharing assessments — find where agents could surface sensitive content
- DLP by sensitivity label or sensitive information type; maker audit logs surfaced to admins

### Beyond the agent: Entra Global Secure Access
- Outbound web calls pass through a web filtering proxy and threat intelligence engine
- A failed check returns 502/403 and the call is blocked; content is inspected via Purview
- The GSA baseline profile applies to all users and agents enabled for protection — also configurable per Environment Group

## H2. Security in action — what to check

1. **Defender for Cloud Apps: AI Agent Inventory** — Auto-discovered agent list, risk scores, data access patterns. Setup: enable AI Agent Inventory in Defender settings.
2. **Purview DSPM for AI: AI Hub** — AI interaction discovery, oversharing assessments, DLP coverage across Copilot Studio and M365 Copilot.
3. **Defender: real-time alert** — UPIA/XPIA alert in Defender XDR — action forwarded, 1-second decision, block or allow. Audit log entry created.
4. **KQL for the audit trail:**

```kql
CloudAppEvents
| where Application == "Microsoft Copilot Studio"
| project TimeGenerated, UserPrincipalName, ActionType, ActivityObjects
```

## H3. Zoned security operations

A day-two operations view of the same three zones — who builds, what's secured, how it's governed, and how it's monitored.

| | Zone 1 — Citizen dev (DIY) | Zone 2 — Team / department | Zone 3 — Professional dev / IT-led |
|---|---|---|---|
| **Purpose** | Personal use and experimentation with safe defaults | Agents built by trained citizen developers, with formal assistance and oversight from a DIY coach | Large, potentially risky agents — reserved for pro dev & IT-led development only |
| **Secure** | Only M365 and Power Platform connectors; agents run in the user's context only | Zone-specific Advanced Connector Policies in PPAC; teams share access to approved data sources | Zone-specific ACP in PPAC + Purview; scale with Environment Groups + rules |
| **Govern** | Personal-use agents in Developer Environments; Environment Routing keeps agents isolated to the maker; sharing disabled and scoped to maker use only | Admin-approved environment provisioning; scoped roles and sharing policies | ALM pipelines for agent versioning; IT-admin approval required to publish |
| **Monitor** | Manage sharing via Integrated Apps in the Microsoft Admin Center | Review agent usage in Copilot Hub in Power Platform | Track agent usage and security posture in Microsoft Admin Center, Microsoft Purview, and Power Platform Admin Center |

## H4. What to monitor, day to day

Six dimensions worth a recurring dashboard review, not just a one-time audit:

| Dimension | What to look at |
|---|---|
| Usage | Volume, sessions, runs, active users — by product & resource |
| Adoption | Who is using what, frequency, depth, maker activity, tenant rollout |
| Performance | Latency, success rates, errors, resolution & engagement quality |
| Anomalies | Inventory, DLP, sprawl, orphaned resources, audit |
| Token & cost | Copilot Credits, token-metered AI tools, capacity & overage |
| Governance | Spikes, failures, drift, throttling — and the alerting gap |

---

⬅️ [Part G — The production gate model](07-production-gate-model.md)  ·  [🏠 Index](../README.md)  ·  [Part I — Self-assessment: where are you today](09-self-assessment.md) ➡️
