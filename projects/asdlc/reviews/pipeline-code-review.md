---
id: REVIEW-PIPELINE-CODE-001
project_id: asdlc
title: Seven-stage orchestration independent code review
status: passed
reviewer: independent-implementation-challenger
review_date: 2026-10-06
human_approval: not-granted
---

# Independent seven-stage orchestration code review

**Current independent verdict: pass for the second-correction final manifest below.** All P1–P4 reproductions are resolved for this scoped serial orchestration increment. Human acceptance is not granted. The initial review and its hashes are retained below as history.

Initial verdict: **changes required** for the initial versions below. Four meaningful findings below. The reviewer changed no runtime, state, template or approval file. Human approval is distinct from this review. Current harness execution remains read-only; this review does not claim autonomous coding or executed integrated testing.

## Executed checks

`.venv/Scripts/python.exe -m unittest discover -s tests -v` passed all **27** tests. The reviewer independently inspected pipeline ordering, snapshot schema, handoff/input integrity, source invalidation, resource refresh, renderer preservation, approval and adapter dispatch. Additional disposable fixture probes reproduced the findings below; no live project was initialised. Existing tests exercise seven serial human gates, wrong-hash rejection, restart, normal input invalidation/archive, forged upstream approval rejection, pending-dispatch failure recovery, correct stage prompt context, human-file init preservation and legacy v1 behaviour.

## Findings

### P1 — Generated question RAID identities collide across stages

Severity: medium. Blocking: yes. Owner: orchestrator record identity. Disposition: open.

Evidence: discovery inserted Q1 and an explicit answer, then advanced through worker/pass/human acceptance to BRD. BRD inserted a new blocking Q1. Canonical RAID then contained two `question:Q1` rows with different business questions and closed/open statuses. Answering the BRD Q1 closed both rows. `clear_current` intentionally empties stage questions while cumulative RAID persists; `question_raid` prefixes only the question ID. Neither schema nor semantic load integrity rejects these duplicate IDs.

Impact/criterion: stable identities and independently persisted history become ambiguous in ordinary stage-local question numbering; downstream operations cannot address a unique dependency. Requested resolution: namespace generated question records by stage/run or another canonical stage-instance ID, and close only the current question's dependency. Enforce uniqueness of canonical collections and cover repeated IDs across stages and invalidation/restart.

### P2 — Existing hash-named artifact content is trusted without verification

Severity: medium. Blocking: yes. Owner: renderer/content materialisation. Disposition: open.

Evidence: after discovery worker submission, the probe replaced `discovery/brief-<canonical-content-hash>.md` with `DIFFERENT UNREVIEWED CONTENT`. Resume left that content untouched and continued to publish the original hash/link from the generated working view. Store.views writes a versioned file only when absent and never compares an existing file with the canonical snapshot.

Impact/criterion: an exact-version human or reviewer link can serve content different from the version named and approved in canonical state. Obsidian edits to generated artifacts need no malicious actor to trigger this. Requested resolution: verify existing versioned content against the expected canonical materialisation, then refuse corruption or explicitly regenerate the owned view according to a documented recovery rule. Preserve human source files and test modified versioned files. The runtime content digest is canonical JSON SHA-256, so compare canonical content/materialisation semantics correctly rather than assuming the digest is a raw Markdown file-byte hash.

### P3 — Retry policy is not version-bound to stage inputs and gates

Severity: medium. Blocking: yes. Owner: policy/orchestrator contract. Disposition: open.

Evidence: v2 state exposes only repair_limit, with no policy revision/identity. Changing the limit from 2 to 99 and saving schema-valid state succeeded with the same input_hash. input_digest covers stage, inputs and questions but excludes the effective retry policy. Dispatches, worker context and human approvals carry no policy revision. Prompts still prescribe two corrections even when code uses a different configured value.

Impact/criterion: current instructions explicitly require a reviewed versioned retry/escalation policy for extensions; the same apparent stage input version can use different correction/exhaustion rules. Requested resolution: persist a concrete policy identifier/version and effective configuration, bind its digest to dispatch/review/approval inputs, supply the selected policy to agents and use an explicit orchestrator operation for changing it with impact invalidation. The review does not decide an unagreed business policy on the user's behalf.

### P4 — Later delivery approvals do not bind actual target code versions

Severity: high. Blocking: yes. Owner: development/testing source resolver and gates. Disposition: open.

