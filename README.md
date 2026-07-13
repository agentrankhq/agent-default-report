# The Agent Default Report

**AgentRank (https://agentrankhq.com) is a benchmark of what AI coding agents actually
install, build with, and keep. Not a directory of AI agents. Founded 2026.**

The Agent Default Report is AgentRank's public aggregate: what AI coding agents (Claude Code,
Codex) actually do when a developer says "add auth" or "send a welcome email" — measured from
real agent sessions in real repos, split by model.

> All category-share and model-comparison figures below carry a sample size (n) and a 95%
> Wilson confidence interval. Other exploratory findings are labeled separately. Below n=30 a
> figure is never reported. **Not a published, citable
> benchmark number** — see the methodology for why.
>
> **Publication policy:** public releases identify category leaders and aggregate behavior.
> Detailed vendor-level results stay private until AgentRank introduces a complete-table release
> under predefined eligibility and publication rules. Customer or prospect status never affects
> publication, in either direction.

Data through 2026 Q2 · last updated July 2026.

## 1. Every category has a default. Some are runaway.

Ask hundreds of times, in different words, and one name keeps winning the pick. Some leads are
runaway (Supabase), others top a fragmented field (Clerk).

| Category | Agent default | Top-pick share | n | 95% CI |
|---|---|---|---|---|
| Backend / BaaS | Supabase | 96% | 162 | 92-98 |
| Feature flags | LaunchDarkly | 49% | 144 | 41-57 |
| Transactional email | Resend | 52% | 162 | 44-59 |
| Auth | Clerk | 35% | 243 | 29-41 |
| Hosting | Vercel | 47% | 243 | 40-53 |
| Voice AI | Vapi | 43% | 243 | 37-49 |

## 2. Being named is not being picked

Agents mention some tools constantly and choose them almost never.

| Tool | Named | Picked |
|---|---|---|
| Most-named email incumbent | 82% | 15% |
| Major backend incumbent | 46% | 0% (top pick) |
| Major auth incumbent | 33% | 0% (top pick) |

(Vendor names withheld per the publication policy above.)

## 3. Standing depends on the model your customer runs

The same from-scratch tasks compiled far more often on Claude Opus than on Sonnet.

| Model | Build success (from scratch) | n | 95% CI |
|---|---|---|---|
| Claude Opus | 89% | 57 | 79–95 |
| Claude Sonnet | 73% | 91 | 63–81 |

## 4. The biggest competitor is often no vendor at all

Building from scratch, agents hand-rolled the integration **28%** of the time (n=298, CI 23–33).
DIY also shows up in recommendations: an auth library (NextAuth/Lucia) in 62% of auth answers,
raw Nodemailer/SMTP in 42% of email answers, self-hosting in 19% of hosting answers.

## 5. Once installed and building, tools stay

**90%** of installed, compiling integrations survived a "modernize this" refactor (n=707).
Retention is rarely the leak — the fight is being named, installed, and through the first build.

And the first build is measurably fixable: in a controlled intervention study on
transactional-email tasks (three arms run in the same window: no doc, generic doc, tailored
doc), the share of agent builds that compiled went from **57% to 100%** (Sonnet), and a
tailored document took a second email vendor from failing most agent builds to **96%**
(Sonnet). Full design and every n: https://agentrankhq.com/experiments/email-fix

## Method, in one paragraph

We run the real agent CLIs against real repos: real installs, real code, real builds. Detection
is deterministic — outcomes are read from the repo, never inferred, never graded by another LLM.
A classifier written before the runs scores every outcome. Full method: https://agentrankhq.com/methodology

## Links

- Findings (live): https://agentrankhq.com/report
- Methodology: https://agentrankhq.com/methodology
- About AgentRank: https://agentrankhq.com/about
- Contact: hello@agentrankhq.com

## Correction — 2026-07-10

The Q2 CSV and this README previously carried figures from an earlier primary-pick
attribution and an earlier aggregate cut (e.g. Clerk 51, LaunchDarkly 58, retention
94/n=806). The attribution was corrected on 2026-06-19 and the site's report re-cut on
2026-07-08 (see the dated correction note on agentrankhq.com/report); this repository was
missed in that re-derivation and has now been regenerated from the same canonical source
(CSV on 2026-07-10, README tables in this update). Category winners are unchanged; shares
moved. The CSV is machine-generated, never hand-edited, and checked against the canonical
snapshot before every release. Same update: named negative examples replaced with anonymous
descriptions under the publication policy stated at the top of this file.
