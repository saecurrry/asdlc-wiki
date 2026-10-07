---
id: REVIEW-PIPELINE-CODE-001
project_id: asdlc
title: Seven-stage orchestration independent code review
status: changes-required
reviewer: independent-implementation-challenger
review_date: 2026-10-06
human_approval: not-granted
---

# Independent seven-stage orchestration code review

Verdict: **changes required** for these exact versions. Four meaningful findings below. The reviewer changed no runtime, state, template or approval file. Human approval is distinct from this review. Current harness execution remains read-only; this review does not claim autonomous coding or executed integrated testing.

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
