# Agent Governance Start Kit for Admins

![status](https://img.shields.io/badge/status-living%20document-FF4D00)
![source](https://img.shields.io/badge/source-EPPC26-0D1B2A)
![license](https://img.shields.io/badge/license-internal%20reference-5B6472)

A practical playbook for governing Copilot Studio agents — from maker onboarding to production monitoring.

> Based on the EPPC26 session **"Rethinking Governance Models for AI Agents"** by Mikko Koskinen, AI & Copilot Lead at Forward Forever · Microsoft Copilot Studio MVP.
>
> **Audience:** Power Platform admins, M365 admins, architects, and governance leads.

## Start here

New to this kit? Read **[How to use this kit](docs/00-how-to-use-this-kit.md)** first — it explains how the parts fit together.

## Contents

| Part | Page | What's in it |
|---|---|---|
| — | [How to use this kit](docs/00-how-to-use-this-kit.md) | How the kit is organized |
| A | [The governance model](docs/01-governance-model.md) | Why the old model bends, who owns what, the three pillars, the three zones |
| B | [Before you touch PPAC](docs/02-before-you-touch-ppac.md) | The planning questions to answer first |
| C | [Maker onboarding](docs/03-maker-onboarding.md) | Request → train → approve, plus licensing paths |
| D | [Environment architecture & PPAC configuration](docs/04-environment-architecture-ppac-configuration.md) | The three environments, step-by-step config, the Entra group chain |
| E | [Policies: DLP & Advanced Connector Policies](docs/05-policies-dlp-acp.md) | Per-zone DLP posture, ACP, MCP/A2A governance |
| F | [Governance tooling: Copilot Studio Kit](docs/06-copilot-studio-kit.md) | The four Kit tools, Agent Review Tool as a quality gate |
| G | [The production gate model](docs/07-production-gate-model.md) | Six gates for business-critical agents |
| H | [Monitoring & threat protection](docs/08-monitoring-threat-protection.md) | Defender, Purview, what to check, zoned operations |
| I | [Self-assessment](docs/09-self-assessment.md) | Score your current state |
| J | [Governance roadmap](docs/10-governance-roadmap.md) | Three phases, in order |

### Appendices

| Appendix | Page |
|---|---|
| 1 | [One-page tool map](docs/11-appendix-tool-map.md) |
| 2 | [Key takeaways](docs/12-appendix-key-takeaways.md) |
| 3 | [Frequently asked questions](docs/13-appendix-faq.md) |
| 4 | [Next steps & resources](docs/14-appendix-next-steps-resources.md) |

## Core idea

> [!IMPORTANT]
> Agent 365, Copilot Studio Kit, Defender, and Purview are your **control planes**. They enforce what you decide — they are not a substitute for a governance model. This kit helps you build that model first.

## Using this in your own repo

Each page in [`docs/`](docs/) is self-contained and cross-links to its neighbors, so it reads fine directly on GitHub — no site generator required. If you want a browsable docs site later, this structure drops into [MkDocs](https://www.mkdocs.org/) or [Docusaurus](https://docusaurus.io/) with minimal changes (add a nav config pointing at the files in `docs/`).

---

*Maintained by [Mikko Koskinen](https://github.com/) · Forward Forever · Last derived from the EPPC26 presentation.*
