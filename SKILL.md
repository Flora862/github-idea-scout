---
name: oss-research-agent
description: ai open-source project discovery and github repository research workflow. use when the user describes an idea, product need, library need, or vague technical requirement and wants chatgpt to find, compare, rank, or recommend github repositories, open-source alternatives, libraries, frameworks, or tools. triggers include natural-language github search, "has anyone built this", "find repos", "compare open-source projects", "read readmes", "evaluate stars/issues/commits/releases", or "which repo best fits my idea".
---

# OSS Research Agent

Run an agentic open-source research workflow for finding and evaluating GitHub repositories from a natural-language idea. Do not behave like keyword search. Behave like a technical research analyst that uses GitHub data, README content, maintenance signals, community signals, and fit-to-requirement reasoning.

## Core principle

Use the skill to orchestrate research. Use connected GitHub tools or GitHub MCP for data access. Use reasoning for extraction, comparison, and recommendation. Do not build or assume a full-GitHub embedding index.

## Default workflow

1. Restate the user's goal in one sentence.
2. Extract structured requirements:
   - core capabilities
   - nice-to-have capabilities
   - constraints such as self-hosted, local-first, lightweight, license, language, deployment, maturity, or enterprise use
   - likely adjacent categories and ambiguous interpretations
3. Generate multiple search queries, not just the user's words:
   - direct query
   - synonym query
   - implementation/architecture query
   - ecosystem/category query
   - negative/alternative phrasing query
4. Search GitHub repositories with those queries.
5. Build an initial candidate pool, normally 20-30 repositories when available.
6. Cheap-filter candidates using metadata and snippets before reading deeply.
7. Read README or equivalent docs for the top candidates only.
8. Deep-analyze only the most promising 3-5 repositories.
9. Output scenario-based recommendations, tradeoffs, and confidence. Avoid pretending the ranking is absolute.

## Query expansion rules

For every user idea, create 5-10 search phrases. Include:

- user-language phrase
- standard category phrase
- likely GitHub topic phrase
- implementation phrase
- product/alternative phrase
- framework/library phrase
- self-hosted/open-source phrase when relevant
- language/runtime phrase when the user specifies a stack

Example: for "AI can operate browser and make workflows", generate queries like:

- ai browser automation workflow
- agent workflow orchestration browser
- self-hosted ai automation platform
- visual workflow automation open source
- browser-use alternative workflow
- rpa agent framework github

## Candidate filtering policy

Do cheap filtering before expensive reading. Prefer candidates that satisfy several of these signals:

- description/topic match with the extracted capabilities
- stars above a context-appropriate threshold; default prefer >100, but keep niche repos if fit is high
- recent activity within 6-12 months, unless the repo appears stable/mature
- has a useful README or docs
- has releases or tags
- has examples, demos, screenshots, quickstart, or templates
- has open-source license visible
- has active issues/PRs or recent maintainer responses

Do not discard a highly relevant niche repo only because it has low stars. Mark it as "high fit, low adoption".

## Token budget policy

Always control reading depth.

- Search broadly, read narrowly.
- Initially inspect only metadata, description, topics, stars, forks, pushed_at, open issues count, license, homepage, and README outline/snippet if available.
- Read README for the top 8-10 candidates max.
- For README, read the beginning and sections likely named overview, features, quickstart, installation, deployment, examples, architecture, integrations, limitations, roadmap, comparison, and license.
- Deep-read full README/docs only for top 3-5 candidates.
- Inspect issues/PRs/releases only for finalists.
- Inspect code only when the user explicitly asks for code-level due diligence or when README evidence is insufficient.

## Repository quality signals

Evaluate quality using multiple dimensions. Stars are only one weak signal.

### Fit signals

- capability match: does it actually do the thing the user wants?
- abstraction level: library, framework, platform, app, infrastructure, SaaS-compatible, self-hosted
- scope match: too narrow, appropriate, too broad, too low-level, too enterprise-heavy
- extensibility: plugin system, SDK, API, webhooks, custom nodes, adapters
- deployment fit: local, Docker, Docker Compose, Kubernetes, cloud-only, desktop, browser extension
- stack fit: language/runtime/framework alignment with user constraints

### Usability signals

- time-to-first-value: can a user run it in minutes?
- clear quickstart
- examples and templates
- screenshots/demo/video
- simple configuration
- documented deployment path
- common failure modes documented

### Maintenance signals

- recent commits, but do not overvalue commit frequency for stable projects
- release cadence and semantic versioning
- changelog or release notes
- maintainer response in issues
- PR merge activity
- CI status where visible
- dependency freshness if visible
- archived/deprecated warning

### Community signals

- issue close ratio and issue age
- discussion quality
- maintainer responsiveness
- contributor diversity and bus factor
- forks with meaningful activity
- external mentions if available through web search: Hacker News, Reddit, blog posts, docs, benchmarks
- signs of real users: examples, integrations, tutorials, production references, case studies

### Project maturity signals

- license clarity
- security policy
- contribution guide
- code of conduct, when community project
- tests/CI badges
- versioned releases
- migration guides or breaking change notes
- documentation site
- roadmap and governance

### Risk signals

- abandoned or archived
- README promises far more than issues/releases support
- many unresolved installation bugs
- no license
- one-person project with no release discipline
- excessive open issues without maintainer replies
- cloud-only despite self-hosted requirement
- unclear business model for open-core projects
- incompatible license
- poor docs or no quickstart

## Scoring rubric

Use scores internally to structure thinking, but present them as estimates, not objective truth.

Default weights:

- requirement fit: 35%
- usability/time-to-first-value: 15%
- maintenance health: 15%
- community/adoption: 15%
- extensibility/ecosystem: 10%
- risk/license/deployment fit: 10%

Adjust weights when the user states priorities. For production use, increase maintenance, security, and release weights. For experimentation, increase fit and quickstart weights. For enterprise, increase governance, license, security, and integration weights.

## Evidence collection checklist

For each finalist, try to collect:

- repository name and URL
- one-sentence project purpose
- stars, forks, license, latest release, last push/commit when available
- README evidence for core capability
- installation/deployment evidence
- examples/docs evidence
- issue or PR health snapshot
- risks and mismatches

Use citations/links when the environment supports them. If exact metadata could not be verified, say so.

## Output format

Use this structure unless the user asks otherwise:

1. **Conclusion first**: name the best fit and why.
2. **Recommendation buckets**:
   - best overall fit
   - best lightweight/quickstart option
   - best mature/production option
   - best adjacent/partial fit
   - not recommended / only useful if your real need is different
3. **Comparison table** with columns:
   - repo
   - fit
   - why it matches
   - key strengths
   - risks / missing pieces
   - maturity signal
4. **Deep notes on top 3**:
   - what it is
   - why it fits
   - where it fails
   - when to choose it
5. **Next action**:
   - which repo to inspect first
   - what to test in 30 minutes
   - what follow-up search would reduce uncertainty

Do not output a long undifferentiated list of repositories. Explain why each recommendation is useful.

## Handling uncertainty

Be explicit about uncertainty. Say when:

- the search may have missed repos due to GitHub keyword limitations
- README was incomplete
- issue/release data was not checked
- project quality cannot be inferred without running it
- a repo is promising but low-adoption

## When using CodeX or a coding agent

If CodeX or another coding agent is available, use it only after narrowing candidates. Useful CodeX tasks:

- clone finalist repos
- inspect directory structure
- check install instructions
- run tests or demo commands in a sandbox
- summarize architecture from files
- verify Docker Compose or package setup

Do not run untrusted code unless the user explicitly requests runtime evaluation and the environment is sandboxed.
