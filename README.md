# Business Central Release Feed

Public import feed for the **Business Central Release Radar** per-tenant
extension. One file, regenerated from Microsoft's published release notes:

```
releases.json
```

## Using it

Set the URL as **Import Endpoint** on the *Release Radar Setup* page in
Business Central:

```
https://raw.githubusercontent.com/<user>/<repo>/main/releases.json
```

The extension fetches it anonymously over HTTPS, so this repository must be
public. Remember to enable **Allow HttpClient Requests** on the extension under
Extension Management, or the call is blocked before it leaves the tenant.

## Shape

```json
{
  "generated_at": "2026-09-12",
  "features": [
    { "id": "...", "version": "28.0", "area": "Development",
      "title": "...", "enabled_for": "", "general_availability": "",
      "doc_url": "/dynamics365/release-plan/..." }
  ],
  "hotfixes": [
    { "id": "4533389", "version": "15.2", "functional_area": "Hotfixes",
      "title": "...", "doc_url": "https://support.microsoft.com/help/..." }
  ]
}
```

Localized titles appear as `title_da`, `title_nl` and `title_fr`, and Microsoft's
one-line summary as `summary` plus `summary_da`, `summary_nl` and `summary_fr`.

## Change log

`changelog.json` lists what changed between daily builds, newest first, for the
last 365 days:

```json
{
  "generated_at": "2026-09-14",
  "entries": [
    { "id": "3f1c...", "date": "2026-09-14", "change": "renamed",
      "item_type": "feature", "item_id": "...", "version": "28.0",
      "title": "...", "old": "old title", "new": "new title" }
  ]
}
```

`change` is `new`, `renamed`, `date_changed` or `removed` for features; `new`
or `fixes_added` for hotfix updates, where `new` and `old` hold the number of
fixes; and `status_changed` for ideas. Each fix is a row of its own in
`releases.json`, so the change log names the update rather than every fix.
`id` is stable, so importing the same file twice adds nothing.

## Full descriptions

`details/<feature-id>.json` carries Microsoft's complete text — business value
and feature details — in every language that has one:

```json
{
  "id": "0019b39b0136ea13",
  "title": "...",
  "languages": {
    "en": { "title": "...", "summary": "...", "details": "...", "source_url": "..." },
    "da": { "...": "..." }
  }
}
```

These are kept out of `releases.json` on purpose. Together they run to 5.5 MB,
and single descriptions pass 50,000 characters, so the extension fetches one
file at a time for the features someone opens and stores the result in the
tenant.

## What is not here

This repository holds the feed only. The tooling that produces it, the
extension source, and all customer data live in a separate private repository.
Customer selections never leave the Business Central tenant.

## Attribution

Titles, summaries and links are Microsoft's, derived from the public Business
Central release notes and release plans on Microsoft Learn.