Evidence: a fresh disposable target Git repository with app.py version 1 proceeded using explicit synthetic results and synthetic human acceptance through development to testing awaiting_approval. The probe changed app.py to version 2 after the testing review pass. Approving the old testing artifact still advanced to `sprint-review, running`. Canonical inputs contain no code commit/dirty-tree digest, stage-result accepts Markdown only, and Store refresh checks standards/patterns rather than target code. The probe proves stale-code acceptance, not actual test execution.

Impact/criterion: externally performed development/testing can be accepted against a different increment than the independently reviewed/tested one. Required exact-code evidence and downstream invalidation are not enforced by prompts or generic artifact hashes. Requested resolution: require verified code-version refs and structured executed-evidence provenance for delivery stages, snapshot/fingerprint the approved target increment and invalidate affected code review/test/sprint evidence when it changes. If that functionality is outside this increment, deterministically hold development/testing/sprint acceptance as unimplemented/design-only rather than treating generic Markdown as a live delivery gate. This finding does not require the Codex adapter to write code autonomously.

## Review boundaries and disposition

The serial ordering and human/artifact gate mechanics pass their current tests, but those checks do not resolve the four gaps. A new sprint/start-next-sprint command is also not implemented; the accepted sprint stops explicitly. No migration or live ASDLC project activation was demonstrated by this review. Fixes return to the owning implementation agent for independent delta review. No approval, policy consent, publication or deployment is inferred.

## Exact target manifest

SHA-256 of complete reviewed file bytes including line endings. These hashes are historical review targets, not human acceptance. Changed files require new independent review.

| Target in tool repository | SHA-256 |
|---|---|
| asdlc/__init__.py | `0ad0a9cdcefe9c7b3f786bdbaa5f56ed1e80724cf8fb4be5bc686984307831c2` |
| asdlc/__main__.py | `cf7390a2508a0fcad4777a4a629fc5212ab655cb45845975995f835676a834e3` |
| asdlc/adapters.py | `77f8752951c9527febfe508ff37dd5a3a88b2fe351ec9adbed317e1231962b56` |
| asdlc/cli.py | `3510d01e5688c3182df84ac3d0a3e1031e6085075b433bafd1a004b294636110` |
| asdlc/engine.py | `597091d06b43df14ea4e9292a4969b4cf0d82fb1c0455c937c1def204b807ef4` |
| asdlc/pipeline.py | `7b645165f7cd63f354ae4958a9b920bf31adc96389ad98a1c229807083ef4183` |
| asdlc/schemas/approvals.json | `0189178663c1112eef78f471aee9201befecb7ca5b869f1c1d0c98ef97200a99` |
| asdlc/schemas/decisions.json | `a8cc4c19b4d8258c117eeb1f7f40b6cf1dfa0aa8559d440a40de094c14ea5790` |
| asdlc/schemas/pipeline-state.json | `19fe523cf67aa043d484d77c1933043010e6bafaf4e0679fb39aee21b9c292fd` |
| asdlc/schemas/project-state.json | `86f350f0d4c8086c979152ae2b7d3efbbbddfad89d820272d08ccd8200d116f4` |
| asdlc/schemas/questions.json | `81fc57f18dbb511a9ea670082055a12b4720419bef0827388a2e5c6ceedb9e2b` |
| asdlc/schemas/raid.json | `2c32add575283dfc6d3bf0a296c18bacca2c8282bae6b01d8834558673ea8811` |
| asdlc/schemas/review-findings.json | `72db003171d5bf34d36ff60530067fd04615e69a55cad6acb87b22d2d1e3d8be` |
| asdlc/schemas/stage-result.json | `b3b016f97f65fbce8568e7fefde9f2a1bad605b24d7c1859347c74e34a1b1d87` |
| asdlc/store.py | `6cfe00a0f0fb561e70c244f541a6e0d01dc61084f956deadaa870b43804c9e67` |
| prompts/architecture.md | `14878481ace41b4ed6c5ef417239592af270253bd7ae6ffd3fb9bf4dee3fab5e` |
| prompts/business-requirements.md | `c6c5dfd8362cc253e5b08d685bfe4fa61ec1e815dfd14614f73e9c46b1aeb5f3` |
| prompts/challenger.md | `80a0b0de8abcc1efc692440221316cd4402e545f0789413611692ee9f3696aad` |
| prompts/development.md | `e5c359a261ccf521266781270fd10654496913c679c8f04d10b447141a834812` |
| prompts/discovery.md | `23968a8e2efcfcb0a5db5271ff4f9f3f26bb9e0e07cf96594f829da27e2d6bad` |
| prompts/orchestrator.md | `76b88d661651ffa6d837fd49bf5cad02aa3ee98e9f7abf0923ec3aef8868f8ca` |
| prompts/sprint-planning.md | `2b94d5b74257ca308a05fa96dbf01cb1541fd0d20e09c213a6576db0ec3295cf` |
| prompts/sprint-review.md | `0e1f5e6baa3e6f17f76f2463a973a362072511a83267a646320551ed607a6972` |
| prompts/testing.md | `74e889de9d77fbd0da9676f3c22f5786ac0eab04e559e70e51b1e12a603a1e0a` |
| schemas/approvals.json | `0189178663c1112eef78f471aee9201befecb7ca5b869f1c1d0c98ef97200a99` |
| schemas/decisions.json | `a8cc4c19b4d8258c117eeb1f7f40b6cf1dfa0aa8559d440a40de094c14ea5790` |
| schemas/pipeline-state.json | `19fe523cf67aa043d484d77c1933043010e6bafaf4e0679fb39aee21b9c292fd` |
| schemas/project-state.json | `86f350f0d4c8086c979152ae2b7d3efbbbddfad89d820272d08ccd8200d116f4` |
| schemas/questions.json | `81fc57f18dbb511a9ea670082055a12b4720419bef0827388a2e5c6ceedb9e2b` |
| schemas/raid.json | `2c32add575283dfc6d3bf0a296c18bacca2c8282bae6b01d8834558673ea8811` |
| schemas/review-findings.json | `72db003171d5bf34d36ff60530067fd04615e69a55cad6acb87b22d2d1e3d8be` |
| schemas/stage-result.json | `b3b016f97f65fbce8568e7fefde9f2a1bad605b24d7c1859347c74e34a1b1d87` |
| tests/test_pipeline.py | `681b82cefc6532485303a10a1ebc7e0e9d71bc3e259a6bdb1031d213e2f1cf42` |
| tests/test_workflow.py | `1bc390a1d4376207f3d44faf740d82e15460b1db66e3555aa017e97dfe8f96aa` |

