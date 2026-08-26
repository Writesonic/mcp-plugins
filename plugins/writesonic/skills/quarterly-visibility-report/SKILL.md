---
description: One-page quarterly visibility summary ready to paste into a deck — overall score and trend, top three topic gainers and losers with a one-line reason each. Use for quarterly reviews, QBRs, or "summarize the quarter".
---
Write a one-page quarterly visibility summary for project "$ARGUMENTS" (resolve via `get_all_projects` if needed). Default to the last completed quarter vs the one before; ask if ambiguous.

1. `get_kpi_summary` with the quarter as current_from/current_to and the prior quarter as previous_from/previous_to — headline numbers with deltas.
2. `query_performance_report` dimensions=["date"] date_aggregation_interval="week" website_type="SELF" — the trend line across the quarter.
3. `query_performance_report` dimensions=["topic"] website_type="SELF" with start_date/end_date = this quarter and comparison_start_date/comparison_end_date = last quarter — each topic row carries previous_* values; rank by change to get the three biggest gainers and the three biggest losers.
4. For each of those six topics, one line on why (use `get_prompts_leaderboard` filtered to the topic if the cause isn't obvious).

Output: headline → trend sentence → gainers table → losers table → one-line reasons. Keep it to one page.
