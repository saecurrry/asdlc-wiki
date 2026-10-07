# Templates for agent work

Use these as small artifact contracts, loading only the current stage and relevant sources. Preserve facts, unknowns, decisions, findings and version bindings across sessions. No template is executed evidence or approval.

## Project documents

Maintain the [living build plan](project/build-plan.md) with scope, increments, evidence, blockers and next permitted action.

Copy [project/](project/index.md) into `projects/<lowercase-hyphenated-id>/` without overwriting an existing project. Replace PROJECT_ID/PROJECT_NAME and assigned owners; record actual dates and sources. Do not copy the legacy state drafts.

| Work | Template | Required gate |
|---|---|---|
| Discovery | [Brief](project/discovery/brief.md) | Questions answered or explicitly unresolved; independent review then human acceptance |
| Business intent | [BRD](project/requirements/brd.md) | Measurable requirements/rules and scope reviewed against approved brief |
| Technical design | [HLD](project/architecture/hld.md) | Standards/patterns, C4, data/integrations/operations and decisions reviewed |
| Delivery planning | [Story](project/backlog/story.md), [sprint plan](project/sprints/sprint-plan.md) | Coverage, dependencies and eligibility reviewed |
| Integrated validation | [Test evidence](project/sprints/test-evidence.md) | Actual code/input versions and executed results |
| Increment acceptance | [Sprint report](project/sprints/sprint-report.md) | Independent evidence review; separate human acceptance |
| Material choice | [Decision](project/decisions/decision.md) | Alternatives/rationale and explicit decision owner |
| Challenge | [Review](project/reviews/review.md) | Fresh reviewer; zero findings is valid |
| Human gate | [Approval](project/approvals/approval.md) | Actual human action bound to exact versions |
| Learning | [Lesson](project/lessons/lesson.md) | Project evidence before shared promotion |

## Machine state and readable views

Follow [runtime contract](project/state/index.md) and [schemas](../schemas/index.md). Canonical state is one project-root state.json created by the tool. Init overwrites the two status/RAID draft views, so archive human drafts first. The runtime currently executes discovery only; later-stage templates do not enable later-stage dispatch. No project is activated by copying the template.

## Shared knowledge

Use [knowledge entry](knowledge-entry.md). Choose kind standard/pattern/knowledge, separate applicability and limits, cite evidence and versions. A standard becomes mandatory only after recorded human owner approval. A pattern or lesson becomes reviewed only after independent challenge. Preserve superseded entries with replacement links.

## Complete example set and hierarchy

[Worked examples](examples/worked-artifacts.md) cover every artifact, including implementation records, unavailable test evidence and pending approval. Use [initiative](project/requirements/initiative.md) and [epic](project/requirements/epic.md) contracts alongside BRD.

[Proposed full-pipeline state](../projects/asdlc/state/pipeline-contract.md) is a design, not today's executable schema.
