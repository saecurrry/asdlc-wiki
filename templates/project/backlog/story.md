---
id: STORY-001
project_id: PROJECT_ID
title: Delivery story
status: draft
owner: unassigned
source_versions: []
review_ref: null
approval_ref: null
---

# Delivery story

Template: replace placeholders with sourced facts. Empty fields are unknown, never agreement. Record actual dates and exact source hashes when instantiated. This file confers no approval.

## Intent and sources

As <actor>, I need <behaviour> so that <linked outcome>. Replace the proposed wording from approved intent.

Initiative / epic / requirements / approved BRD-HLD versions:

## Scope and acceptance

Include one small verifiable delivery unit; list exclusions and objective acceptance criteria.

```gherkin
Feature: Proposed business behaviour
  Scenario: Replace with a real acceptance example
    Given an approved business precondition
    When the actor performs the operation
    Then the measurable expected behaviour occurs
```

Use Gherkin when it clarifies business behaviour; use objective checks for technical work.

## Dependencies and execution eligibility

| Dependency ID | Required artifact/code version | Ready condition | Status |
|---|---|---|---|

Execution: serial / parallel-eligible (select with reason). Parallel eligibility requires non-overlapping ownership, ready dependencies and an integration plan; first runtime executes serially.

## Tests, evidence and change binding

Planned checks, integrated test coverage, exact code commit plus dirty-tree digest, actual commands/results and relative evidence links.

## Ready/done and review

Ready requires approved inputs and unblocked dependencies. Done requires acceptance evidence, independent code challenge and inclusion in integrated sprint validation. Story completion does not grant sprint human acceptance.

## Shared resource and integration assessment

| File / interface / data resource | Story owner | Other consumers | Compatibility / conflict risk | Isolation method | Integration owner / checks |
|---|---|---|---|---|---|

Parallel eligibility is a reasoned proposal, not dispatch authority. Record approved contracts/ADRs/standards/pattern IDs and versions.

Worked examples: [synthetic artifact set](../../examples/worked-artifacts.md). Examples confer no real execution or acceptance.