## Independent correction-round re-review — 6 October 2026

Review ID: REVIEW-PIPELINE-CODE-002. Verdict: **pass** for the final exact versions below. Meaningful new findings: **none**. The reviewer reran all original failure cases and inspected the code-version and next-sprint additions. The initial report is also preserved as [initial review](pipeline-code-review-initial.md). No source fixes were made by this reviewer.

| Finding | Final disposition | Independent evidence |
|---|---|---|
| P1 | Resolved | Stage/history-epoch question RAID namespaces keep discovery Q1 and BRD Q1 distinct. The original duplicate-ID probe now finds two unique records, and explicit answer closes only the current dependency. Canonical v2 RAID duplicates are refused. |
| P2 | Resolved | The original edited hash-named brief now stops load/resume with a versioned-artifact integrity error. The check covers historical/current artifact snapshots and does not overwrite the human edit. |
| P3 | Resolved for this conservative implementation policy | Effective repair_limit is included in the stage input digest; the original 2→99 mutation without rebinding is refused. Exact implementation file versions below and configured cap define this reviewed serial policy, and zero-cap exhaustion holds. This does not agree a broader conditional/delegated gate policy or infer business consent to a specific cap. |
| P4 | Resolved for external-stage orchestration | Delivery results require actual code-version metadata. The original change to app.py after testing pass now refuses stale approval, archives affected evidence, returns to development and retains the four valid upstream approvals. Current delivery artifact/review result metadata must match the canonical code version, and testing/report inputs match accepted development code. |

All **35 tests passed** with `.venv/Scripts/python.exe -m unittest discover -s tests -v` after the final next-sprint change. Additional independent probes used fresh disposable Git targets and wiki fixtures, reran original P1–P4 cases, and traversed two synthetic sprints: first seven human stage acceptances, then explicit next-sprint with four new scoped acceptances. Resume preserved all eleven historical accepted snapshots while current gate authority remained limited to the new cycle. The normal test suite separately verifies process restart, source/resource invalidation, wrong version/identity rejection, question pause and repair exhaustion, corruption refusal, immutable file preservation and legacy v1 behaviour.

