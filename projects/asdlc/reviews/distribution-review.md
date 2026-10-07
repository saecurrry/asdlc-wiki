---
id: REVIEW-DISTRIBUTION-001
project_id: asdlc
title: Installed distribution and bundled prompts independent review
status: passed
reviewer: independent-implementation-challenger
review_date: 2026-10-06
human_approval: not-granted
---

# Independent installed distribution review

Verdict: **pass** for the scoped exact targets below. Meaningful findings: **none**. This is a new packaging review; the previous pipeline code review and immutable lifecycle evidence were not overwritten or rebound. Human acceptance, publication and real-project activation remain separate.

## Reviewed change

Default prompt resolution now uses the installed asdlc/prompts directory when no override is supplied. Engine and CLI pass None by default; an explicit --prompts directory still overrides it. pyproject.toml ships schemas and all nine Markdown contracts as package data. Root source contracts and packaged copies are equal, with an executable mirror regression. The old v1 generator is guarded before any writes so it cannot overwrite the reviewed current contracts.

## Independent executed evidence

- Retained wheel: asdlc-0.1.0-py3-none-any.whl, SHA-256 `3b6a8090f12696d7fdaa224d103e89a477923c177b43c05e7b0221375b02a1ec`.
- The author's clean-install verifier evidence was inspected at the local distribution-checks run 9f6e5a76348b4208a606bb9ae0b51e78. It records fresh-venv wheel installation, schema-v2 fixture init, nine packaged prompts and synthetic default prompt probing, explicitly denying actual Codex execution/application delivery/live activation.
- Independently compared the retained wheel's Python modules and all nine bundled prompts to current source bytes; they match. The wheel contains packaged runtime assets rather than planning/tests/project folders, as the verifier checks.
- Independently ran installed Python with -I from the separate application's Git root, without importing framework source. asdlc.__file__ resolved under the fresh environment's site-packages. Default adapter prompt loading succeeded for all seven stage specialists using synthetic returned results; installed challenger and orchestrator contracts were also present. No canonical state was persisted by this additional probe, no Codex process was invoked and no application code was delivered.
- The installed asdlc console entry point --help succeeded from the separate application directory and exposed the expected orchestration commands.
- `.venv/Scripts/python.exe -m unittest discover -s tests -p test_distribution.py -v` passed the root/package byte-for-byte mirror test.
- Independently invoked the obsolete generator guard after hashing all root/package schemas/prompts. It stopped with the explicit historical-generator-disabled message; every recorded hash remained unchanged.

Local retained independent probe output: .asdlc-local/distribution-review-installed-probe.json. All verification files are local fixture evidence. The fixture application is its own Git root within the ignored .asdlc-local verification area; process isolation and installed-module provenance establish that source-checkout prompt files are unnecessary. This is not a claim of testing on a second clean machine or another operating system.

## Drift and generator assessment

There are two checked-in prompt locations. The mirror regression makes drift a failing standard test, and the reviewed current source/package/wheel copies agree. Future prompt edits must update both copies and rerun that check before a new wheel build. The historical generator intentionally no longer regenerates current contracts; it fails before writing instead of silently replacing them with old discovery-only instructions. The separate v2 schema generator and prior lifecycle behaviour are not expanded or reapproved by this packaging pass.

## Limits and ownership

This demonstrates usable wheel installation, console registration, bundled schema/prompt availability and installed default resolution. It does not demonstrate real seven-stage Codex execution, autonomous application changes, integrated testing, human acceptance or production readiness. Synthetic prompt outputs carry no business approval. The verifier creates labelled local fixture projects only. No live wiki project was activated and no push, merge, release or publication occurred. The reviewer edited only this new review report and disposable local verification evidence; implementation and prior reports remain unchanged.

## Exact scoped target manifest

SHA-256 of complete file bytes including line endings. Tool-repository paths are listed as source identities; wiki review links remain relative. Any target changes require independent delta review for this packaging scope.

