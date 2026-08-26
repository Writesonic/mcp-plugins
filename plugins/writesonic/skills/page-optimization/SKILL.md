---
description: Prioritized list of changes to make a specific page easier for AI to cite, with rationale, and how to verify the lift afterwards. Use when the user gives a page URL and asks how to win more AI citations for it.
---
Optimize the page "$ARGUMENTS" (a URL; ask for one if missing) in the user's project (resolve via `get_all_projects`).

1. `get_all_optimization_opportunities` — find the page and its detected issues. If it isn't listed, say so and suggest `track_pages` first.
2. `get_optimization_fixes` for that page — concrete fixes with rationale.
3. Present the fixes in priority order: what to change, why AI cites pages that do this, expected effect.
4. Close with the verification step: after publishing, `get_webpage_citation_trends` filtered by `cited_page_url` to confirm the citation lift.
