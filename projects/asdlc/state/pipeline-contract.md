# Full-pipeline state contract — proposed, not executable

[Strict structural schema](pipeline-state.schema.json) and [illustrative records](pipeline-state.example.json). These are deliberately separate from project-root state.json and runtime schema version1. No live state is created. The example contains synthetic worker/review records, a material finding, an unanswered question and a pending approval; no stage or artifact is accepted. Its code reference is explicitly synthetic and test execution is planned, never passed. Its schema requires illustrative_only=true; it must never be passed to runtime init/load.

## Authority and identity

Proposed one project-root state envelope after a separately reviewed migration. Canonical collections: stages, runs, artifacts, questions, decisions, findings, reviews, approvals, conditions, RAID, stories, sprints, code versions, evidence, next actions and policies. Artifact ID/version references identify immutable snapshots and typed SHA256; code versions bind repo/commit and optional dirty digest. Collections use unique IDs and every referenced ID/version must exist. Markdown documents are versioned sources or generated views, never competing state copies.

The schema describes record shapes, not executable gates. Semantic validator/scheduler must additionally enforce cross-reference validity, unique IDs, DAG acyclicity, output/source hash recomputation, author/reviewer independence, dispatch identity/revision/digest, evidence result=not_run unless execution=executed, attribution for answered questions/decided decisions, null actor/source for pending approval and actual attribution for decided approval, owner/reason for deferrals, exact prerequisite review/acceptance and condition satisfaction. Proposed policy cannot authorise a transition. These checks and migration are backlog S08–S10, not implemented capabilities.

## Transitions and human decisions

not_started → ready only with available current accepted inputs and authorised scope; ready → running on persisted dispatch; valid worker output → awaiting_review; review finding → changes_requested; missing fact → awaiting_input; exhausted correction → blocked; pass → awaiting_approval when policy requires, otherwise only the permitted next action. Actual exact-version acceptance → accepted, subject to conditions. Source change → stale for affected dependency closure. There is no automatic conversion from pass to human acceptance.

Policy versions specify repair cap, escalation owner and human gate stages. The example's two-repair cap and gate list are proposals. Business BRD approval and sprint acceptance remain explicit requirements; other approval points and conditional advancement need reviewed policy. Count correction attempts once and preserve spent budgets across restart, failed dispatch and unchanged-input retries. Reset only under an explicit scoped policy/action, never to bypass exhaustion.

## Questions, change impact, resume and RAID

Persist question before presenting short rounds; answered needs attributed source. Deferred requires owner, resolution stage and reason; it blocks at that required stage if unresolved. Business gaps found downstream return to their owner; pause affected work.

Build impact from artifact input_refs and story/sprint/evidence dependencies. Changed sources produce explicit affected closure; current acceptance/reviews become stale, historical records remain. Re-review/reaccept exact changed outputs and verify preserved unaffected outputs. No stale accepted artifact may authorise work.

Resume validates schema and semantic invariants, verifies source/code/guidance versions, reconciles pending run/side effects, derives next actions, and regenerates status/RAID. Corruption holds with diagnostics. Transaction protocol remains a reviewable implementation choice; proposed reuse of local lock/revision/atomic state with derived-view recovery has delivered discovery evidence only. Stories/sprints, graph invalidation and distributed writers are not yet supported.

RAID changes have stable ID/kind/source/owner/action/due stage; no worker writes canonical RAID directly. Questions/findings create or update linked records; resolving a question does not erase the history. Views show active owner/exact request, completed evidence, stage readiness and future gates distinctly. Planned/unavailable tests cannot be listed as passes.
