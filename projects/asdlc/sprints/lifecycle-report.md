# Serial lifecycle orchestrator increment — review package

Status: accepted by the user on 6 October 2026; independent code review passed. [Exact acceptance](../approvals/lifecycle-approval.md). Source: user clarification that the orchestrator manages stages, gates, handoffs, progress and continuation.

## Delivered behaviour

- New project init defaults to schema v2 and refuses populated human project folders. Existing v1 discovery remains unchanged; no silent migration.
- Seven ordered stages use specialist and independent challenger dispatches. Serial run-stage manages outputs/review/corrections and pauses at input, exact approval or escalation.
- Human approval records an exact current artifact/input version and saves its next-stage handoff atomically. approve --run-next drives the next stage to its next human gate. No automatic human acceptance.
- Exact-target rejection records actual human reason and returns the owner to correction. Retry cap is configurable at init and bound into the input digest.
- Approved sprint can use next-sprint to return to planning with accepted business/HLD inputs. Prior sprint acceptance remains history, not authorisation of new scope.
- Current artifacts and immutable content versions are materialised in established wiki stage folders; status contains stage/gate/artifact/action table. Restart restores records and regenerates views.
- Shared source changes conservatively invalidate the dependent lifecycle; application code commit plus tracked/staged/untracked dirty digest binds development/test/sprint submissions. Later code drift returns to development and retires affected downstream authority.
- Generated question IDs are scoped to stage and generation; tampered immutable content and stale/forged results/approvals are refused.

## Validation and independent challenge

[Executed checks and exact source manifest](evidence/lifecycle-test-run.json): 37-test full suite passed; final strict wire-schema/prompt check also passed. Tests cover seven approval pauses/handoffs, process restart mid-cycle, next sprint, rejected/stale approvals, source/code invalidation, questions, retry cap and human file preservation. Explicitly synthetic specialist/reviewer/human fixtures; no real application or full Codex lifecycle delivery claim.

Independent review found four initial material integrity gaps and a further rejection/correction-state gap. Repairs scope question IDs, validate materialised bytes, bind retry policy, add actual-code provenance/invalidation and persist rejection through question rounds until fresh review passes. [Code review](../reviews/pipeline-code-review.md) records initial and final exact versions.

## Limits and outstanding work

Built-in Codex adapter remains read-only; separately scoped application-writing and real integrated-test workers are not delivered here. Composite stage artifact splitting into standalone initiatives/epics/stories, content-quality sufficiency validation beyond challenge and legacy-state migration remain outstanding. This is lifecycle-control delivery, not a claim of full project-ready application execution or distribution. No live wiki state, Git publication, deployment or new credentials were created.

## Human acceptance recorded

The user accepted this increment on 6 October 2026. [Approval record](../approvals/lifecycle-approval.md) binds the exact originally presented report, executed evidence and independent review. This is an accepted presentation; the original report bytes are retained. Missing capabilities are not treated as delivered.
