# Wiki Log

Record of every `ingest` run: what changed, why, and which `raw/` source
drove it, grouped under `## YYYY-MM-DD` date headings (ISO 8601) with the
**newest date group first**. Entries are prose bullets, e.g. `* **Update**:
…`, `* **Creation**: …`, `* **Deprecation**: …` — the leading bold word is a
convention, not a requirement.

**Add newest first, never edit or remove a prior entry.** "Newest first"
means a new entry (and, if today isn't already the top group, a new
`## YYYY-MM-DD` heading) is *prepended* above everything else — the
insertion point moves from the bottom to the top, but prepending never
touches a prior entry's text, so the append-only guarantee holds exactly as
before. If a past entry itself needs correcting, add a new entry that says
so; never edit or remove the old one in place. See [the schema](schema.md) for
the full maintenance schema.

## 2026-11-22

* **Creation**: the wiki, from the project documentation (issue #13). The documentation index moved to `index.md` and was rewritten as a list of wiki pages. The triage conventions moved to `issue-triage.md` with no change to their headings; the `area:docs` label now names the wiki instead of the old folder. Each page got OKF frontmatter. `schema.md` was scaffolded from the gvt-wiki template. No `raw/` capture drove this run: the source is the repository's own history.