The reviewer inspected `approve --run-next`: it records the explicit approval first and optionally drives the next specialist/reviewer only to its next human pause. It does not create downstream approval. Explicit next-sprint is allowed only after final exact human acceptance and carries three business/HLD inputs into a new planning gate; previous sprint planning/delivery/test/report history remains durable but grants no new scope authority. The code-version capture covers Git commit, tracked/staged diffs and untracked file bytes; ignored files and the external execution environment remain outside this Git source fingerprint.

## Final scope boundary

This pass concerns deterministic orchestration and version binding for structured results of externally executed stages. The installed Codex adapter remains read-only. Synthetic results and metadata do not prove a real worker edited application code, executed appropriate tests or produced sufficient evidence; an independent stage challenger and human gate must assess actual evidence. The runtime has not demonstrated an autonomous coding/test runner in this review. Advanced condition/delegation policy, per-story scheduler and automatic publication are outside this pass. No live project activation, human acceptance, push, merge or deploy occurred.

## Final exact target manifest

SHA-256 of complete final file bytes including line endings. This supersedes the initial manifest for current agent review only; any later target change requires independent delta review.

| Target in tool repository | SHA-256 |
|---|---|
| asdlc/__init__.py | `0ad0a9cdcefe9c7b3f786bdbaa5f56ed1e80724cf8fb4be5bc686984307831c2` |
| asdlc/__main__.py | `cf7390a2508a0fcad4777a4a629fc5212ab655cb45845975995f835676a834e3` |
| asdlc/adapters.py | `82c5fae7882701b901a6107636da97d3fde50f3c90388902f3f65fce0af370b0` |
| asdlc/cli.py | `a63d6aa33ba5fd141304b87b09712710aacb22d0fe48b771b387439849ce89b6` |
| asdlc/code_version.py | `a17ef1a21f32247f12b12e9fade2c333cd318c8e27bde98e1521bfe8f8c76734` |
| asdlc/engine.py | `648b6627561e1e25612845ac6ce5a9dd7a5e3c3e9ed234780b3d667f2680ddf5` |
| asdlc/pipeline.py | `d52e25039dfac8c01c4b793d3b140ae002e946d5ba30ab8cd0e63d6e4ddb287d` |
| asdlc/schemas/approvals.json | `0189178663c1112eef78f471aee9201befecb7ca5b869f1c1d0c98ef97200a99` |
| asdlc/schemas/decisions.json | `a8cc4c19b4d8258c117eeb1f7f40b6cf1dfa0aa8559d440a40de094c14ea5790` |
| asdlc/schemas/pipeline-state.json | `73c372d95c3450867dfd4b61067073577077403f922f35663f93ee1ffdf95bf8` |
| asdlc/schemas/project-state.json | `29dc570a5c85e17ba075f15536bea871734b397da22b1f6f14044f61df533be7` |
| asdlc/schemas/questions.json | `81fc57f18dbb511a9ea670082055a12b4720419bef0827388a2e5c6ceedb9e2b` |
| asdlc/schemas/raid.json | `2c32add575283dfc6d3bf0a296c18bacca2c8282bae6b01d8834558673ea8811` |
| asdlc/schemas/review-findings.json | `72db003171d5bf34d36ff60530067fd04615e69a55cad6acb87b22d2d1e3d8be` |
| asdlc/schemas/stage-result.json | `1ddadb582e1822939f6e8231356a63dd6fcafded3a6750311a74eea6f54133f9` |
| asdlc/store.py | `392d2c68a4a5a85a93368abd4a4c75e3287a7960068872420e61e4d016fde1a5` |
| prompts/architecture.md | `14878481ace41b4ed6c5ef417239592af270253bd7ae6ffd3fb9bf4dee3fab5e` |
| prompts/business-requirements.md | `c6c5dfd8362cc253e5b08d685bfe4fa61ec1e815dfd14614f73e9c46b1aeb5f3` |
| prompts/challenger.md | `80a0b0de8abcc1efc692440221316cd4402e545f0789413611692ee9f3696aad` |
| prompts/development.md | `e5c359a261ccf521266781270fd10654496913c679c8f04d10b447141a834812` |
| prompts/discovery.md | `23968a8e2efcfcb0a5db5271ff4f9f3f26bb9e0e07cf96594f829da27e2d6bad` |
| prompts/orchestrator.md | `76b88d661651ffa6d837fd49bf5cad02aa3ee98e9f7abf0923ec3aef8868f8ca` |
| prompts/sprint-planning.md | `2b94d5b74257ca308a05fa96dbf01cb1541fd0d20e09c213a6576db0ec3295cf` |
| prompts/sprint-review.md | `0e1f5e6baa3e6f17f76f2463a973a362072511a83267a646320551ed607a6972` |
| prompts/testing.md | `74e889de9d77fbd0da9676f3c22f5786ac0eab04e559e70e51b1e12a603a1e0a` |
| schemas/approvals.json | `0189178663c1112eef78f471aee9201befecb7ca5b869f1c1d0c98ef97200a99` |
| schemas/decisions.json | `a8cc4c19b4d8258c117eeb1f7f40b6cf1dfa0aa8559d440a40de094c14ea5790` |
| schemas/pipeline-state.json | `73c372d95c3450867dfd4b61067073577077403f922f35663f93ee1ffdf95bf8` |
| schemas/project-state.json | `29dc570a5c85e17ba075f15536bea871734b397da22b1f6f14044f61df533be7` |
| schemas/questions.json | `81fc57f18dbb511a9ea670082055a12b4720419bef0827388a2e5c6ceedb9e2b` |
| schemas/raid.json | `2c32add575283dfc6d3bf0a296c18bacca2c8282bae6b01d8834558673ea8811` |
| schemas/review-findings.json | `72db003171d5bf34d36ff60530067fd04615e69a55cad6acb87b22d2d1e3d8be` |
| schemas/stage-result.json | `1ddadb582e1822939f6e8231356a63dd6fcafded3a6750311a74eea6f54133f9` |
| tests/test_pipeline.py | `96d0ad80a8e27ecda12fdddfd464b57607d4fa1002bd215c03fb098664faaf0e` |
| tests/test_workflow.py | `1bc390a1d4376207f3d44faf740d82e15460b1db66e3555aa017e97dfe8f96aa` |
| tools/generate_contracts.py | `4fba26419844c7c7314a4e3cdc9d60f220d1a43f4b791494794b4ddd7a3f4efa` |

