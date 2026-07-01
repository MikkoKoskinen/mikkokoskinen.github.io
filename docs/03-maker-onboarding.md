[⬅️ Back to index](../README.md)

# Part C — Maker onboarding

## C1. The onboarding flow: request → train → approve

Adding a user to the CS Authors Entra ID group triggers all downstream access automatically. That single group is the control point — design the process around it.

1. **Request access** — Maker submits an access request via an internal portal. This triggers a review workflow. Opt-in model — only approved makers can build.
2. **Training & policy** — Maker completes mandatory Copilot Studio training and acknowledges the acceptable use policy. CoE verifies completion before approval.
3. **Approval & zone assignment** — CoE/IT approves → user is added to the CS Authors Entra group. Environment Routing places the maker in Zone 1 (Personal) by default.

> [!IMPORTANT]
> **Key principle — single trigger, full access:** one Entra group action provisions all downstream access automatically. No manual IT work per new maker, and a full audit trail: every access change is tied to a named group membership change. Offboarding is the same action in reverse — remove from the group, all access is revoked instantly.

## C2. Licensing: choose your path

There are two license paths and one setting that matters regardless of which path you choose.

| Path | Best for | Notes |
|---|---|---|
| M365 Copilot + Studio permission | Orgs with M365 Copilot already broadly deployed | Easiest path if the license is already there — but the Copilot Studio app permission can be removed from M365 to prevent uncontrolled access; gate with the PPAC Authoring Group instead. |
| Copilot Studio Maker license | Dedicated makers or third-party consultants | Purpose-built, decoupled from M365 Copilot. Cleaner governance: license = intent to build. |
| ⭐ PPAC Authoring Group | Every organization, regardless of license path | **The critical gate.** Create an Entra ID group (e.g. "CS Authors"), set it in PPAC Copilot Settings. Without this, any licensed user can open Copilot Studio and start building. Configure this first. |

---

⬅️ [Part B — Before you touch PPAC](02-before-you-touch-ppac.md)  ·  [🏠 Index](../README.md)  ·  [Part D — Environment architecture & PPAC configuration](04-environment-architecture-ppac-configuration.md) ➡️
