---
name: portfolio-readme
description: >
  Write or rewrite GitHub README files for student and early-career engineering portfolio projects — especially cloud infrastructure, distributed systems, microservices, AppSec, DevOps, and platform engineering projects. Use this skill whenever the user says "write a README", "help me with my README", "improve my GitHub README", "make my project look better on GitHub", or pastes a README and asks for feedback. Also trigger when the user describes a project and wants help explaining it to recruiters, hiring managers, or senior engineers. This skill enforces strict rules: no vendor documentation padding, no hallucinated knowledge, no explaining what managed services are, mandatory design-trade-off sections, and external links only to official docs. It produces READMEs that show engineering judgment rather than feature lists.
---

# Portfolio README Skill

Produces GitHub READMEs for portfolio projects that reveal **engineering judgment** — not product brochures. Aimed at a **mixed audience**: recruiters scanning for keywords, hiring managers checking depth, and senior engineers reading for thinking quality.

Primary context: **microservices / distributed systems across cloud platforms**.

---

## Core Mandate

> "Anyone can describe what a tool does. Only engineers explain *why they chose it*."

Every README this skill produces must pass one test:  
**Would a senior engineer learn something about this person's thinking from reading this?**

---

## Non-Negotiable Rules

### Rule 1 — No Vendor Documentation Padding

**NEVER** write paragraphs explaining what a managed service is. The audience knows.

❌ Forbidden pattern:
> "Cloud SQL for PostgreSQL is a fully managed relational database service provided by Google Cloud that handles patching, backups, and high availability automatically..."

✅ Required pattern:
> "Used Cloud SQL (PostgreSQL) — [docs](https://cloud.google.com/sql/docs) — over self-managed Postgres on GCE to eliminate operational overhead for a solo project; acceptable trade-off given no need for custom extensions."

One sentence. Service name. Link. **Why you chose it for this specific project.**

### Rule 2 — No Hallucinated Knowledge

**NEVER** invent design trade-offs, cost figures, latency numbers, failure modes, or limitations that the user did not provide. If the user hasn't told you something, you have two options only:

1. Ask the user for the information before writing that section.
2. Insert a clearly marked placeholder: `<!-- TODO: add your observed latency here -->`

**Do not fill gaps with plausible-sounding technical detail.** A recruiter may ask about it in an interview. The author must be able to defend every sentence.

### Rule 3 — Links Must Be Official or Clearly-Attributed

Acceptable link sources (in order of preference):
- Official product docs (e.g., `cloud.google.com/datastream/docs`, `docs.aws.amazon.com`, `istio.io/docs`)
- CNCF project sites (e.g., `opentelemetry.io`, `argo-cd.readthedocs.io`, `prometheus.io/docs`)
- Official GitHub repos for open-source tools (e.g., `github.com/open-telemetry/opentelemetry-collector`)
- Well-known community guides **only** if prefixed with `[Community Guide]` in the link text

❌ Never link to: Medium posts, random blogs, tutorials without attribution, or any URL you cannot verify exists.

**If you cannot produce a real, known-good URL for a service, write the service name without a link and add `<!-- TODO: add official doc link -->`.**

### Rule 4 — Design Trade-Off Sections Are Mandatory

Every README must include a `## Design Decisions & Trade-offs` section with at least **3 comparative decisions** in the format below. These must come from information the user actually provided — not invented.

---

## Required README Structure

```markdown
# [Project Name]

> One-sentence hook: what problem this solves and for whom.

## What This Does (User-Facing Summary)
<!-- 3–5 sentences. What does it do? Who would use it? What triggers it? -->
<!-- No architecture jargon here. Pretend you're explaining to a PM. -->

## Architecture
<!-- Diagram if you have one. If not, a numbered data-flow description. -->
<!-- Each component: name, official doc link, ONE sentence on its role in THIS system. -->

## Design Decisions & Trade-offs
<!-- MANDATORY. Minimum 3 decisions. Use the decision template below. -->

## What I'd Do Differently
<!-- Honest reflection. Shows growth mindset. 2–4 bullet points. -->
<!-- If user hasn't provided this, insert TODO placeholder. -->

## Known Limitations
<!-- Real constraints you hit. Not theoretical ones. -->
<!-- Examples: "Datastream replication lag spikes under bulk inserts (observed ~8s)" -->
<!-- If user hasn't provided numbers, insert TODO placeholder. -->

## Running It
<!-- Actual commands that work. If it requires cloud setup, say so explicitly. -->

## Cost Estimate
<!-- Even rough: "~$X/month at idle on free tier" or "not measured — TODO" -->
```

---

## Decision Template

For every entry in `## Design Decisions & Trade-offs`, use this structure:

```markdown
### Why [Chosen Tool] over [Alternative]?

**Chosen:** [Tool] — [Official Docs Link]  
**Alternatives considered:** [Tool A], [Tool B]

**Decision:** [1–3 sentences explaining the actual reason for this specific project. 
Must reference a real constraint: cost, skill, latency, ops burden, data volume, team size, etc.]

**Trade-off accepted:** [What you gave up by making this choice. Be honest.]

**Would reconsider if:** [Under what conditions would you switch? Shows you understand the limits.]
```

Examples of good decisions (fill in with real user data):
- Datastream vs Debezium vs Kafka Connect
- BigQuery vs Cloud Storage vs AlloyDB
- EventBridge vs SNS/SQS vs Kinesis
- Managed Kubernetes vs Cloud Run vs EC2
- GuardDuty vs self-hosted SIEM

---

## Tone & Length Guidelines

| Section | Target length | Tone |
|---|---|---|
| Hook | 1 sentence | Punchy, specific |
| What This Does | 3–5 sentences | Plain English, no jargon |
| Architecture | Medium | Technical, precise |
| Design Decisions | Long | Engineering voice, honest |
| What I'd Do Differently | Short | Reflective, confident |
| Known Limitations | Short | Factual, no hedging |
| Running It | As needed | Exact commands |

**Total target:** 600–1200 words for a solo project. More is not better.

---

## What to Ask the User Before Writing

Before writing any trade-off section, confirm you have answers to:

1. What alternatives did you actually consider (even briefly)?
2. Why did you rule them out — cost, complexity, time, missing feature?
3. What broke or surprised you during the build?
4. What would you change if you had more time/money?
5. Any real numbers — latency, cost, throughput, error rates?

If the user can't answer some of these, use `<!-- TODO -->` placeholders. Never invent the answers.

---

## Anti-Patterns to Refuse

If the user's draft README contains any of these, flag them and rewrite:

| Anti-pattern | Why it fails | Fix |
|---|---|---|
| "X is a fully managed service that..." | Everyone knows. Wastes space. | Replace with why you chose X. |
| "This project uses cutting-edge technology" | Meaningless marketing. | Delete. |
| Architecture diagram with no explanation | Can't read minds. | Add numbered flow description. |
| No alternatives mentioned | Looks like first-option-wins thinking. | Add trade-off section. |
| "Future work: add Kubernetes" | Vague aspiration. | Either explain why you didn't now, or cut. |
| Numbers without source | Can't defend in interview. | Add "(observed)" or "(estimated)" or remove. |

---

## Reference Files

See `references/link-registry.md` for a curated list of official doc URLs for common cloud/platform services. Read it before generating links to avoid hallucinated URLs.
