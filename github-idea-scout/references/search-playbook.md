# Search Playbook

## Query Families

Generate several query families before searching:

- Direct product terms: words the user used.
- Alternative domain terms: synonyms and adjacent categories.
- Implementation terms: protocols, libraries, APIs, algorithms, file formats, or runtimes likely involved.
- Artifact terms: template, starter, boilerplate, sdk, cli, plugin, self-hosted, dashboard, agent, workflow, examples.
- Ecosystem terms: preferred language, framework, runtime, database, deployment target, package manager.
- Integration terms: third-party APIs or services the project must connect to.
- Quality terms: awesome, alternatives, comparison, open source, reference implementation.

## Useful GitHub Qualifiers

Use these when supported:

```text
stars:>100
stars:>1000
pushed:>2025-01-01
language:TypeScript
language:Python
topic:ai
topic:self-hosted
license:mit
license:apache-2.0
fork:false
archived:false
```

If a tool does not support qualifiers, simplify the query and filter manually.

## Candidate Collection

For each candidate, collect owner/repo, URL, one-line description, features matching the idea, language/framework, artifact type, stars/forks, last push or release date, license, docs/examples/demo availability, and visible concerns.

## Exclusion Filters

Reject or downgrade when archived, stale, license unclear, README lacks quickstart/examples, demo-only, core feature missing, issue tracker suggests main path is broken, or repo is a fork with little independent activity.
