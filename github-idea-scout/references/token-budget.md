# Token Budget

Use layered reading to control cost.

## Default Limits

1. Metadata scan: up to 30 repos.
2. README skim: top 8-10 repos.
3. README deep read: top 3-5 repos.
4. Issues: newest 10-20 relevant issues for top 3-5 repos.
5. PRs: newest 5-10 relevant PRs for top 3 repos when needed.
6. Releases: newest 3-5 releases for top 3-5 repos.
7. Code files: avoid unless the user requests code-level verification or README evidence is contradictory.

## Expansion Rules

Expand only when the candidate is plausibly top-tier or evidence conflicts. Stop reading weak candidates early. Spend tokens on distinguishing the top candidates.

## Confidence Labels

- metadata-level: repo metadata only
- README-level: README/docs inspected
- issue-level: issues/PRs/releases inspected
- execution-level: cloned, installed, built, tested, or run
