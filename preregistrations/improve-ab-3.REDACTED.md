> **REDACTED PUBLIC COPY (2026-07-13).** The vendor's name is replaced with [VENDOR]
> throughout, per AgentRank's publication policy (naming a vendor's experiment requires
> their consent). The sha256 fingerprint published BEFORE launch —
> `2519d94722e09a2eee21ed855ac96b9fd3258c399d9d26a9ad35634603a89ea7` — is of the
> UNREDACTED original, which reveals unchanged when the vendor consents or at the first
> citable release. This copy differs from the original only in the redaction and this notice.

# Preregistration — improve-ab-3 ([VENDOR] build-fix A/B, co-temporal)

Registered 2026-07-13, BEFORE any run of this study was launched. The sha256 of this
file is committed to the public `agentrankhq/agent-default-report` repository at
registration time (hash public, design private until reveal), and the file itself is
committed to the AgentRank repo in the same sitting. Any change after launch would
change the hash.

## Hypothesis

A tailored, in-repository agent-facing document (`AGENTS.md` for [VENDOR]) increases the
rate at which Claude Code (Sonnet) integrations of [VENDOR] compile, relative to an
identical environment without the document. Prior evidence: the improve-ab-1/2 ladders
(2026 Q2, same harness), which motivated but do not bias this run — this study is a
fresh, co-temporal two-arm replication under a pinned effort level.

## Design

- Two arms, ONE invocation, interleaved in the same window (same afternoon, same
  machine, same network): 
  - **Control** — condition `greenfield`: the `nextjs_saas_email` template, no fix doc.
  - **Treatment** — condition `ax:[vendor]`: identical, plus `ax/[vendor]/AGENTS.md`
    copied into the repository root before the agent starts.
    Treatment artifact sha256: `f8fda1508300ae064cae7db4a5a65d13352b51b91abe071546aa15959875b62d`.
- Agent: `claude-sonnet` (Claude Code CLI, model `claude-sonnet-4-6`), closed-book
  (no WebFetch/WebSearch), hermetic MCP config (zero servers).
- Reasoning effort: pinned `xhigh` (config/agents.yaml `claude_effort_pin`), asserted
  at batch start and recorded per run (harness task #16, shipped 2026-07-13).
- Runs: 20 per cell (40 journeys), `--concurrency 3`, `--seed 2026`.
- Prompt pool: the 24 open-ended transactional-email phrasings; `vendor_named`
  prompts excluded (the doc, not the prompt, is the intervention).
- Billing: `subscription` — this is an EXPLORATORY release run, not a citable one,
  and will be labeled as such wherever reported.
- Runner: Kevin's Mac mini, runs visible on-screen, `caffeinate` held.

## Primary metric (pre-specified)

**[VENDOR] build success per arm**: among runs in that arm where the agent used [VENDOR]
(`installed_vendors` contains `[vendor]`) and a build was executed (`build_passed` is
not NULL), the fraction with `build_passed = true`. Reported per arm as a point
estimate with a 95% Wilson interval. Effect = difference of the two proportions.

## Secondary metric

[VENDOR] first-install share per arm (fresh-build installs / non-error runs). Note: the
treatment document is expected to influence selection as well; that is part of the
lever, not a confound for the primary metric (which conditions on [VENDOR] being used).

## Exclusions (standard classifier rules, unchanged for this study)

Runs classified `error` / infra-failed (network, harness, rate-limit kills) are
excluded from all denominators. No other exclusions. No per-run vetoes.

## Decision rule

Both arms' results are published on the public experiment card REGARDLESS of
direction, magnitude, or how flattering they are, with n and the Wilson intervals.
No statistical-significance claim will be made; the card reports estimates and
intervals. If the treatment arm underperforms the control, that is the published
result.

## Analysis

Computed from the harness `study.db` with the same definitions the public scorecard
uses; the queries will be shown on the experiment card. No new detection logic; the
pre-registered classifier as of the harness commit recorded below.

## Environment pins

- Harness: the `stackrank-harness/` tree at the AgentRank repo commit that contains
  this file (the commit hash is the pin; recorded by git).
- Template: `templates/nextjs_saas_email` (per-run tree hash recorded in each run's
  manifest as always).
