---
id: REVIEW-WIKI-TEMPLATES-001
project_id: asdlc
title: Independent wiki template alignment review
status: reviewed
reviewer: wiki_template_challenger
human_acceptance: pending
---

# Independent wiki template alignment review

Review completed: 2026-10-05T21:42:49.841993+00:00. Reviewer: independent agent `/root/wiki_template_challenger`; author: parent implementation agent. This review does not grant human acceptance, activate a project, or authorise publication.

## Scope and verdict

**Pass. No blocking findings and no material corrections required for the reviewed versions.**

Reviewed the agent-use templates, wiki operation/resume guidance, contribution lifecycle, runtime schema copies, project state guidance and preserved legacy records. Later delivery stage contracts remain explicitly proposed; runtime dispatch remains serial discovery only.

## Checks and evidence

- All seven wiki schemas match both `asdlc/schemas/` (the runtime-loaded source) and root `schemas/` byte for byte. Their file SHA256 values match `schemas/source-manifest.json`; all pass Draft 2020-12 schema meta-validation.
- Relative Markdown links resolve across 36 scoped guidance/template files. Shared-context paths are portable from `templates/project/` to `projects/<id>/` because both have the same depth.
- Seven archived split JSON records retain the original tracked template content, allowing only newline normalization. They are labelled incompatible/inert and are outside the current project template.
- The current ASDLC project has no project-root `state.json`; guidance identifies the documentation bootstrap as unactivated, preserves its immutable baseline, and does not invent human approvals.
- State guidance matches inspected store/engine/CLI behavior: one project-root runtime record, revision and dispatch binding, canonical JSON content hashes distinct from file hashes, serial discovery, orchestrator-owned status/RAID views and current resource invalidation on resume.
- Stage templates provide distinct source/input bindings, unknowns, measurable requirements, business rules, C4 context/container views, failure paths, dependencies, traceability, executed test provenance, independent review and separate human gates. Placeholders are clearly drafts and do not assert executed evidence.
- Agent instructions require focused retrieval and exact version/status checks; shared knowledge separates observed facts from proposals and requires independent challenge before promotion plus human owner approval for mandatory standards.

## Findings

None. Review pass applies only to the exact file-byte manifest below. Any change to a target file requires impact assessment and a new review for the changed version.

## Limitations

This is a template and documentation compatibility review, not execution evidence for planned BRD/HLD/backlog/sprint runtime stages. No live project workflow was started. No human acceptance was recorded. Local fixture runtime test evidence and publication remain separate concerns.

## Completion delta review

Delta reviewed: 2026-10-05T21:44:47.216320+00:00. **Pass; no meaningful findings.** Living build-plan templates and the current ASDLC plan distinguish supplied intent, authorised local actions, pending acceptance, historical test evidence, inactive runtime state and next permitted actions. Their resume/recovery contracts preserve source histories and reject stale evidence. Updated template/project/review index links resolve. Root code-repository AGENTS guidance routes future sessions to the configured separate wiki and its current templates, gives CLI global flags consistent with inspected argparse definitions, and preserves current permission/approval boundaries.

## SHA256 target manifest

Paths are relative to the wiki root. Digests bind exact file bytes, not canonical runtime content hashes. This refreshed manifest includes the completion delta.

