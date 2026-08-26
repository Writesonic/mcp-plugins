---
description: Full teardown of one competitor — every prompt where they're cited and we aren't, topics where they out-rank us, platforms where their lead is biggest, and a plan to overtake them. Use when the user names a competitor and asks how they beat us or how to catch up.
---
Tear down competitor "$ARGUMENTS" for the user's project (resolve the project via `get_all_projects`; confirm the competitor is tracked via `get_all_websites`).

1. `get_prompts_not_mentioning_you` — prompts where we are absent; keep the ones where this competitor appears.
2. `query_performance_report` dimensions=["website", "topic"] website_type="SELF+COMPETITORS" — topics where they out-rank us.
3. `query_performance_report` dimensions=["website", "model"] website_type="SELF+COMPETITORS" — platforms where their lead is biggest.
4. `get_brand_gap_summary` → `get_all_brand_gap_opportunities` — third-party pages citing them but not us (the outreach list).

Finish with a prioritized plan: biggest gap first, one concrete action per gap. Cite the numbers behind each claim.
