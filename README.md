# GitHub Idea Scout

A Codex/ChatGPT skill for discovering and ranking existing GitHub repositories from a natural-language product, feature, library, or technical idea.

Instead of relying on one keyword search, this skill guides the agent to expand the idea into multiple search angles, inspect README evidence, evaluate repository health, and produce a practical recommendation.

## What It Does

- Converts a rough idea into concrete repository search requirements.
- Searches with multiple query families instead of one keyword.
- Evaluates candidate repositories by fit, maintenance, documentation, setup cost, adoption, license, and risk.
- Uses token controls so the agent reads broadly first and deeply only for top candidates.
- Produces a scenario-based shortlist with evidence and a validation plan.

## Install

Copy the `github-idea-scout/` folder into your Codex skills directory.

Windows:

```powershell
C:\Users\<you>\.codex\skills\github-idea-scout
```

macOS/Linux:

```bash
~/.codex/skills/github-idea-scout
```

Restart Codex if the skill list does not refresh automatically.

## Example Prompt

```text
Use $github-idea-scout to find existing GitHub projects for a self-hosted AI workflow builder that supports browser automation and visual workflows. Read README evidence, check stars, issues, releases, and maintenance signals, then recommend the best options by fit and validation effort.
```

## Notes

This skill does not claim that a recommended repository runs successfully unless the agent has cloned, installed, built, or tested it. Search-stage recommendations are based on public evidence such as README content, repository metadata, releases, issues, documentation, and visible activity.
