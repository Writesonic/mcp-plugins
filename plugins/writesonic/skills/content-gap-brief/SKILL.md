---
description: Find the top content gaps by impact, optionally start tracking the underlying questions, and set up citation monitoring for the pages once published. Use when the user asks what content to create, content opportunities, or content gaps.
---
Find content gaps for project "$ARGUMENTS" (resolve via `get_all_projects` if needed).

1. `get_all_new_content_opportunities` — questions AI answers where we have no page.
2. `get_new_content_impact` — rank the gaps by estimated visibility lift; take the top three unless the user asks for more.
3. For each gap, draft a one-paragraph brief: the question, the platforms answering it, who is cited today, and the angle for our page.
4. Only if the user asks to track them: show the exact prompts you would create, ask for confirmation, then `create_prompt` for each. Never create prompts without an explicit yes.
5. Tell the user that once the pages are live, `get_webpage_citation_trends` with the page URL as the `cited_page_url` filter will show their first AI citations.