## Late rejection delta finding — P5

Review ID: REVIEW-PIPELINE-CODE-003. Verdict: **changes required** for the new reject operation. P1–P4 remain resolved at their reviewed versions; this finding is new and does not invalidate the executed evidence for their repairs.

Severity: high. Blocking: yes. Owner: rejection/correction gate. Disposition: open.

Independent evidence: reviewed-pass → explicit human reject → correction worker with a fresh unanswered nonblocking question. The probe repeated four worker submissions, each producing `status=running, repairs=1`. Rejection sets changes_requested but leaves the last independent review verdict as pass; question invalidation derives pending correction solely from that review and restores unrestricted running. Subsequent workers therefore do not consume the repair budget and the human rejection no longer constrains the workflow correctly.

Requested resolution: preserve pending human rejection/correction authority across question/answer invalidation until a fresh review/decision satisfies the correction path. Questions must not erase the correction status or budget. Add reject-plus-question regression through exhaustion, including restart. No human consent or rejection resolution should be invented. The owning agent is correcting this finding; pass is withheld for the rejection delta.

### Rejection delta exact versions

| Target | SHA-256 |
|---|---|
| asdlc/engine.py | `648b6627561e1e25612845ac6ce5a9dd7a5e3c3e9ed234780b3d667f2680ddf5` |
| asdlc/cli.py | `a63d6aa33ba5fd141304b87b09712710aacb22d0fe48b771b387439849ce89b6` |
| asdlc/adapters.py | `82c5fae7882701b901a6107636da97d3fde50f3c90388902f3f65fce0af370b0` |
| tests/test_pipeline.py | `96d0ad80a8e27ecda12fdddfd464b57607d4fa1002bd215c03fb098664faaf0e` |

## Second correction round: final P5 resolution

Review ID: REVIEW-PIPELINE-CODE-004. Date: 6 October 2026. **Final verdict: pass** for the exact versions below. P1–P4 remain resolved; **P5 is resolved**. New meaningful findings: none. Earlier findings and manifests above are preserved as historical evidence; this section supersedes their open disposition for current review.

