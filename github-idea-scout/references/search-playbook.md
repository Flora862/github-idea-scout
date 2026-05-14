# Search Playbook

Use this reference when turning a rough idea into repository search queries.

## Query Families

Generate several query families before searching:

- Direct product terms: words the user used to describe the thing.
- Alternative domain terms: synonyms and adjacent categories.
- Implementation terms: protocols, libraries, APIs, file formats, or algorithms likely used.
- Artifact terms: `template`, `starter`, `boilerplate`, `sdk`, `cli`, `plugin`, `self-hosted`, `dashboard`, `agent`, `workflow`.
- Ecosystem terms: preferred language, framework, runtime, database, deployment target, package manager.
- Integration terms: third-party services or APIs the project must connect to.
- Quality terms: `awesome`, `best`, `alternatives`, `open source`, `examples`, `reference implementation`.

## GitHub Search Qualifiers

Use qualifiers when they fit the user's constraints:

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

Not every search surface supports every qualifier. If a qualifier fails, simplify the query and filter manually.

## Search Strategy

Start broad, then narrow:

1. Search the user's exact idea.
2. Search synonyms and adjacent product categories.
3. Search implementation terms without product wording.
4. Search package names and examples.
5. Search `awesome` lists and comparison pages to discover names.
6. Search each promising repository name with `GitHub`, `issues`, `license`, and `alternative`.

## Candidate Collection

For each candidate, collect:

- `owner/repo`
- URL
- one-line description
- core features matching the idea
- main language and framework
- artifact type: library, app, template, CLI, service, plugin, demo, or reference implementation
- stars and forks
- last push or release date
- license
- docs/examples/demo availability
- visible concerns

## Exclusion Filters

Reject or downgrade repositories when:

- archived
- no meaningful update in 12+ months, unless the domain is stable
- license is missing or incompatible with the user's stated use
- README has no quickstart or examples
- project is only a toy demo but the user needs production use
- core feature is missing despite matching keywords
- issue tracker suggests the main path is broken
- repo is a fork with little independent activity

## Search Completeness

Do not imply the search is exhaustive. Say what surfaces were checked and what could still be missing.
