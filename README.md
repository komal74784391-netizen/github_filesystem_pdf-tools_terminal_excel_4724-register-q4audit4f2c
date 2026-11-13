# Research Implementation Register

Internal register maintained by the Programmes Office.  It stores the intake
records for portfolio research works and vendors candidate community
implementations into the hub.

## Layout

- `works/` — quarterly intake batches.  Each batch file contains a `records`
  array; one file can hold records from more than one intake queue.
- `repositories/` — community implementation projects.  Every project has a
  `README.md` and a `meta.json` describing its popularity snapshot.
  Its canonical URL is the project folder URL on the hub.
- `audits/` — quarterly audit submissions.  `audits/_template.json` shows the
  expected shape of an audit document.

## Record fields

- `record_id` — intake handle printed on the batch (a human handle only).
- `work_id` — portfolio-wide work identifier.
- `title`, `identifier`, `authors`, `year`, `abstract` — bibliographic data.
- `program_label` — intake shorthand printed on the batch.
- `program_note` — intake annotation recorded by the analyst who filed it.
- `candidate_watchlist` — implementation projects spotted by the quarterly
  crawler.  Each entry contains `project` (folder name under
  `repositories/`), `popularity` (the quarterly popularity score captured for
  that project), `captured_at` and free-text `notes`.

## Audit conventions

Quarterly audits are written to `audits/<period>.json` following the template.
For each work the audit records either a verified community implementation or
`none`.  `repository_url` must be the canonical folder URL of a project that
implements the exact work; use `null` when no such implementation is verified.
Popularity comparisons use the values captured in `candidate_watchlist` / the
project `meta.json`.
