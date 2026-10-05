---
id: APPROVAL-001
project_id: PROJECT_ID
title: Human approval evidence
status: draft
owner: unassigned
source_versions: []
review_ref: null
approval_ref: null
---

# Human approval evidence

Template: replace placeholders with sourced facts. Empty fields are unknown, never agreement. Record actual dates and exact source hashes when instantiated. This file confers no approval.

## Pending gate

Human actor, actual action, actual date, stage/sprint and scope: **not recorded**. Do not populate these on the user's behalf.

## Exact target and prerequisite evidence

| Artifact/input/code target | Exact version or digest | Independent review | Test evidence |
|---|---|---|---|

## Decision and conditions

Approval / rejection / risk acceptance (only record the actual human decision). Record explicit conditions and their owners. Risk acceptance does not fabricate passing tests or waive engine gates.

## Invalidation

Identify affected inputs/code and approval revocation/review conditions. A changed target invalidates acceptance of that target. Preserve historical approvals as invalidated rather than erasing them.

## Canonical recording

Current runtime approval uses id, actor, artifact_hash, input_hash, date and valid; the orchestrator records it only after a passing independent discovery review. Later code/sprint approval gates are planned. This Markdown template is explanatory evidence, not a fake canonical record.
