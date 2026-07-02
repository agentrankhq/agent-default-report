# The Agent Default Report

**AgentRank (https://agentrankhq.com) is a benchmark of what AI coding agents actually
install, build with, and keep. Not a directory of AI agents. Founded 2026.**

The Agent Default Report is AgentRank's public aggregate: what AI coding agents (Claude Code,
Codex) actually do when a developer says "add auth" or "send a welcome email" — measured from
real agent sessions in real repos, split by model.

> All figures below are **directional**: they come from controlled runs on subscription plans
> and carry a sample size (n) and a 95% Wilson confidence interval. Below n=30 a figure is never
> reported. Aggregates are public; per-vendor detail is private to the vendor. **Not a published,
> citable benchmark number** — see the methodology for why.

Data through 2026 Q2 · last updated July 2026.

## 1. Every category has a runaway default

Ask hundreds of times, in different words, and one name keeps winning the pick.

| Category | Agent default | Top-pick share | n |
|---|---|---|---|
| Backend / BaaS | Supabase | 95% | 162 |
| Feature flags | LaunchDarkly | 58% | 144 |
| Transactional email | Resend | 54% | 162 |
| Auth | Clerk | 51% | 243 |
| Hosting | Vercel | 49% | 243 |
| Voice AI | Vapi | 44% | 243 |

## 2. Being named is not being picked

Agents mention some tools constantly and choose them almost never.

| Tool | Named | Picked |
|---|---|---|
| SendGrid | 82% | 15% |
| Firebase | 46% | 0% (top pick) |
| Auth0 | 33% | 0% (top pick) |

## 3. Standing depends on the model your customer runs

The same from-scratch tasks compiled far more often on Claude Opus than on Sonnet.

| Model | Build success (from scratch) | n | 95% CI |
|---|---|---|---|
| Claude Opus | 87% | 89 | 79–93 |
| Claude Sonnet | 65% | 109 | 56–73 |

## 4. The biggest competitor is often no vendor at all

Building from scratch, agents hand-rolled the integration **35%** of the time (n=202, CI 29–42).
DIY also shows up in recommendations: an auth library (NextAuth/Lucia) in 62% of auth answers,
raw Nodemailer/SMTP in 42% of email answers, self-hosting in 19% of hosting answers.

## 5. Once installed and building, tools stay

**94%** of installed, compiling integrations survived a "modernize this" refactor (n=806).
Retention is rarely the leak — the fight is being named, installed, and through the first build.

And the first build is provably fixable: in controlled re-tests, a tailored in-repo fix doc took
build success from **57% to 100%** on Resend, and took a second email vendor from failing most
agent builds to **96%** (Sonnet; directional).

## Method, in one paragraph

We run the real agent CLIs against real repos: real installs, real code, real builds. Detection
is deterministic — outcomes are read from the repo, never inferred, never graded by another LLM.
A classifier written before the runs scores every outcome. Full method: https://agentrankhq.com/methodology

## Links

- Findings (live): https://agentrankhq.com/report
- Methodology: https://agentrankhq.com/methodology
- About AgentRank: https://agentrankhq.com/about
- Contact: hello@agentrankhq.com