The reviewer inspected persistent human_changes_pending state, rejection setting, correction invalidation, independent-pass clearing, approval integrity, stage/reset clearing and both schema versions. Independent reproduction restarted Store/Engine before every correction: first optional-question worker returned `changes_requested, repairs=1, pending=true`; second returned `blocked, repairs=2, pending=true`; a further worker was refused. A separate normal correction/fresh independent-pass probe cleared the flag, returned awaiting_approval and left approvals empty. This proves rejection does not become approval and that restart/questions cannot erase the correction budget.

All **37 tests passed** with `.venv/Scripts/python.exe -m unittest discover -s tests -v` against these final runtime versions. The earlier independent original P1–P4 and two-sprint probes remain applicable; final changes add only the persistent rejection gate. The reviewer made no implementation, canonical-state, template or human-approval edits. The read-only adapter and externally executed stage-evidence scope remain the boundary stated above. This agent pass grants no human acceptance, live-project activation or publication authority.

### Second-correction exact final manifest

SHA-256 of complete bytes including line endings. This is the current authoritative target manifest for this independent review; earlier manifests are retained only for provenance. Any target change requires a new independent delta review.

| Target in tool repository | SHA-256 |
|---|---|
| asdlc/__init__.py | `0ad0a9cdcefe9c7b3f786bdbaa5f56ed1e80724cf8fb4be5bc686984307831c2` |
| asdlc/__main__.py | `cf7390a2508a0fcad4777a4a629fc5212ab655cb45845975995f835676a834e3` |
| asdlc/adapters.py | `e618a9013561a53c79bfd097ad8a5eceb945df606e43087b8c39558d1154106e` |
| asdlc/cli.py | `a63d6aa33ba5fd141304b87b09712710aacb22d0fe48b771b387439849ce89b6` |
| asdlc/code_version.py | `a17ef1a21f32247f12b12e9fade2c333cd318c8e27bde98e1521bfe8f8c76734` |
| asdlc/engine.py | `4cb405a54fb68e425a84f45677816559bfab690c002720033df9b689143703c7` |
| asdlc/pipeline.py | `b40c75a2688fdb82a8b7382ae1adf9b6efc52ec41217b4030bc61f328603e5df` |
| asdlc/schemas/approvals.json | `0189178663c1112eef78f471aee9201befecb7ca5b869f1c1d0c98ef97200a99` |
| asdlc/schemas/decisions.json | `a8cc4c19b4d8258c117eeb1f7f40b6cf1dfa0aa8559d440a40de094c14ea5790` |
| asdlc/schemas/pipeline-state.json | `b80eeebee3d43f27ee5c53c036ef1260d5bc802c1add5f1ab377caf5a55b34b9` |
| asdlc/schemas/project-state.json | `726e2a74077f4ab6710ae9dced765328e49961cef3d03b6d21345c7903ebe1f0` |
| asdlc/schemas/questions.json | `81fc57f18dbb511a9ea670082055a12b4720419bef0827388a2e5c6ceedb9e2b` |
| asdlc/schemas/raid.json | `2c32add575283dfc6d3bf0a296c18bacca2c8282bae6b01d8834558673ea8811` |
| asdlc/schemas/review-findings.json | `72db003171d5bf34d36ff60530067fd04615e69a55cad6acb87b22d2d1e3d8be` |
| asdlc/schemas/stage-result.json | `1ddadb582e1822939f6e8231356a63dd6fcafded3a6750311a74eea6f54133f9` |
| asdlc/store.py | `8717acee0f7ab56e7d875e51d8f3bb14ea7fb0f360d7f0637a793b3349eb4fd3` |
| prompts/architecture.md | `14878481ace41b4ed6c5ef417239592af270253bd7ae6ffd3fb9bf4dee3fab5e` |
| prompts/business-requirements.md | `c6c5dfd8362cc253e5b08d685bfe4fa61ec1e815dfd14614f73e9c46b1aeb5f3` |
| prompts/challenger.md | `80a0b0de8abcc1efc692440221316cd4402e545f0789413611692ee9f3696aad` |
| prompts/development.md | `e5c359a261ccf521266781270fd10654496913c679c8f04d10b447141a834812` |
| prompts/discovery.md | `23968a8e2efcfcb0a5db5271ff4f9f3f26bb9e0e07cf96594f829da27e2d6bad` |
| prompts/orchestrator.md | `76b88d661651ffa6d837fd49bf5cad02aa3ee98e9f7abf0923ec3aef8868f8ca` |
| prompts/sprint-planning.md | `2b94d5b74257ca308a05fa96dbf01cb1541fd0d20e09c213a6576db0ec3295cf` |
| prompts/sprint-review.md | `0e1f5e6baa3e6f17f76f2463a973a362072511a83267a646320551ed607a6972` |
| prompts/testing.md | `74e889de9d77fbd0da9676f3c22f5786ac0eab04e559e70e51b1e12a603a1e0a` |
| schemas/approvals.json | `0189178663c1112eef78f471aee9201befecb7ca5b869f1c1d0c98ef97200a99` |
| schemas/decisions.json | `a8cc4c19b4d8258c117eeb1f7f40b6cf1dfa0aa8559d440a40de094c14ea5790` |
| schemas/pipeline-state.json | `b80eeebee3d43f27ee5c53c036ef1260d5bc802c1add5f1ab377caf5a55b34b9` |
| schemas/project-state.json | `726e2a74077f4ab6710ae9dced765328e49961cef3d03b6d21345c7903ebe1f0` |
| schemas/questions.json | `81fc57f18dbb511a9ea670082055a12b4720419bef0827388a2e5c6ceedb9e2b` |
| schemas/raid.json | `2c32add575283dfc6d3bf0a296c18bacca2c8282bae6b01d8834558673ea8811` |
| schemas/review-findings.json | `72db003171d5bf34d36ff60530067fd04615e69a55cad6acb87b22d2d1e3d8be` |
| schemas/stage-result.json | `1ddadb582e1822939f6e8231356a63dd6fcafded3a6750311a74eea6f54133f9` |
| tests/test_pipeline.py | `c453e8a48d6c911285fdbf78ed7e705c7c416f1fe2b163bce62df71c1388689e` |
| tests/test_workflow.py | `1bc390a1d4376207f3d44faf740d82e15460b1db66e3555aa017e97dfe8f96aa` |
| tools/generate_contracts.py | `4fba26419844c7c7314a4e3cdc9d60f220d1a43f4b791494794b4ddd7a3f4efa` |
| tools/generate_pipeline_schema.py | `fb6d34e9f9a8859a16fa2f9c99d0f9b511a429efb83d3fce93e294dda59a164d` |