| Target in tool repository | SHA-256 |
|---|---|
| asdlc/adapters.py | `64f08607b4b380b633a3a8f719a2f3700dbdc734676b5c4db5bc7d5798fafe9e` |
| asdlc/cli.py | `60fe1237951138de99b398c6d28cc6347d4c0d6d04831d7ba088c74e9d1d7133` |
| asdlc/engine.py | `497f9b96ba07690cac04ab1962aa8e6e39e43b22fd807645238b010ef2648dad` |
| asdlc/prompts/architecture.md | `14878481ace41b4ed6c5ef417239592af270253bd7ae6ffd3fb9bf4dee3fab5e` |
| asdlc/prompts/business-requirements.md | `c6c5dfd8362cc253e5b08d685bfe4fa61ec1e815dfd14614f73e9c46b1aeb5f3` |
| asdlc/prompts/challenger.md | `80a0b0de8abcc1efc692440221316cd4402e545f0789413611692ee9f3696aad` |
| asdlc/prompts/development.md | `e5c359a261ccf521266781270fd10654496913c679c8f04d10b447141a834812` |
| asdlc/prompts/discovery.md | `23968a8e2efcfcb0a5db5271ff4f9f3f26bb9e0e07cf96594f829da27e2d6bad` |
| asdlc/prompts/orchestrator.md | `76b88d661651ffa6d837fd49bf5cad02aa3ee98e9f7abf0923ec3aef8868f8ca` |
| asdlc/prompts/sprint-planning.md | `2b94d5b74257ca308a05fa96dbf01cb1541fd0d20e09c213a6576db0ec3295cf` |
| asdlc/prompts/sprint-review.md | `0e1f5e6baa3e6f17f76f2463a973a362072511a83267a646320551ed607a6972` |
| asdlc/prompts/testing.md | `74e889de9d77fbd0da9676f3c22f5786ac0eab04e559e70e51b1e12a603a1e0a` |
| prompts/architecture.md | `14878481ace41b4ed6c5ef417239592af270253bd7ae6ffd3fb9bf4dee3fab5e` |
| prompts/business-requirements.md | `c6c5dfd8362cc253e5b08d685bfe4fa61ec1e815dfd14614f73e9c46b1aeb5f3` |
| prompts/challenger.md | `80a0b0de8abcc1efc692440221316cd4402e545f0789413611692ee9f3696aad` |
| prompts/development.md | `e5c359a261ccf521266781270fd10654496913c679c8f04d10b447141a834812` |
| prompts/discovery.md | `23968a8e2efcfcb0a5db5271ff4f9f3f26bb9e0e07cf96594f829da27e2d6bad` |
| prompts/orchestrator.md | `76b88d661651ffa6d837fd49bf5cad02aa3ee98e9f7abf0923ec3aef8868f8ca` |
| prompts/sprint-planning.md | `2b94d5b74257ca308a05fa96dbf01cb1541fd0d20e09c213a6576db0ec3295cf` |
| prompts/sprint-review.md | `0e1f5e6baa3e6f17f76f2463a973a362072511a83267a646320551ed607a6972` |
| prompts/testing.md | `74e889de9d77fbd0da9676f3c22f5786ac0eab04e559e70e51b1e12a603a1e0a` |
| pyproject.toml | `1af40f60f2d1f7fe100d3079d77e3cd9a3256e8ad58df649441eef2e15d54bc4` |
| tests/test_distribution.py | `8e6c3fcbb38ff916ae7850df75cfd024dd8bea95e57f8c57c7fd19c1ee5f7996` |
| tools/generate_contracts.py | `31cb7347f60c133cf94882e945679afb76376bbd4c1525142c9064738b9e2002` |
| tools/verify_distribution.py | `bab06da8b53b07cf1cc03f1330de42875e9ecfec2545b5929f62121c4c014865` |

## Retained install evidence manifest

| Local evidence | SHA-256 |
|---|---|
| .asdlc-local/distribution/asdlc-0.1.0-py3-none-any.whl | `3b6a8090f12696d7fdaa224d103e89a477923c177b43c05e7b0221375b02a1ec` |
| .asdlc-local/distribution-checks/9f6e5a76348b4208a606bb9ae0b51e78/evidence.json | `ce5467dfc15ad718407447045411ffc3cba14595ed262b9b9f52d25194c2dda7` |
| .asdlc-local/distribution-review-installed-probe.json | `c37cce0bd7b921caf62774487587beab85c1d65c66dc6ee41fc0727f8371a7b6` |

## Portable retained evidence

The reviewer also checked the [distribution source manifest](../sprints/evidence/distribution-source-manifest.json): every listed hash matches the current scoped files. The [install record](../sprints/evidence/distribution-install.json) matches the independently checked wheel digest and retains the explicit no-real-Codex/no-delivery/no-live-activation limits. The owning agent reports all 38 framework tests and diff checks passed after the packaging change; this reviewer independently executed the focused distribution regression and installed probes described above, rather than claiming a duplicate full-suite run.
