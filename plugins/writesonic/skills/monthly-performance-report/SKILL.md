---
description: Monthly performance summary — visibility, citation and sentiment trends for the brand. Use when the user asks for a monthly report, month-in-review, or performance summary over months.
---
Build the monthly performance summary for project "$ARGUMENTS" (resolve via `get_all_projects` if not given). Cover the last 3 full months unless the user specifies a range.

1. `query_performance_report` dimensions=["date"] date_aggregation_interval="month" website_type="SELF" — visibility_score, share_of_voice, mention_count per month.
2. `query_citation_report` dimensions=["date"] date_aggregation_interval="month" website_type="SELF" — citation count and unique pages per month.
3. `query_sentiment_report` dimensions=["date"] date_aggregation_interval="month" website_type="SELF" — sentiment per month (request `pct_positive`).

Report each layer as its own short table, then a 3-bullet takeaway. Numbers and periods only; declines first.
