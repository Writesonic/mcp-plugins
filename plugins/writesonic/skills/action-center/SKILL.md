---
description: Rank Writesonic's recommended actions by impact and pick the three with the biggest visibility lift for the least effort. Use when the user asks what to do, what to work on, recommendations, or priorities.
---
Prioritize actions for project "$ARGUMENTS" (resolve via `get_all_projects` if needed).

1. `get_actionables_dashboard` FIRST — every recommendation with per-category counts and impact. Do not call the individual category tools before this.
2. For the leading categories, pull estimated lift: `get_brand_gap_impact`, `get_new_content_impact`, `get_broken_pages_impact`.
3. Rank by lift ÷ effort (broken-page fixes are cheapest, new content is most expensive) and name the three to do first, each with the number behind it.