| Target | SHA256 |
|---|---|
| `AGENTS.md` | `25df5f86eb21d5e83aea41e0a055107c6851f1a9a5d6ee73aecd32d6d0bede3d` |
| `CONTRIBUTING.md` | `6b821453f5f2ddceab0a3bd0708d71150c05ab93bdd1d313f141690a96b14237` |
| `README.md` | `93826118d2cd568ff221b29346081880d397d2c6ece2315286de98232a18a05a` |
| `projects/asdlc/build-plan.md` | `a0dc78646ae3e14d9990c18915765c1f71bb80d2174ea25d017aedf8ef8c6dbe` |
| `projects/asdlc/index.md` | `409b384a2d6915372d8f15aa48e6176147577391fbffb34446292e02362e141a` |
| `projects/asdlc/reviews/index.md` | `270da6a6e85882af6f664d6a3892d27b2be35ce7930e71eead47789fa9221b2d` |
| `projects/asdlc/state/index.md` | `c8f829b5cbd4ce239868843345ec3b1d3a7ee59066dd0566706747dda2c9d0fb` |
| `schemas/approvals.json` | `0189178663c1112eef78f471aee9201befecb7ca5b869f1c1d0c98ef97200a99` |
| `schemas/decisions.json` | `a8cc4c19b4d8258c117eeb1f7f40b6cf1dfa0aa8559d440a40de094c14ea5790` |
| `schemas/index.md` | `1e5ee1fe1570708a5b0b8cfac810a9c48febfa6d63c34e3a9f29771a2d9d7a81` |
| `schemas/project-state.json` | `86f350f0d4c8086c979152ae2b7d3efbbbddfad89d820272d08ccd8200d116f4` |
| `schemas/questions.json` | `81fc57f18dbb511a9ea670082055a12b4720419bef0827388a2e5c6ceedb9e2b` |
| `schemas/raid.json` | `2c32add575283dfc6d3bf0a296c18bacca2c8282bae6b01d8834558673ea8811` |
| `schemas/review-findings.json` | `72db003171d5bf34d36ff60530067fd04615e69a55cad6acb87b22d2d1e3d8be` |
| `schemas/source-manifest.json` | `f2581dda71db8623f0a2aa2ee9684c3c66f2b1d955e1cb6710f46b86994e9c0f` |
| `schemas/stage-result.json` | `b3b016f97f65fbce8568e7fefde9f2a1bad605b24d7c1859347c74e34a1b1d87` |
| `templates/index.md` | `6bf188115011943f7b1c54f214693bb94778c485708f901697641c4aca7a4d34` |
| `templates/knowledge-entry.md` | `59c765cf6bf1523f0c154217ebce73e622b55a5652635db0290428bcd059df1e` |
| `templates/legacy-state-v0/approvals.json` | `acfd918691564ddf8c54b5e1330dd76126dbc6ed456ab8ada6a422ea14874864` |
| `templates/legacy-state-v0/decisions.json` | `acfd918691564ddf8c54b5e1330dd76126dbc6ed456ab8ada6a422ea14874864` |
| `templates/legacy-state-v0/events.json` | `acfd918691564ddf8c54b5e1330dd76126dbc6ed456ab8ada6a422ea14874864` |
| `templates/legacy-state-v0/findings.json` | `acfd918691564ddf8c54b5e1330dd76126dbc6ed456ab8ada6a422ea14874864` |
| `templates/legacy-state-v0/index.md` | `4e214a4cb6e20a1f3f709a7d34bf0afd279d6601c4c277e41b9faef7acee471f` |
| `templates/legacy-state-v0/project.json` | `fdc37a66eda12a1ecfe6ac245d9bf95171c6385aae927ea8a7c3d09dac477b15` |
| `templates/legacy-state-v0/questions.json` | `acfd918691564ddf8c54b5e1330dd76126dbc6ed456ab8ada6a422ea14874864` |
| `templates/legacy-state-v0/raid.json` | `acfd918691564ddf8c54b5e1330dd76126dbc6ed456ab8ada6a422ea14874864` |
| `templates/project/approvals/approval.md` | `2cdbb0447affbbe4d6d8515a783ed4fe8b99f635888af7f4f4268c2638d3eb83` |
| `templates/project/approvals/index.md` | `874e50bb8049227c1168ec53607e72b836e680f182c7d74f85a1309efad86335` |
| `templates/project/architecture/hld.md` | `7765de0c755548670415227689148d0ff7dda0698e05ac136ca481442e5053cc` |
| `templates/project/architecture/index.md` | `da6108c267c66bf285d4ca4102a3326d85e1f38eba0dbb26763de733d1f511c5` |
| `templates/project/backlog/index.md` | `032e8f5a2562e5f33a893fe246ea74500b55f0e61486b858e37d6c0f262de891` |
| `templates/project/backlog/story.md` | `5815fa68f36f54b51f3c24875dd4a79ef2a69fb37e83bdd9a66bf0c38f89917b` |
| `templates/project/build-plan.md` | `9fc1f003696686602fa6ef70a70a29f6bd9e213255c3da64596567cf6c60cc43` |
| `templates/project/decisions/decision.md` | `14fc52193476b45f710f36199e0e5fb8f250230d82dd8c4f833c8dc86f251397` |
| `templates/project/decisions/index.md` | `70d1cf1863d09268e5b50b3d516e43b192aa2741fe967442372bff8308bd38ce` |
| `templates/project/discovery/brief.md` | `59814e02b5ddc19b5b4bbe4d7171a5485fdb286fc55500709ebe8731b0257192` |
| `templates/project/discovery/index.md` | `9d1abbf99fca931c3eebf0c14ace74172248d6972ed6df02a0dfe64e42ca9189` |
| `templates/project/index.md` | `701ab26124d78c1519c4fe8a03c3eee638c988a8e013c978f9daa84055dbc23e` |
| `templates/project/lessons/index.md` | `210dc20147e63b9184ccfb596e8cd1fe7f004c644b7b14a7d098e1426afa3cf4` |
| `templates/project/lessons/lesson.md` | `cf0e1a3d5d2b572fa4bdb14ee2f02df62304ba7ff6a56ad3479c7f73ed345012` |
| `templates/project/project-status.md` | `6c94a6b06c424edeadbf6861e646239f14d962785b7c5338a6ebab27d6274974` |
| `templates/project/raid.md` | `65f2dcadc4204c2e8eb95d61681bb95645edf52118d3c640f92ffc61f06a804a` |
| `templates/project/requirements/brd.md` | `13466483db01fca3cba3df75ed518e44de93665bee183d1c52cb33b77837e778` |
| `templates/project/requirements/index.md` | `1b5f3eb7959fe2dc2f0a0ee27ecf1dbe5452516cb27045d52d8401681a765d5d` |
| `templates/project/reviews/index.md` | `7fdaf2e056c6b5eda68b804cdf549a897f4efd9f394f192cba68e8ff48dd09e4` |
| `templates/project/reviews/review.md` | `f30db929bd97babf3558f94b0c3100555da8557f18cb4951cef2b5a949960ff7` |
| `templates/project/sprints/index.md` | `f75341636e96656244f55fbd66a819582444e6d1da0e60803558511f3979842a` |
| `templates/project/sprints/sprint-plan.md` | `06b7167fc09d71f4c5aedd7e893edf609bcc71ec9f39b5e869f305a31caca1dd` |
| `templates/project/sprints/sprint-report.md` | `8c00a235688e1ff7be2d4de81f9cf670ea3b739024279228678e40c3f61b39b4` |
| `templates/project/sprints/test-evidence.md` | `e2e4993138ba0740c3a7e90cc697a71ffa77dc2e80e16b6e753cb70fda33fb7b` |
| `templates/project/state/index.md` | `40f19915850209a73ebe7bf2436a28ebc9e2667bc78e5833a4da5c5a0dd50584` |

