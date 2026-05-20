---
name: github-idea-scout
description: ai open-source project discovery and github repository research workflow. use when the user describes an idea, product need, library need, prototype, or vague technical requirement and wants to find, compare, rank, or recommend github repositories. triggers include natural-language github search, has anyone built this, find repos, compare open-source projects, read readmes, evaluate stars/issues/commits/releases, codex github research, or which repo best fits my idea.
---

# GitHub Idea Scout

## Purpose

Use this skill to turn a vague idea into an evidence-backed shortlist of existing open-source GitHub projects. The goal is not to return links. The goal is to help the user decide which repositories are worth trying, forking, integrating, or ignoring.

Do not claim a project works locally unless it has actually been cloned, installed, built, tested, or run in the current task.

## Preferred Tools

Use whichever GitHub access channel is available in the current host: Codex GitHub connectors or plugins, GitHub MCP servers, GitHub CLI, repository connectors, Codex execution, or web search/public GitHub pages as a fallback. MCP is optional; do not require the user to configure GitHub MCP when another GitHub tool is already available.

Prefer GitHub data for repository facts. Use the closest available tool for repository search, README inspection, issue search, PR search, commit search, release inspection, and repository metadata.

## Workflow

### 1. Clarify only when necessary
Ask at most two questions only if missing information would materially change the search. Otherwise proceed and state assumptions.

Infer or state: desired artifact type, reuse goal, must-have features, nice-to-have features, preferred or excluded tech stack, deployment constraints, license constraints, and maturity expectation.

### 2. Build a research brief
Before searching, structure the idea into: core problem statement, primary use case, must-have capabilities, adjacent capabilities, likely category names, implementation terms, GitHub topics, hard constraints, and disqualifiers. Do not trust the user's exact words; vocabulary mismatch is the main failure mode.

### 3. Expand queries
Read `references/search-playbook.md`. Generate several query families: exact wording, synonyms, implementation terms, artifact terms, ecosystem terms, and discovery terms.

### 4. Retrieve broadly, then deduplicate
Initial target: 20-30 plausible candidates. Deduplicate forks, mirrors, renamed projects, and thin wrappers around the same upstream.

### 5. Filter early
Reject or downgrade archived, license-missing, README-poor, toy-only, stale, mismatched, fork-only, or keyword-only repositories. Do not discard a low-star repo solely because it is low-star if it is relevant and active.

### 6. Control token use
Read `references/token-budget.md`. Default limits: metadata scan up to 30 repos; README skim top 8-10; README deep read top 3-5; issues newest 10-20 for top 3-5; PRs newest 5-10 for top 3 when needed; releases newest 3-5 for top 3-5. Avoid code files unless the user asks for code-level verification or README evidence conflicts.

### 7. Evaluate quality beyond stars
Read `references/scoring-rubric.md`. Judge candidates on fit, docs, time-to-first-value, setup complexity, release discipline, issue response, PR activity, contributors, license, integrations, examples, demos, production signals, and community signals. Stars are only one adoption signal.

### 8. Recommend by scenario
Prefer scenario buckets over a fake universal ranking: best overall fit, fast validation, self-hosting, library/API, full application, mature option, lightweight option, promising but risky, lower fit/rejected.

### 9. Output report
Use `references/report-template.md`. Always include assumptions, search strategy, best pick, shortlist, evidence table, candidate details, rejected candidates, risks, validation plan, and confidence level.

Confidence levels: metadata-level, README-level, issue-level, execution-level.

## Stop Condition

Stop when the user has a decision-ready shortlist. Usually 3-7 strong candidates are enough. More links are not better unless the user asks for an exhaustive landscape scan.
