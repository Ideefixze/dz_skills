---
name: dz-web-search
description: Skill for searching the internet with ketch. Use when a task needs external sources: web pages, opinions, OSS code, library docs, or the content of a URL. Not for local codebase lookups.
---

# dz-web-search

Internet research goes through [ketch](https://github.com/1broseidon/ketch), a stateless CLI to search and access the Internet.

## When to use

Use whenever the answer lives outside the repo:

- "research X", "what are people saying about Y", "is X worth using",
- a library's own docs or a concrete API example,
- the content of a URL you already hold,
- proofs for a dz-analyze hypothesis.

Do not use for local codebase search. Read the files.

## Check first

```sh
ketch --version        # installed?
ketch config           # active backends and settings as JSON
```

Missing ketch: `brew install ketch`, `npm i -g ketch-cli`, or `go install github.com/1broseidon/ketch@latest`. Propose the command, wait for confirmation. Never mutate config (`ketch config set`) unless the user asks.

## Surfaces

Pick the cheapest surface that answers the question. First match wins.

| Need | Command |
| --- | --- |
| Current pages, news, opinions, comparisons | `ketch search "query"` |
| Full content from search hits in one call | `ketch search "query" --scrape` |
| How real projects call an API | `ketch code "symbol" --lang go` |
| A library's docs, version-aware | `ketch docs "query" --library /org/repo` |
| Content of a known URL | `ketch scrape <url>` |
| Many pages from one site | `ketch crawl <url>` |
| What you already found in this project | `ketch tag show <name>` |

`search` finds URLs. `scrape` reads one. `crawl` reads a site. `code` greps public OSS. `docs` returns curated library snippets. `tag` is a bookmark index, not a search surface.

## Basics

```sh
ketch search "golang error handling" --json
ketch search "golang error handling" --scrape --max-chars 6000 --trim
ketch scrape https://go.dev/doc/effective_go --max-chars 6000 --trim
ketch code "http.NewRequestWithContext" --lang go --limit 3
ketch docs "react useEffect" --library /facebook/react
ketch tag show my-research
```

Every command takes `--json`. The CLI defaults to `auto`, a fallback chain over keyless providers, so search works with no key. Set a key only for higher limits or a specific provider.

## Rules

1. Bound every fetch. Use `--max-chars 4000` to `8000` with `--trim` on any page you have not seen. An uncapped page can cost around 25k tokens. Skip the cap only with a stated reason.
2. Cite every claim with its source URL. A synthesis without links is not a deliverable.
3. Exit codes are control flow. `2` bad input, `3` not found, `4` upstream failure, `5` missing precondition, `6` cancelled. Never retry `2` or `3` unchanged. On `4`, retry once with another backend from `available_backends`. On `5`, propose setup.
4. Tag what matters across sessions. Pass `--tag <project>` on sources you will reuse, then `ketch tag show <project>` instead of re-running the search.
5. Never re-find a URL you already hold. Scrape it.
6. The binary outranks any table here. Trust `ketch --help` and `ketch config` when they disagree.
