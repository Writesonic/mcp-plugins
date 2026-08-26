---
description: Build the weekly GEO digest — visibility change vs last week, sentiment shift, biggest-moving prompts, top recommended actions. Use when the user asks for a weekly summary, digest, or "what moved this week".
---
Produce the weekly GEO digest for project "$ARGUMENTS" (call `get_all_projects` and ask if none is given). Use the last 7 days vs the 7 before.

1. `get_kpi_summary` with current_from/current_to and previous_from/previous_to — week-over-week visibility and mention deltas.
2. `query_sentiment_report` dimensions=["date"] website_type="SELF" — did sentiment shift?
3. `get_ai_answer_changes` — answers that appeared or disappeared this week (the biggest-moving prompts).
4. `get_actionables_dashboard` — recommended actions ranked by impact; pick the top three.

Format: four short sections in that order. Cite numbers with the period ("fell 3 pp from 41% to 38% WoW"), lead with declines, no hyperbole.
