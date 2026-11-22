---
okf_version: "0.2"
---

# Wiki Index

This wiki is the documentation of `@genvidtech/cordova-plugin-marketplace`. It lists every page under `wiki/`, grouped under section headings, one line each. Each entry's text is the linked page's frontmatter `description`. The page format and the maintenance rules are in [the schema](schema.md). The change log is [log.md](log.md).

Gvt-dev skills read this page as the documentation index. With no `paths['docs/TOC.md']` override in `.gvt-agent.json`, the index is `<wikiDir>/index.md`, which is this page.

## Project context

These two files are at the repository root, outside the wiki:

- `README.md`: build, package and demo-run instructions, the manual Android install workaround, and the release steps.
- `CLAUDE.md`: architecture overview (the JS bridge and the Android and iOS native layers), commands and conventions.

## Process

* [Issue Triage Conventions](issue-triage.md) - Project conventions that /gvt-dev:triage-issues reads: types, priorities, labels, required fields, splitting, duplicates, dependencies and mutation recipes.

## Schema

* [Wiki Maintenance Schema](schema.md) - The maintenance rules for this wiki: page format, create-vs-update lifecycle, raw/ immutability, staleness policy and the verb contract.
