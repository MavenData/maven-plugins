---
name: maven-analytics
description: Analyze governed marketing, revenue, commerce, CRM, web, SEO, social, email, or retail data from an authorized Maven workspace. Use for metric questions, comparisons, rankings, freshness checks, and evidence-backed performance explanations.
---

# Maven Analytics

Use Maven's governed query tools for customer-specific claims. Never invent a metric, dimension, filter value, date range, or causal explanation.

## Workflow

1. Use `whoami` when authorization or scope is unclear. Use `list_workspaces` when the credential can access more than one workspace.
2. Call `get_workspace_brief` at the start of a new customer analysis to learn connected sources, readiness, and caveats.
3. Call `describe_schema` without a table for the compact index, then call it with the chosen table for full metric, dimension, formula, caveat, predicate, and grain details.
4. Decompose compound questions into focused same-table `query_metrics` calls. Preserve every explicit date, metric, and dimension; do not silently substitute semantics.
5. Call `get_dimension_values` before applying a filter value that has not already been verified.
6. Use `query_metrics` with `compare: { mode: "previous_period" }` (or `"previous_year"`) for explicit change questions and `top_n` for rankings. Use `check_freshness` when recency affects the answer.
7. State the applied period, relevant defaults, source limitations, and material caveats returned by the tools.

Keep analysis in chat unless the user explicitly requests a report, dashboard, presentation, shareable artifact, Site, or visualization. For a live Maven report, use the `maven-report-builder` workflow.
