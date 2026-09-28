# Intune docs mirror

The Intune and Windows Autopilot pages on Microsoft Learn, as Markdown, one
file per page at the path of the source file Learn built it from. It stands in
for `MicrosoftDocs/memdocs` now that the repository is no longer public: every
commit here is a crawl that found something new on Learn, so the history of
this repository is the history of the published docs.

- `learn-mirror.config.json` picks the sitemaps and pages to mirror.
- `.learn-mirror/state.json` records each page's ETag and the publish metadata
  stripped from its front matter (`updated_at`, `git_commit_id`), so a run only
  downloads pages that changed and a republish is not a diff.
- `.github/workflows/mirror-learn.yml` runs [learn-mirror](https://github.com/merill/learn-mirror)
  four times a day and commits what changed.

Content is © Microsoft, published on Microsoft Learn under
[CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).