## Final Codex wire-schema delta

Review ID: REVIEW-PIPELINE-CODE-005. Verdict: **pass** for the final hashes below, with P1–P5 resolved. The reviewer inspected the temporary output schema requiring every property while permitting null code_version, and normalization that removes an inapplicable null before canonical schema validation. Mandatory actual delivery-code binding remains enforced by Engine.submit; normalization does not waive that gate. The targeted stage-prompt/output-contract test passed independently. The 37-test full suite above preceded this small adapter/test delta; appropriate targeted validation after it passed. No new meaningful findings. Actual backend execution remains separate evidence, not established by a mocked prompt test.

### Final current manifest

This supersedes all prior target manifests for current agent review. SHA-256 of complete bytes including line endings. Human acceptance remains a separate exact-version decision.

| Target in tool repository | SHA-256 |
|---|---|
| asdlc/__init__.py | `0ad0a9cdcefe9c7b3f786bdbaa5f56ed1e80724cf8fb4be5bc686984307831c2` |
| asdlc/__main__.py | `cf7390a2508a0fcad4777a4a629fc5212ab655cb45845975995f835676a834e3` |
| asdlc/adapters.py | `e618a9013561a53c79bfd097ad8a5eceb945df606e43087b8c39558d1154106e` |
| asdlc/cli.py | `a63d6aa33ba5fd141304b87b09712710aacb22d0fe48b771b387439849ce89b6` |
| asdlc/code_version.py | `a17ef1a21f32247f12b12e9fade2c333cd318c8e27bde98e1521bfe8f8c76734` |
| asdlc/engine.py | `4cb405a54fb68e425a84f45677816559bfab690c002720033df9b689143703c7` |
| asdlc/pipeline.py | `b40c75a2688fdb82a8b7382ae1adf9b6efc52ec41217b4030bc61f328603e5df` |
| asdlc/schemas/approvals.json | `0189178663c1112eef78f471aee9201befecb7ca5b869f1c1d0c98ef97200a99` |
| asdlc/schemas/decisions.json | `a8cc4c19b4d8258c117eeb1f7f40b6cf1dfa0aa8559d440a40de094c14ea5790` |
| asdlc/schemas/pipeline-state.json | `b80eeebee3d43f27ee5c53c036ef1260d5bc802c1add5f1ab377caf5a55b34b9` |
| asdlc/schemas/project-state.json | `726e2a74077f4ab6710ae9dced765328e49961cef3d03b6d21345c7903ebe1f0` |
| asdlc/schemas/questions.json | `81fc57f18dbb511a9ea670082055a12b4720419bef0827388a2e5c6ceedb9e2b` |
| asdlc/schemas/raid.json | `2c32add575283dfc6d3bf0a296c18bacca2c8282bae6b01d8834558673ea8811` |
| asdlc/schemas/review-findings.json | `72db003171d5bf34d36ff60530067fd04615e69a55cad6acb87b22d2d1e3d8be` |
| asdlc/schemas/stage-result.json | `1ddadb582e1822939f6e8231356a63dd6fcafded3a6750311a74eea6f54133f9` |
| asdlc/store.py | `8717acee0f7ab56e7d875e51d8f3bb14ea7fb0f360d7f0637a793b3349eb4fd3` |
| prompts/architecture.md | `14878481ace41b4ed6c5ef417239592af270253bd7ae6ffd3fb9bf4dee3fab5e` |
| prompts/business-requirements.md | `c6c5dfd8362cc253e5b08d685bfe4fa61ec1e815dfd14614f73e9c46b1aeb5f3` |
| prompts/challenger.md | `80a0b0de8abcc1efc692440221316cd4402e545f0789413611692ee9f3696aad` |
| prompts/development.md | `e5c359a261ccf521266781270fd10654496913c679c8f04d10b447141a834812` |
| prompts/discovery.md | `23968a8e2efcfcb0a5db5271ff4f9f3f26bb9e0e07cf96594f829da27e2d6bad` |
| prompts/orchestrator.md | `76b88d661651ffa6d837fd49bf5cad02aa3ee98e9f7abf0923ec3aef8868f8ca` |
| prompts/sprint-planning.md | `2b94d5b74257ca308a05fa96dbf01cb1541fd0d20e09c213a6576db0ec3295cf` |
| prompts/sprint-review.md | `0e1f5e6baa3e6f17f76f2463a973a362072511a83267a646320551ed607a6972` |
| prompts/testing.md | `74e889de9d77fbd0da9676f3c22f5786ac0eab04e559e70e51b1e12a603a1e0a` |
| schemas/approvals.json | `0189178663c1112eef78f471aee9201befecb7ca5b869f1c1d0c98ef97200a99` |
| schemas/decisions.json | `a8cc4c19b4d8258c117eeb1f7f40b6cf1dfa0aa8559d440a40de094c14ea5790` |
| schemas/pipeline-state.json | `b80eeebee3d43f27ee5c53c036ef1260d5bc802c1add5f1ab377caf5a55b34b9` |
| schemas/project-state.json | `726e2a74077f4ab6710ae9dced765328e49961cef3d03b6d21345c7903ebe1f0` |
| schemas/questions.json | `81fc57f18dbb511a9ea670082055a12b4720419bef0827388a2e5c6ceedb9e2b` |
| schemas/raid.json | `2c32add575283dfc6d3bf0a296c18bacca2c8282bae6b01d8834558673ea8811` |
| schemas/review-findings.json | `72db003171d5bf34d36ff60530067fd04615e69a55cad6acb87b22d2d1e3d8be` |
| schemas/stage-result.json | `1ddadb582e1822939f6e8231356a63dd6fcafded3a6750311a74eea6f54133f9` |
| tests/test_pipeline.py | `c453e8a48d6c911285fdbf78ed7e705c7c416f1fe2b163bce62df71c1388689e` |
| tests/test_workflow.py | `1bc390a1d4376207f3d44faf740d82e15460b1db66e3555aa017e97dfe8f96aa` |
| tools/generate_contracts.py | `4fba26419844c7c7314a4e3cdc9d60f220d1a43f4b791494794b4ddd7a3f4efa` |
| tools/generate_pipeline_schema.py | `fb6d34e9f9a8859a16fa2f9c99d0f9b511a429efb83d3fce93e294dda59a164d` |
