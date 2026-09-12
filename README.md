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

Localized titles appear as `title_da`, `title_nl` and `title_fr` when the feed
is generated with `--locales`.

## What is not here

This repository holds the feed only. The tooling that produces it, the
extension source, and all customer data live in a separate private repository.
Customer selections never leave the Business Central tenant.

## Attribution

Titles, summaries and links are Microsoft's, derived from the public Business
Central release notes and release plans on Microsoft Learn.