## SHA256 supporting source manifest

Paths are relative to the code repository root. These were inspected, not edited by this reviewer.

| Source | SHA256 |
|---|---|
| `AGENTS.md` | `07e424bfbf40b4d5a57baa2705575b5ab5c0c744e26a850f8c9ec5e990323b03` |
| `asdlc/cli.py` | `48a4c55cd67e44ae98aa630273e1854849f6aa0cac5895f971c485e0c220e5ce` |
| `asdlc/engine.py` | `a5b41acfc5935cc1cca993ec03f364a806e2f5d05788a6f2d173a9c1cff1a273` |
| `asdlc/schemas/approvals.json` | `0189178663c1112eef78f471aee9201befecb7ca5b869f1c1d0c98ef97200a99` |
| `asdlc/schemas/decisions.json` | `a8cc4c19b4d8258c117eeb1f7f40b6cf1dfa0aa8559d440a40de094c14ea5790` |
| `asdlc/schemas/project-state.json` | `86f350f0d4c8086c979152ae2b7d3efbbbddfad89d820272d08ccd8200d116f4` |
| `asdlc/schemas/questions.json` | `81fc57f18dbb511a9ea670082055a12b4720419bef0827388a2e5c6ceedb9e2b` |
| `asdlc/schemas/raid.json` | `2c32add575283dfc6d3bf0a296c18bacca2c8282bae6b01d8834558673ea8811` |
| `asdlc/schemas/review-findings.json` | `72db003171d5bf34d36ff60530067fd04615e69a55cad6acb87b22d2d1e3d8be` |
| `asdlc/schemas/stage-result.json` | `b3b016f97f65fbce8568e7fefde9f2a1bad605b24d7c1859347c74e34a1b1d87` |
| `asdlc/store.py` | `05991f0856672d1aff8447b976f3d94c869021b2e7203af8d6a8bb921714300f` |
