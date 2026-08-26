---
description: Share of voice vs competitors, optionally on one AI platform and over N days (e.g. "/writesonic:sov ChatGPT 30").
disable-model-invocation: true
---
Arguments "$ARGUMENTS" may contain a platform name and/or a number of days (default: all platforms, last 30 days). Resolve the project via `get_all_projects` if needed, then call `query_performance_report` with dimensions=["website"], website_type="SELF+COMPETITORS", measures=["share_of_voice","visibility_score"], the date range, and a filters.platform "is" condition if a platform was named. Rank websites by share_of_voice and state our rank and the gap to #1.
