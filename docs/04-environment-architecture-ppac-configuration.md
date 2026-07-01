[⬅️ Back to index](../README.md)

# Part D — Environment architecture & PPAC configuration

## D1. The three environments

The recommended design: personal developer sandboxes plus shared productivity environments, governed automatically via Environment Groups. One Entra group addition triggers Studio access, sandbox routing, and Shared Dev maker role — all at once.

| | CS Developer Sandbox | Shared Dev | Production |
|---|---|---|---|
| **How created** | Auto-provisioned via Environment Routing on first Copilot Studio login | All CS Authors auto-added via Entra Group Team → Environment Maker role | Admin-controlled deployment only — no direct maker publishing |
| **Governance** | Managed Env + Group Rules: sharing limits, maker onboarding, ACP | Managed environment — separate security group | ALM Pipeline with approval gate from Dev → Prod |
| **Rules** | Agent sharing: max 5 people, no Editor permission to groups | Dev for agent building, testing & review before production | Separate Entra security group — makers are NOT members |
| **Policies** | ACP set via Environment Group Rule — applies to all sandboxes automatically | ACP via Environment Group Rule | ACP via Environment Group Rule |

## D2. Step-by-step PPAC configuration

The implementation sequence. All four steps are configured in the Power Platform Admin Center (PPAC).

1. **Step 1 — Create Environment Groups.** PPAC → Manage → Environment Groups. Create one group per tier: Sandboxes, Dev, Prod. Rules set at the group level cascade automatically to every environment inside — no individual configuration needed.
2. **Step 2 — Enable Environment Routing.** PPAC → Manage → Environment Groups → Environment Routing. Tick Copilot Studio specifically — not Power Apps or Automate, which have separate governance. Priority 1 rule: security group "Everyone" routes to Sandboxes. You can create up to 25 rules — e.g. a pilot group routes to Dev, everyone else to Sandboxes.
3. **Step 3 — Configure the Shared Dev environment.** Set the environment to Sandbox type with Managed Environment enabled — this unlocks sharing limits, ACP, and audit features. All CS Authors must be members of the environment's security group to access it. Enable auditing for production-bound environments.
4. **Step 4 — Entra ID Group Team → Environment Maker role.** In the Shared Dev environment, create a Team of type "Microsoft Entra ID Security Group" (not Owner or AAD Office group), linked to the CS Authors group. Assign the Environment Maker role to that team. Every user added to CS Authors immediately gets Environment Maker — no manual steps. Removing them from the group revokes all access instantly: sandbox, shared dev, and Copilot Studio authoring.

## D3. The Entra group chain

The six-step chain worth memorizing — and worth saying out loud when you explain the design to a colleague:

1. Create the CS Authors Entra ID group
2. Set it as the Authoring Group in PPAC
3. Enable routing to the Sandbox Environment Group
4. Add it to the Dev environment's security group
5. Create an Entra Group Team and assign Environment Maker
6. Result: one group addition provisions everything automatically

> [!TIP]
> The inverse is just as true: removing someone from the CS Authors group revokes every downstream access in one action. This is your single highest-leverage governance control — and it costs zero manual IT work per maker.

---

⬅️ [Part C — Maker onboarding](03-maker-onboarding.md)  ·  [🏠 Index](../README.md)  ·  [Part E — Policies: DLP & Advanced Connector Policies](05-policies-dlp-acp.md) ➡️
