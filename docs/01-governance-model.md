[⬅️ Back to index](../README.md)

# Part A — The governance model

## A1. Why the old app-governance model bends

The app-era model does not disappear — it becomes the foundation. Agent governance extends it, question by question, wherever agents introduce new risk.

| App-era governance | Agent-era extension |
|---|---|
| Who can build apps and flows? | Who can build agents with data and tool access? |
| Which environment should this solution use? | Which zone is safe for this agent's knowledge, actions, and audience? |
| Which connectors are allowed? | Which actions, MCP servers, A2A connections, and APIs are allowed? |
| Who owns the app? | Who owns the agent, its identity, its tools, and its business outcome? |
| Is it production-ready? | Has it been reviewed, tested, monitored, and assigned an incident owner? |
| How do we retire the app? | How do we retire the agent, identity, credentials, access, and connected tools? |

The old model works — until agents hit five stress points. Each one is a place where maker-access controls alone stop being enough:

- **Data access** — agents read or write SharePoint, email, ERP, and customer records directly.
- **Tool & API access** — agents call connectors, MCP servers, or APIs with their own credentials, not a delegated user session.
- **Privileged identity** — an agent can hold an email address, calendar access, or a service identity and act like a person in the system.
- **Autonomous behavior** — decisions happen at machine speed, without a human in every loop.
- **Cross-platform ownership** — a single agent can span Power Platform, M365, Azure, Security, and Data — no one team owns the whole thing by default.

> [!IMPORTANT]
> Remember this line: **"Inventory without ownership is not governance."** Seeing agents in a list is not the same as governing them — ownership and process decide outcomes.

## A2. Operating model: who owns which part of the agent lifecycle

Agent 365 is an important control plane, but it is not your governance model. The governance model decides who owns each of these areas.

| Area | Primary owner | Supporting teams | Governance question |
|---|---|---|---|
| Maker access | Power Platform / CoE | Entra admins | Who is allowed to build? |
| Environment strategy | Power Platform admins | Security, business owners | Where can agents run? |
| Agent identity | Entra / IAM team | App owners, platform team | Who or what is the agent acting as? |
| Data exposure | Data governance / Purview | Business data owners | What content can the agent use? |
| Production approval | CoE / platform team | Business owner, security | When is review required before go-live? |
| Runtime protection | Security operations (SOC) | Power Platform admins | Who reacts when behavior looks risky? |
| Lifecycle & retirement | CoE / platform team | Business owner, IAM | Who monitors, retires, and cleans up access? |

## A3. The three governance pillars

These three pillars apply at every zone — the controls just get deeper as zone maturity increases. Skip one and you get a predictable failure mode: security-only programs produce zombie agents nobody retires; reporting-only programs have no enforcement.

### Security controls
- Access management & encryption
- Connector policies (ACP) via PPAC
- Purview DLP + sensitivity labels
- Runtime threat protection (Zone 3)
- Purview Information Protection

### Management controls
- Agent lifecycle: create → deploy → decommission
- Role-based access + environment scoping
- ALM pipelines: Dev → Test → Prod
- Agent publishing controls
- Owner reassignment & sharing limits

### Agent reporting
- Inventory: tenant-wide app/agent catalog
- Monitoring: session health, degradation alerts
- Security: connector posture + recommendations
- Copilot: ROI dashboard + governance command center
- Purview: cross-tenant compliance layer

## A4. The three governance zones

Zones are distinct governance maturity levels, implemented as **Environment Groups in PPAC** — not just a naming convention. Environment Routing sends every maker to the right zone automatically on first login.

| | Zone 1 — Personal Productivity | Zone 2 — Team Collaboration | Zone 3 — Enterprise Managed |
|---|---|---|---|
| **Who** | Individual makers | Department / team | Central IT / CoE |
| **Scope** | Low risk / low complexity | Medium risk / medium complexity | High risk / high complexity |
| **Environment type** | Personal Developer Env | Managed Dept Env | Enterprise Managed Env |
| **Sharing** | Disabled or very limited | Entra security groups | Org-wide via catalog |

> [!NOTE]
> **Promotion triggers:** 1→2 when sharing is needed beyond the maker (team-level use or collaboration). 2→3 when the agent is business-critical, needs org-wide rollout, touches elevated data, or has compliance requirements.

Suggested tool stack per zone (build out further as your maturity increases):

- **Zone 1** — M365 Admin Center for oversight; agents grounded in M365 data only; SharePoint permissions govern access (agents inherit the user's access — never over-permission).
- **Zone 2** — add Purview DSPM for AI to surface risky usage and sensitive grounding data; ALM pipelines with Dev → Test → Prod and approvals become mandatory.
- **Zone 3** — full compliance stack: Purview DLP + Information Protection + eDiscovery, Defender runtime protection via Microsoft Agent 365, and Sentinel-style monitoring for anomaly detection. Publishing is change-controlled with phased rollout.

---

⬅️ [How to use this kit](00-how-to-use-this-kit.md)  ·  [🏠 Index](../README.md)  ·  [Part B — Before you touch PPAC](02-before-you-touch-ppac.md) ➡️
