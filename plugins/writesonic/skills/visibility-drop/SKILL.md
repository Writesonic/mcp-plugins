---
description: Diagnose a visibility drop — which topics and platforms declined, whether citations were lost or sentiment turned, the exact prompts responsible, and a fix per cause. Use when the user asks why visibility, share of voice, or mentions went down.
---
Diagnose the visibility drop for project "$ARGUMENTS" (resolve via `get_all_projects` if needed). Compare the drop period against the period before it. Do not skip steps or diagnose from the aggregate alone.

1. `query_performance_report` dimensions=["topic", "date"] website_type="SELF" — which topics declined.
2. `query_performance_report` dimensions=["model", "date"] website_type="SELF" — which platforms declined.
3. `query_citation_report` dimensions=["date"] website_type="SELF" — were citations lost?
4. `query_sentiment_report` dimensions=["date"] website_type="SELF" — did sentiment turn?
5. `get_ai_answer_changes` — the exact prompts where answers changed; spot-check 2–3 with `get_prompt_answers`.
6. Check for configuration changes (prompts or competitors added/removed) — these shift denominators and can mimic a real drop.

Report: cause → evidence (numbers + period) → recommended fix, one block per cause. Declines first, no hyperbole.
