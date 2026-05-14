---
name: github-idea-scout
description: Use when the user wants to find, evaluate, compare, or rank existing GitHub repositories for a natural-language product idea, feature idea, library need, prototype, technical solution, or "has someone already built this?" question. Produces a ranked shortlist with evidence, fit scoring, maintenance signals, license and risk notes, rejected candidates, and validation steps.
---

# GitHub Idea Scout

## Overview

Use this skill to turn a user's rough idea into a ranked, evidence-backed list of existing GitHub projects. The goal is not just to find links; it is to help the user decide which repositories are worth trying first.

This skill is intentionally search-and-evaluation only. Do not claim a repository works locally unless you actually clone, install, build, or run it.

## Default Workflow

1. Restate the user's idea as concrete requirements.
2. Extract:
   - must-have capabilities
   - nice-to-have capabilities
   - preferred and excluded tech stacks
   - artifact type: library, template, full app, CLI, API, service, plugin, demo, or reference implementation
   - license or commercial-use constraints
   - validation target: learn from code, reuse directly, fork, self-host, or integrate as a dependency
3. Ask at most two clarifying questions only when missing constraints would materially change the search. Otherwise make reasonable assumptions and state them.
4. Read `references/search-playbook.md` when building search queries.
5. Search broadly with multiple query families, not one literal phrase.
6. Gather evidence for each candidate:
   - repository URL and owner/name
   - README or docs claims relevant to the idea
   - language and framework
   - stars, forks, last push, release recency, archived status, and license when visible
   - issue and PR activity when visible
   - demo, examples, quickstart, package, or Docker availability when visible
7. Read `references/scoring-rubric.md` before ranking candidates.
8. Exclude poor candidates explicitly instead of hiding them.
9. Return a ranked shortlist and a 30-minute validation plan.

## Search Guidance

Search for repositories, packages, examples, and comparison pages. Include both exact product terms and implementation terms.

Prefer current, primary evidence:
- GitHub repository pages
- README and documentation
- release pages
- issue and PR activity
- package registry pages when relevant
- official project websites linked from the repository

Avoid over-trusting:
- stale blog roundups
- star count alone
- README claims without examples or recent activity
- projects that are demos when the user needs production-ready code

## Ranking Rules

Use a 0-100 score only when enough evidence exists. If evidence is thin, mark confidence as low instead of inventing precision.

Always distinguish:
- `Fit`: Does it solve the user's actual problem?
- `Health`: Is it maintained and usable today?
- `Cost`: How hard is it to adopt or verify?
- `Risk`: What could block real use?

Do not rank a repository highly only because it has many stars. A smaller active project may be better than a famous abandoned one.

## Output Format

Use this structure:

1. `Assumptions`: Briefly state constraints you inferred.
2. `Best Pick`: One repository, with a short reason.
3. `Ranked Shortlist`: Table with rank, repo, fit score, maintenance signal, license, validation effort, and why it matches.
4. `Details`: 2-4 bullets per strong candidate covering evidence, gaps, and integration notes.
5. `Rejected Or Lower-Fit Candidates`: Repos that looked relevant but were excluded, with reasons.
6. `30-Minute Validation Plan`: Concrete next steps to check whether the top 1-3 repos actually work.
7. `Confidence`: State whether the result is based on search metadata only or includes deeper repo inspection.

If the user asks for actual verification, move from search to execution: clone the top repositories only after confirming scope and then install, build, run tests, or launch demos as appropriate.

## When To Stop

Stop after producing a decision-ready shortlist unless the user asks to clone or run projects. For most discovery tasks, 5-10 ranked candidates are enough.

## Limitations To State

When relevant, be explicit that:
- Search can miss niche or poorly indexed repositories.
- Public metadata cannot prove a project runs.
- License and security review are initial signals, not legal or security approval.
- Private repositories, package ecosystems, or paid tools may require additional access.
