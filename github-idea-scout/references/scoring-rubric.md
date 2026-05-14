# Scoring Rubric

Use this rubric to rank candidate repositories. Score out of 100 when enough evidence exists. If evidence is limited, provide a qualitative score such as `high`, `medium`, or `low` confidence.

## Weights

| Dimension | Weight | What To Check |
| --- | ---: | --- |
| Requirement fit | 30 | Must-have features, artifact type, workflow match, domain match |
| Maintenance activity | 20 | Recent commits, releases, issue responses, PR activity, archived status |
| Documentation and examples | 15 | README clarity, quickstart, examples, demo, API docs |
| Integration cost | 15 | Setup complexity, dependencies, deployment model, extensibility, framework fit |
| Adoption signal | 10 | Stars, forks, contributors, package downloads, dependent projects, community mentions |
| License and risk | 10 | License clarity, commercial compatibility, security posture, known blockers |

## Scoring Notes

- Do not use stars as a proxy for fit.
- Prefer active, narrowly relevant repositories over popular but generic repositories.
- Penalize unclear setup instructions when the user wants fast validation.
- Penalize missing or incompatible license when the user wants commercial use.
- Penalize abandoned projects even if they are highly starred.
- Reward projects with examples, Docker Compose, hosted demos, sample data, or tests.

## Confidence Labels

Use these labels in addition to scores:

- `High`: Multiple strong evidence sources, recent activity, clear docs, and direct feature match.
- `Medium`: Good match but some uncertainty around maintenance, setup, or missing features.
- `Low`: Looks relevant by keywords, but evidence is thin or stale.

## Risk Flags

Flag these explicitly:

- `Archived`
- `Stale`
- `License unclear`
- `Commercial-use risk`
- `No quickstart`
- `No release history`
- `Demo only`
- `High setup cost`
- `Framework mismatch`
- `Security review needed`
- `Unclear maintainer activity`

## Recommendation Rule

The top recommendation should be the repository with the best combined practical value, not necessarily the highest numerical score. Practical value means the user can plausibly validate or reuse it quickly for their stated goal.
