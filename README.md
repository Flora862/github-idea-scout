# GitHub Idea Scout

A Codex/ChatGPT skill for discovering and ranking existing GitHub repositories from a natural-language product, feature, library, or technical idea.

Instead of relying on one keyword search, this skill guides the agent to expand the idea into multiple search angles, inspect README evidence, evaluate repository health, and produce a practical recommendation.

## What It Does

- Converts a rough idea into concrete repository search requirements.
- Searches with multiple query families instead of one keyword.
- Evaluates candidate repositories by fit, maintenance, documentation, setup cost, adoption, license, and risk.
- Uses token controls so the agent reads broadly first and deeply only for top candidates.
- Produces a scenario-based shortlist with evidence and a validation plan.

## GitHub Access

This repository is a skill, not a running MCP server.

The skill can use any GitHub access method available in the host app:

- Codex GitHub connector or plugin
- GitHub MCP server
- GitHub CLI (`gh`)
- Web search or public GitHub pages as a fallback

You do not need to configure GitHub MCP just to use this skill in Codex if Codex already has a working GitHub connector/plugin. MCP is only one optional tool channel for repository search, README inspection, issue/PR checks, and metadata collection.

## Install

Copy the inner `github-idea-scout/` skill folder from this repository into your Codex skills directory. Do not copy the whole repository folder as an extra nesting level.

Correct Windows destination:

```powershell
C:\Users\<you>\.codex\skills\github-idea-scout\SKILL.md
```

Correct macOS/Linux destination:

```bash
~/.codex/skills/github-idea-scout/SKILL.md
```

If you clone the repository first, copy this folder:

```text
github-idea-scout/github-idea-scout/
```

into:

```text
~/.codex/skills/github-idea-scout/
```

Restart Codex if the skill list does not refresh automatically.

## Example Prompt

```text
Use $github-idea-scout to find existing GitHub projects for a self-hosted AI workflow builder that supports browser automation and visual workflows. Read README evidence, check stars, issues, releases, and maintenance signals, then recommend the best options by fit and validation effort.
```

## Notes

This skill does not claim that a recommended repository runs successfully unless the agent has cloned, installed, built, or tested it. Search-stage recommendations are based on public evidence such as README content, repository metadata, releases, issues, documentation, and visible activity.
