# GitHub Idea Scout

A lightweight Codex skill for discovering and ranking existing GitHub repositories from a natural-language product, feature, library, or technical idea.

This first version is intentionally thin: it does not call the GitHub API or maintain an index. It gives the agent a repeatable workflow for search, evaluation, ranking, risk flagging, and next-step validation.

## What It Does

- Converts a rough idea into concrete repository search requirements.
- Searches with multiple query families instead of one keyword.
- Evaluates candidate repositories by fit, maintenance, documentation, integration cost, adoption, license, and risk.
- Produces a ranked shortlist with evidence and a practical validation plan.
- Clearly separates metadata-level confidence from actually running a project.

## Install

Copy the `github-idea-scout/` folder into your Codex skills directory.

On Windows, that is usually:

```powershell
C:\Users\<you>\.codex\skills\github-idea-scout
```

On macOS or Linux, that is usually:

```bash
~/.codex/skills/github-idea-scout
```

Restart Codex if the skill list does not refresh automatically.

## Example Prompt

```text
Use $github-idea-scout to find existing GitHub projects for a local-first AI meeting notes app. It should support recording, transcription, summarization, action items, and export to Notion. Prefer TypeScript, Electron, Tauri, or Next.js. Rank by fit, maintenance, license risk, and how fast I can validate it.
```

## Notes

This skill does not claim that a recommended repository runs successfully unless the agent has cloned, installed, built, or tested it. Search-stage recommendations are based on public evidence such as README content, repository metadata, releases, issues, documentation, and visible activity.
