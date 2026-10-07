---
id: REVIEW-DELIVERY-001
project_id: asdlc
title: Scoped application delivery independent review
status: independent-pass
reviewer: independent-implementation-challenger
review_date: 2026-10-06
human_approval: not-granted
---

# Independent delivery increment review

Current verdict: **independent pass for the final exact manifest below**, with no unresolved blocking findings. DEL1–DEL6 were corrected and independently checked. Human approval is not granted by this report. The initial findings, inspected versions and correction observations below are retained as historical provenance; their original open dispositions are superseded only by the final resolution table. Earlier lifecycle/distribution reports and approvals were not rewritten. No real application or wiki project was activated by the reviewer.

## Scope and evidence boundary

Reviewed exact human-approved sprint JSON write scope/test argv, read-only proposal adapter, copied-source checks, orchestrator integration/rollback, code version/evidence, artifact inventory identities/materialisation and relevant schema/tests. Test commands are trusted local project code, as explicitly documented; copying source is not an OS isolation boundary. Probes used disposable local Git targets and wiki fixtures only. No real Codex/application delivery success is claimed by this review.

## Findings

### DEL1 — Windows path aliases bypass protected Git metadata exclusion

Severity: high. Blocking: yes. Owner: delivery path validator. Disposition: open.

Independent probe: a contract/proposal for `.git./hooks/asdlc-review-probe.txt` passed Transaction construction and checks, and apply wrote the file at `.git/hooks/asdlc-review-probe.txt`. The probe then removed it through rollback in the disposable Git repository. Windows resolves `.git.` to `.git`; safe_path checks only the unnormalised spelling, and target_path checks containment without rejecting protected resolved components. Similar trailing-space/dot and device aliases need consideration.

Impact: protected metadata can be changed despite the deterministic exclusion, including hooks outside code-version inventory. Requested resolution: reject nonportable trailing-dot/space components, Windows device names and aliases, and recheck resolved relative components against protected directories. Human-approved write_paths must not override protected runtime/Git metadata boundaries. Add Windows regressions and verify normal nested source paths remain usable.

### DEL2 — A second-file write failure leaves the first code change applied

Severity: high. Blocking: yes. Owner: code transaction/rollback. Disposition: open.

Independent probe: Transaction with two approved files wrote a.py; b.py write raised OSError before touching b.py. apply had appended b.py to applied before writing it. rollback compared original b.py bytes with proposed after bytes, misclassified the failed operation as a concurrent edit and raised before reaching a.py. a.py remained changed while b.py was original, and no canonical success could be committed.

Impact: ordinary filesystem failure loses the all-or-recovered preservation property; partial writes can produce the same problem. Requested resolution: use atomic byte replacements for proposed files, track only completed mutations, restore prior completed paths on failure, and distinguish failed writes from actual concurrent edits. Keep commit detection and recovery under the canonical lock. Add a multi-file injected failure test through Engine submit, including partial-write/replace and canonical pre/postcommit errors.

### DEL3 — Current inventory can reuse an approved upstream ID for another type

Severity: medium. Blocking: yes. Owner: artifact identity/traceability. Disposition: open.

Independent probe: approved upstream artifacts include initiative I1 and epic E1(parent I1). Sprint-planning story I1(parent E1) was accepted by validate_inventory. known built from upstream+new values shadows the upstream I1 type; parent validation alone does not prevent the identity collision.

Impact: requirement/epic/story traceability refers to ambiguous stable IDs across stage artifacts. Requested resolution: validate IDs against approved upstream and persistent artifact identity/type/ownership, rejecting conflicting reuse while allowing legitimate same-story version refinement across sprint epochs. Add cross-type and historical/refinement regressions.

### DEL4 — First executed test failure holds without owner repair/review/retest flow

Severity: high. Blocking: yes. Owner: delivery failure routing. Disposition: open.

Evidence: Engine.submit CheckFailure branch stores result/evidence, sets status blocked immediately and clears dispatch, irrespective of repair_limit. There is no automatic development correction handoff or retest path from that failure. Existing test expects blocked at the first failure. A failed integrated testing stage likewise stays testing/blocked rather than returning its defect to development, getting fresh code review and rerunning testing. Saved evidence is useful, but escalation happens before the configured repair budget can operate.

Impact/criterion: the new executable increment lacks the agreed owner-correction and integrated defect repair/review/retest loop; ordinary defects require manual scope reset or unmanaged source edits. Requested resolution: distinguish execution/environment failures requiring human input from correctable code/test defects, persist findings and failure context, route to the owning stage under bounded policy, then independently review/retest before acceptance. Exhaustion must hold, and infrastructure inability must never become a pass. If deliberately narrower, explicitly gate and report that limitation rather than representing an automatic defect cycle as implemented.

## Earlier lock-boundary observation

Initial inspection found rollback outside Store.update's lock. Before this manifest, the author introduced an on_failure callback inside the locked action/save block; current code was inspected and that lock-boundary concern is no longer asserted as an open finding. DEL2 still concerns mutation accounting and remains distinct. Callback commit detection must continue distinguishing postcommit rendering failure from precommit failure.

## Initial exact reviewed manifest

SHA-256 of complete on-disk bytes including line endings. These are the current inspected targets during correction, not human approval or proof that subsequent repairs were tested. Findings describe the independently reproduced pre-repair algorithms above; final repaired versions need a separate re-review manifest.

| Target in tool repository | SHA-256 |
|---|---|
| asdlc/adapters.py | `6ab8b7dd13e5a12e908b7c0432f4978fe88e5a0bb1eafc96dfeda67a307ef5f9` |
| asdlc/artifacts.py | `aa875db8fd67f590a90b3cd54913c55d98e226bcae58227e5bd6317e71301aa7` |
| asdlc/delivery.py | `eab7d87733034d127185d839f1c9fe3a7b4b0d545db97dff74a7e1d3e5640e59` |
| asdlc/engine.py | `10fdac3e7c5cb3e2e6f92108d8694978ff200004462750e94b8e8d6858a49270` |
| asdlc/prompts/architecture.md | `14878481ace41b4ed6c5ef417239592af270253bd7ae6ffd3fb9bf4dee3fab5e` |
| asdlc/prompts/business-requirements.md | `c7969fc9f245a56acb550263ded1cd376123a4503cae0a07a62b7f55455bf7df` |
| asdlc/prompts/challenger.md | `80a0b0de8abcc1efc692440221316cd4402e545f0789413611692ee9f3696aad` |
| asdlc/prompts/development.md | `452fece6d156c800f584945489b38d05301559ecd46c9115eff6c87cebb6a832` |
| asdlc/prompts/discovery.md | `23968a8e2efcfcb0a5db5271ff4f9f3f26bb9e0e07cf96594f829da27e2d6bad` |
| asdlc/prompts/orchestrator.md | `76b88d661651ffa6d837fd49bf5cad02aa3ee98e9f7abf0923ec3aef8868f8ca` |
| asdlc/prompts/sprint-planning.md | `af933fb2ae216b73ea91cb6ad673a3042ce80dcb2bf8035939ea511b83611483` |
| asdlc/prompts/sprint-review.md | `0e1f5e6baa3e6f17f76f2463a973a362072511a83267a646320551ed607a6972` |
| asdlc/prompts/testing.md | `50c2f82971b2d8d614cc9994a6156d75197b28678d06c0995aecb270970ba6c2` |
| asdlc/schemas/approvals.json | `0189178663c1112eef78f471aee9201befecb7ca5b869f1c1d0c98ef97200a99` |
| asdlc/schemas/decisions.json | `a8cc4c19b4d8258c117eeb1f7f40b6cf1dfa0aa8559d440a40de094c14ea5790` |
| asdlc/schemas/pipeline-state.json | `884ae3d37706d5adddb02e37fcbf6b7ebf9410ed640adc66dfbf9d6cde947562` |
| asdlc/schemas/project-state.json | `15d20c53c5b397186a40ff66f1f71059953c465b21599f0794c449347c6d4edb` |
| asdlc/schemas/questions.json | `81fc57f18dbb511a9ea670082055a12b4720419bef0827388a2e5c6ceedb9e2b` |
| asdlc/schemas/raid.json | `2c32add575283dfc6d3bf0a296c18bacca2c8282bae6b01d8834558673ea8811` |
| asdlc/schemas/review-findings.json | `72db003171d5bf34d36ff60530067fd04615e69a55cad6acb87b22d2d1e3d8be` |
| asdlc/schemas/stage-result.json | `ca88c11275f586e22c967c283b1a7c1cd845b31413e2e0dadabc3080d4e5c95a` |
| asdlc/store.py | `002cf28e700694393717b11fe145684dd5a08c2dc1947477d7a467ad01e91c7a` |
| prompts/architecture.md | `14878481ace41b4ed6c5ef417239592af270253bd7ae6ffd3fb9bf4dee3fab5e` |
| prompts/business-requirements.md | `c7969fc9f245a56acb550263ded1cd376123a4503cae0a07a62b7f55455bf7df` |
| prompts/challenger.md | `80a0b0de8abcc1efc692440221316cd4402e545f0789413611692ee9f3696aad` |
| prompts/development.md | `452fece6d156c800f584945489b38d05301559ecd46c9115eff6c87cebb6a832` |
| prompts/discovery.md | `23968a8e2efcfcb0a5db5271ff4f9f3f26bb9e0e07cf96594f829da27e2d6bad` |
| prompts/orchestrator.md | `76b88d661651ffa6d837fd49bf5cad02aa3ee98e9f7abf0923ec3aef8868f8ca` |
| prompts/sprint-planning.md | `af933fb2ae216b73ea91cb6ad673a3042ce80dcb2bf8035939ea511b83611483` |
| prompts/sprint-review.md | `0e1f5e6baa3e6f17f76f2463a973a362072511a83267a646320551ed607a6972` |
| prompts/testing.md | `50c2f82971b2d8d614cc9994a6156d75197b28678d06c0995aecb270970ba6c2` |
| schemas/approvals.json | `0189178663c1112eef78f471aee9201befecb7ca5b869f1c1d0c98ef97200a99` |
| schemas/decisions.json | `a8cc4c19b4d8258c117eeb1f7f40b6cf1dfa0aa8559d440a40de094c14ea5790` |
| schemas/pipeline-state.json | `884ae3d37706d5adddb02e37fcbf6b7ebf9410ed640adc66dfbf9d6cde947562` |
| schemas/project-state.json | `15d20c53c5b397186a40ff66f1f71059953c465b21599f0794c449347c6d4edb` |
| schemas/questions.json | `81fc57f18dbb511a9ea670082055a12b4720419bef0827388a2e5c6ceedb9e2b` |
| schemas/raid.json | `2c32add575283dfc6d3bf0a296c18bacca2c8282bae6b01d8834558673ea8811` |
| schemas/review-findings.json | `72db003171d5bf34d36ff60530067fd04615e69a55cad6acb87b22d2d1e3d8be` |
| schemas/stage-result.json | `ca88c11275f586e22c967c283b1a7c1cd845b31413e2e0dadabc3080d4e5c95a` |
| tests/test_artifacts.py | `0dddeca174acde2d436ed7a2bde7d80b6110225549c58b045454afeae3a9709a` |
| tests/test_delivery.py | `3e5796136a0ce90ca59d6e15361bc48b215565316869f7f02de9149feb7a264a` |

## Additional executed-evidence finding — DEL5

Severity: high. Blocking: yes. Owner: copied-source test evidence. Disposition: open.

Independent probe used an approved test argv that changes app.py in the copied workspace from proposed value=1 to value=2, imports it and asserts value=2. Checks exit 0. Transaction.apply then writes the original proposed value=1 to the actual application, because execute_checks never verifies the checked copy still matches the candidate inventory. This is a correctness/version-binding failure even for trusted commands that perform source generation or automatic fixes; it is not a demand for an OS security boundary.

Requested resolution: verify candidate source bytes remain equal to the approved proposed inventory after checks (and between commands if relevant), rejecting source mutation with retained evidence, or explicitly model mutated output as another reviewed in-scope proposal. Do not label testing of changed copied source as evidence for different applied bytes. Add a mutation regression proving original target remains unchanged and the mismatch cannot pass.

DEL1–DEL4 repairs were supplied by the owner and are undergoing independent delta checks; this new finding keeps the current verdict changes required. The previous records and observed original failure evidence remain historical.

| Current DEL5 inspected target | SHA-256 |
|---|---|
| asdlc/delivery.py | `598489e51ca44bd1ca94efc5ab3bd674f195fb1631a0133cfa749df708a7566e` |
| asdlc/engine.py | `10fdac3e7c5cb3e2e6f92108d8694978ff200004462750e94b8e8d6858a49270` |

## Final correction review — additional question gate DEL6

Severity: high. Blocking: yes. Owner: delivery question/result routing. Disposition: open.

Independent reproduction after DEL1–DEL5 corrections: development dispatch with a complete worker result containing a blocking unanswered Q-rule and delivery={"changes":[]} raises GateError("Resolve delivery questions before applying code"). Canonical questions remain empty, status remains running and the dispatch remains pending. The built-in Codex adapter requires a delivery payload at development/testing, so omitting it does not offer a usable built-in question-only path.

Impact: a delivery worker missing a business rule cannot request a canonical short question round; user waiting ownership/status and question persistence are lost. Requested resolution: accept a question-only delivery result without source integration or test execution, persist its question/RAID and enter awaiting_input. Never apply proposed code when required answers are missing; explicitly reject or safely defer any mixed nonempty proposals. Add restart/answer/redispatch coverage and verify the existing repair budget is preserved.

DEL1–DEL5 corrected algorithms have been inspected and focused regression checks are passing; this newly reproduced gate gap keeps the verdict changes required pending correction and exact final review.

| DEL6 inspected target | SHA-256 |
|---|---|
| asdlc/engine.py | `a90caf9c5a27e1ed765f9ad013a155714cabcf0ac84d392eefa50939f344d197` |
| asdlc/adapters.py | `5014360af4496468cb5f9788de7363a279afb989d0dfa143471fc5f7f8ae9ef2` |
| asdlc/delivery.py | `598489e51ca44bd1ca94efc5ab3bd674f195fb1631a0133cfa749df708a7566e` |
| tests/test_delivery.py | `40921c1d78d9df7d6d484359620558ab355d72f5555839d5a8fd9656b3139ec5` |

## Final independent re-review — 6 October 2026

Verdict: **pass**, no unresolved material findings within this delivery increment. This verdict applies only to the complete-byte SHA-256 manifest below. It is independent implementation review, not human acceptance, publication authority or approval of a live project.

| Finding | Final disposition | Independent resolution evidence |
|---|---|---|
| DEL1 Windows protected-path aliases | Resolved | Trailing dot/space, reserved devices, invalid characters and protected resolved components refused; ordinary scoped delivery still applies. |
| DEL2 completed-write recovery | Resolved | Atomic replacements and completed mutation accounting restore the first file after injected second-write failure. Store action/save/recovery remains under its OS lock. Precommit canonical save failure rolls code back; independently injected postcommit view failure preserves saved code/result. |
| DEL3 upstream identity collision | Resolved | Inventory rejects upstream ID reuse before provenance/materialisation; distinct initiative/epic/story parents remain traceable. |
| DEL4 executed failure routing | Resolved | Development failures request owner correction; repeated independent failure probe reaches repair counts 0,1,2 then blocked and rejects further worker dispatch. Testing failure returns to development, retires accepted delivery states and preserves four approved upstream docs. Separate probe with an accepted development repair count of two returns blocked at two, also after restart. Failure results, decisions and RAID remain recorded; no approval appears. |
| DEL5 checked copy differs from delivered bytes | Resolved | Candidate originals must remain byte-identical after each command. Original probe now fails; separate newly-created extra.py probe also fails. Only Python/pytest cache additions are permitted. Actual checks and code_version are emitted as orchestrator evidence. |
| DEL6 blocking question cannot pause delivery | Resolved | Empty delivery changes with a question skips checks and writes, persists awaiting_input plus question/RAID, survives restart, and resumes worker dispatch after explicit answer. Nonempty mixed proposals/questions refused. Target bytes and approval list remain unchanged. |

### Final verification and preservation

Independent full command `.venv/Scripts/python.exe -m unittest discover -s tests -v`: **52 tests passed in 81.962 seconds** (stable-version run27162). Manifest capture immediately before the run and post-run recomputation matched all 48 files. The owner also retained a separate 52-test passing transcript at `.asdlc-local/delivery-final-tests.txt`; this report's pass is based on the independent run. Scoped prompt mirrors are covered by the suite. `git -c core.whitespace=cr-at-eol diff --check` passed; plain diff-check treats the existing Windows CRLF bytes as trailing whitespace. No global Git configuration was changed.

Earlier independent 49/50-test runs encountered transient Windows PermissionError replacing postcommit generated views. Their affected isolated test passed, and an independently injected postcommit failure retained canonical results/code. The final version adds a shared atomic replacement helper: transient PermissionError retries only the same replacement, up to five attempts with bounded delays; persistent error propagates with original destination preserved. Independent injected transient and persistent checks and the final regression both passed. An intermediate run spanning source edits failed a rearranged test with NameError; it is not evidence for the frozen final version.

The additional rejected-attempt callback receives the original exception, rolls back uncommitted code under the lock, and retains a structured rejection file for the active dispatch. Resume links that attempt without changing it into a successful result or approval. Final regression confirms this path. Postcommit callback detection preserves the committed result instead of treating rendering failure as uncommitted code.

Gate/state/code-binding checks cover stale revisions, exact dispatch identity, code drift invalidation, dirty source provenance, immutable materialisation tamper, failed test routing, repair caps, explicit answers, exact human-target approval/rejection and restart. Worker/reviewer prompts explicitly separate their verdicts and reserve orchestrator RAID prefixes. Reviewers cannot self-approve. No new human approval was created by this independent review. Fixture tests use explicitly synthetic approvals only.

### Scope limits

Approved test argv is trusted project code, and the copy is not an OS isolation boundary. The built-in adapter remains read-only and returns complete UTF-8 proposals; the orchestrator executes approved checks and applies scoped changes. Testing proposes no application writes. A test result establishes only its approved command coverage; it does not establish all business acceptance or nonfunctional properties. Rejection files are evidence, not canonical passes.

Real Codex sample execution was performed by the owner under separate user authorization; this reviewer does not relabel synthetic planning/fixture approvals as live human acceptance. Packaging a new wheel and broader use/publication require their own applicable validation/authorization; the earlier distribution report remains byte-specific to its original version. Prior lifecycle approvals and report bytes were preserved.

### Final exact manifest

All hashes cover complete on-disk bytes including line endings. Paths are relative to the ASDLC tool checkout.

| Target | SHA-256 |
|---|---|
| asdlc/adapters.py | `05346e13e9df04665441c42c268b25961772bba901a0fafefdb08bf49bfb3687` |
| asdlc/artifacts.py | `aa875db8fd67f590a90b3cd54913c55d98e226bcae58227e5bd6317e71301aa7` |
| asdlc/cli.py | `60fe1237951138de99b398c6d28cc6347d4c0d6d04831d7ba088c74e9d1d7133` |
| asdlc/code_version.py | `a17ef1a21f32247f12b12e9fade2c333cd318c8e27bde98e1521bfe8f8c76734` |
| asdlc/delivery.py | `6c692545042b685f3551cf9516944a229da5ef9ff596fa5ec9e165b4115984f8` |
| asdlc/engine.py | `8fb95d8db7f99c43f085b915c38775f368844dc19ee346102380a7e3f968e716` |
| asdlc/pipeline.py | `b40c75a2688fdb82a8b7382ae1adf9b6efc52ec41217b4030bc61f328603e5df` |
| asdlc/prompts/architecture.md | `14878481ace41b4ed6c5ef417239592af270253bd7ae6ffd3fb9bf4dee3fab5e` |
| asdlc/prompts/business-requirements.md | `c7969fc9f245a56acb550263ded1cd376123a4503cae0a07a62b7f55455bf7df` |
| asdlc/prompts/challenger.md | `80a0b0de8abcc1efc692440221316cd4402e545f0789413611692ee9f3696aad` |
| asdlc/prompts/development.md | `452fece6d156c800f584945489b38d05301559ecd46c9115eff6c87cebb6a832` |
| asdlc/prompts/discovery.md | `23968a8e2efcfcb0a5db5271ff4f9f3f26bb9e0e07cf96594f829da27e2d6bad` |
| asdlc/prompts/orchestrator.md | `76b88d661651ffa6d837fd49bf5cad02aa3ee98e9f7abf0923ec3aef8868f8ca` |
| asdlc/prompts/sprint-planning.md | `af933fb2ae216b73ea91cb6ad673a3042ce80dcb2bf8035939ea511b83611483` |
| asdlc/prompts/sprint-review.md | `0e1f5e6baa3e6f17f76f2463a973a362072511a83267a646320551ed607a6972` |
| asdlc/prompts/testing.md | `9ad46f8ee42f54ab9189bb3c2cc66540b6eb4df0dad47e54e0f914d1149d481a` |
| asdlc/schemas/approvals.json | `0189178663c1112eef78f471aee9201befecb7ca5b869f1c1d0c98ef97200a99` |
| asdlc/schemas/decisions.json | `a8cc4c19b4d8258c117eeb1f7f40b6cf1dfa0aa8559d440a40de094c14ea5790` |
| asdlc/schemas/pipeline-state.json | `884ae3d37706d5adddb02e37fcbf6b7ebf9410ed640adc66dfbf9d6cde947562` |
| asdlc/schemas/project-state.json | `15d20c53c5b397186a40ff66f1f71059953c465b21599f0794c449347c6d4edb` |
| asdlc/schemas/questions.json | `81fc57f18dbb511a9ea670082055a12b4720419bef0827388a2e5c6ceedb9e2b` |
| asdlc/schemas/raid.json | `2c32add575283dfc6d3bf0a296c18bacca2c8282bae6b01d8834558673ea8811` |
| asdlc/schemas/review-findings.json | `72db003171d5bf34d36ff60530067fd04615e69a55cad6acb87b22d2d1e3d8be` |
| asdlc/schemas/stage-result.json | `ca88c11275f586e22c967c283b1a7c1cd845b31413e2e0dadabc3080d4e5c95a` |
| asdlc/store.py | `32120284e9b96dc663166fb9e0aa4b461ec63c3ce6e0ba557ecc8eae68b92619` |
| examples/product_delivery.py | `cccd5560d71def808cc79b7b79df4d7411a7af4e7f35f96ef88ee23beca6ac7b` |
| prompts/architecture.md | `14878481ace41b4ed6c5ef417239592af270253bd7ae6ffd3fb9bf4dee3fab5e` |
| prompts/business-requirements.md | `c7969fc9f245a56acb550263ded1cd376123a4503cae0a07a62b7f55455bf7df` |
| prompts/challenger.md | `80a0b0de8abcc1efc692440221316cd4402e545f0789413611692ee9f3696aad` |
| prompts/development.md | `452fece6d156c800f584945489b38d05301559ecd46c9115eff6c87cebb6a832` |
| prompts/discovery.md | `23968a8e2efcfcb0a5db5271ff4f9f3f26bb9e0e07cf96594f829da27e2d6bad` |
| prompts/orchestrator.md | `76b88d661651ffa6d837fd49bf5cad02aa3ee98e9f7abf0923ec3aef8868f8ca` |
| prompts/sprint-planning.md | `af933fb2ae216b73ea91cb6ad673a3042ce80dcb2bf8035939ea511b83611483` |
| prompts/sprint-review.md | `0e1f5e6baa3e6f17f76f2463a973a362072511a83267a646320551ed607a6972` |
| prompts/testing.md | `9ad46f8ee42f54ab9189bb3c2cc66540b6eb4df0dad47e54e0f914d1149d481a` |
| pyproject.toml | `20648b711a09c6bdf3b9166608a4897d7329186971a6aa9c44283978858575c3` |
| schemas/approvals.json | `0189178663c1112eef78f471aee9201befecb7ca5b869f1c1d0c98ef97200a99` |
| schemas/decisions.json | `a8cc4c19b4d8258c117eeb1f7f40b6cf1dfa0aa8559d440a40de094c14ea5790` |
| schemas/pipeline-state.json | `884ae3d37706d5adddb02e37fcbf6b7ebf9410ed640adc66dfbf9d6cde947562` |
| schemas/project-state.json | `15d20c53c5b397186a40ff66f1f71059953c465b21599f0794c449347c6d4edb` |
| schemas/questions.json | `81fc57f18dbb511a9ea670082055a12b4720419bef0827388a2e5c6ceedb9e2b` |
| schemas/raid.json | `2c32add575283dfc6d3bf0a296c18bacca2c8282bae6b01d8834558673ea8811` |
| schemas/review-findings.json | `72db003171d5bf34d36ff60530067fd04615e69a55cad6acb87b22d2d1e3d8be` |
| schemas/stage-result.json | `ca88c11275f586e22c967c283b1a7c1cd845b31413e2e0dadabc3080d4e5c95a` |
| tests/test_artifacts.py | `539e4e435017105fed4ae7ef723c34d6a2f3721a5c68850ec108d595da5933ec` |
| tests/test_delivery.py | `6f6ec239b093119eddcfe99634147997c943074e5ebfea306fbac33d05845faf` |
| tests/test_pipeline.py | `c453e8a48d6c911285fdbf78ed7e705c7c416f1fe2b163bce62df71c1388689e` |
| tests/test_workflow.py | `1bc390a1d4376207f3d44faf740d82e15460b1db66e3555aa017e97dfe8f96aa` |

## Subsequent narrow delta — execution provenance and configured policy context

Current verdict remains **independent pass for the subsequent exact manifest below**, with no newly unresolved blocking findings. The earlier 52-test pass and its complete manifest remain historical evidence for that earlier byte version; they are not silently reassigned to this delta. No human approval is added. Only adapters.py and delivery.py changed among the 48 scoped targets.

### Reviewed behavior and evidence

Successful/exited subprocess evidence now records a fresh execution UUID, UTC timestamp, actual copy cwd, expanded argv, resolved executable, pre/post copied-source SHA-256 manifests, normalized full stdout/stderr SHA-256 and truncation flags. Independent two-command probe verified UUID and timestamp syntax, actual Python executable, pre/post source equality, ordinary output digest, and a 13,001-character output whose displayed tail is 12,000 characters but whose digest matches the complete decoded output. These are hashes of UTF-8-normalized captured text, not raw process output bytes.

Transaction.apply rechecks the complete nonignored target inventory against the tested candidate after all writes. Independent failure injection performed an external editor overwrite immediately after atomic integration; apply refused the final mismatch and no canonical result was recorded. Existing preservation/recovery rules still apply to genuinely concurrent external edits.

The Codex adapter supplies serial-exact-gates version1 as configured implementation policy, with actual input-bound repair_limit, repairs_consumed, current stage, correction accounting, final allowed review, exhaustion and explicit human gate. Prompt capture verified actual limit2 and consumed0 and the final-review rule. Code inspection confirms correction dispatch alone increments consumption; the last allowed correction can receive independent review, unresolved defects at cap hold, and exact current independent pass only enables human approval. There is no business-policy acceptance or invented consent in this text. This is runtime context; a broader retry/escalation policy contract remains future work.

Focused independent command with PYTHONPATH=tests: `python -m unittest test_delivery test_pipeline.PipelineTests.test_stage_prompt_and_approved_package_are_dispatched test_pipeline.PipelineTests.test_zero_repair_policy_holds_after_first_material_finding test_pipeline.PipelineTests.test_failure_keeps_dispatch_and_configurable_repairs_hold -v`: **14 tests passed in35.732 seconds**. Additional independent probes above validate the new provenance, output truncation and postintegration check beyond existing assertions. No implementation files were edited by the reviewer.

### Nonblocking evidence limit

Timeout/OSError catch entries currently retain command, unavailable exit code and exception type, without the prepared UUID/time/cwd/argv/source manifest or partial timeout output. They always raise CheckFailure and cannot support acceptance. Detailed provenance is therefore asserted for subprocesses that return a CompletedProcess, not every failed launch/timeout item. Extending unavailable-attempt metadata would improve diagnosis; this omission is not an approval bypass and does not reopen DEL1–DEL6.

### Subsequent exact manifest

This manifest supersedes the earlier final manifest only for the latest reviewed implementation bytes; all prior manifests remain untouched as provenance. Complete-byte SHA-256, including line endings. The separate snapshot is `.asdlc-local/delivery-review-provenance-policy-manifest.json`.

| Target | SHA-256 |
|---|---|
| asdlc/adapters.py | `a1d526f8fff8b9633358393b79a5ed45cd42fd736dce51c449c98de11c9659ca` |
| asdlc/artifacts.py | `aa875db8fd67f590a90b3cd54913c55d98e226bcae58227e5bd6317e71301aa7` |
| asdlc/cli.py | `60fe1237951138de99b398c6d28cc6347d4c0d6d04831d7ba088c74e9d1d7133` |
| asdlc/code_version.py | `a17ef1a21f32247f12b12e9fade2c333cd318c8e27bde98e1521bfe8f8c76734` |
| asdlc/delivery.py | `9f5a05e363c5229961235892d91b6938bd9d2a10251ecb64caf28d236e986a0d` |
| asdlc/engine.py | `8fb95d8db7f99c43f085b915c38775f368844dc19ee346102380a7e3f968e716` |
| asdlc/pipeline.py | `b40c75a2688fdb82a8b7382ae1adf9b6efc52ec41217b4030bc61f328603e5df` |
| asdlc/prompts/architecture.md | `14878481ace41b4ed6c5ef417239592af270253bd7ae6ffd3fb9bf4dee3fab5e` |
| asdlc/prompts/business-requirements.md | `c7969fc9f245a56acb550263ded1cd376123a4503cae0a07a62b7f55455bf7df` |
| asdlc/prompts/challenger.md | `80a0b0de8abcc1efc692440221316cd4402e545f0789413611692ee9f3696aad` |
| asdlc/prompts/development.md | `452fece6d156c800f584945489b38d05301559ecd46c9115eff6c87cebb6a832` |
| asdlc/prompts/discovery.md | `23968a8e2efcfcb0a5db5271ff4f9f3f26bb9e0e07cf96594f829da27e2d6bad` |
| asdlc/prompts/orchestrator.md | `76b88d661651ffa6d837fd49bf5cad02aa3ee98e9f7abf0923ec3aef8868f8ca` |
| asdlc/prompts/sprint-planning.md | `af933fb2ae216b73ea91cb6ad673a3042ce80dcb2bf8035939ea511b83611483` |
| asdlc/prompts/sprint-review.md | `0e1f5e6baa3e6f17f76f2463a973a362072511a83267a646320551ed607a6972` |
| asdlc/prompts/testing.md | `9ad46f8ee42f54ab9189bb3c2cc66540b6eb4df0dad47e54e0f914d1149d481a` |
| asdlc/schemas/approvals.json | `0189178663c1112eef78f471aee9201befecb7ca5b869f1c1d0c98ef97200a99` |
| asdlc/schemas/decisions.json | `a8cc4c19b4d8258c117eeb1f7f40b6cf1dfa0aa8559d440a40de094c14ea5790` |
| asdlc/schemas/pipeline-state.json | `884ae3d37706d5adddb02e37fcbf6b7ebf9410ed640adc66dfbf9d6cde947562` |
| asdlc/schemas/project-state.json | `15d20c53c5b397186a40ff66f1f71059953c465b21599f0794c449347c6d4edb` |
| asdlc/schemas/questions.json | `81fc57f18dbb511a9ea670082055a12b4720419bef0827388a2e5c6ceedb9e2b` |
| asdlc/schemas/raid.json | `2c32add575283dfc6d3bf0a296c18bacca2c8282bae6b01d8834558673ea8811` |
| asdlc/schemas/review-findings.json | `72db003171d5bf34d36ff60530067fd04615e69a55cad6acb87b22d2d1e3d8be` |
| asdlc/schemas/stage-result.json | `ca88c11275f586e22c967c283b1a7c1cd845b31413e2e0dadabc3080d4e5c95a` |
| asdlc/store.py | `32120284e9b96dc663166fb9e0aa4b461ec63c3ce6e0ba557ecc8eae68b92619` |
| examples/product_delivery.py | `cccd5560d71def808cc79b7b79df4d7411a7af4e7f35f96ef88ee23beca6ac7b` |
| prompts/architecture.md | `14878481ace41b4ed6c5ef417239592af270253bd7ae6ffd3fb9bf4dee3fab5e` |
| prompts/business-requirements.md | `c7969fc9f245a56acb550263ded1cd376123a4503cae0a07a62b7f55455bf7df` |
| prompts/challenger.md | `80a0b0de8abcc1efc692440221316cd4402e545f0789413611692ee9f3696aad` |
| prompts/development.md | `452fece6d156c800f584945489b38d05301559ecd46c9115eff6c87cebb6a832` |
| prompts/discovery.md | `23968a8e2efcfcb0a5db5271ff4f9f3f26bb9e0e07cf96594f829da27e2d6bad` |
| prompts/orchestrator.md | `76b88d661651ffa6d837fd49bf5cad02aa3ee98e9f7abf0923ec3aef8868f8ca` |
| prompts/sprint-planning.md | `af933fb2ae216b73ea91cb6ad673a3042ce80dcb2bf8035939ea511b83611483` |
| prompts/sprint-review.md | `0e1f5e6baa3e6f17f76f2463a973a362072511a83267a646320551ed607a6972` |
| prompts/testing.md | `9ad46f8ee42f54ab9189bb3c2cc66540b6eb4df0dad47e54e0f914d1149d481a` |
| pyproject.toml | `20648b711a09c6bdf3b9166608a4897d7329186971a6aa9c44283978858575c3` |
| schemas/approvals.json | `0189178663c1112eef78f471aee9201befecb7ca5b869f1c1d0c98ef97200a99` |
| schemas/decisions.json | `a8cc4c19b4d8258c117eeb1f7f40b6cf1dfa0aa8559d440a40de094c14ea5790` |
| schemas/pipeline-state.json | `884ae3d37706d5adddb02e37fcbf6b7ebf9410ed640adc66dfbf9d6cde947562` |
| schemas/project-state.json | `15d20c53c5b397186a40ff66f1f71059953c465b21599f0794c449347c6d4edb` |
| schemas/questions.json | `81fc57f18dbb511a9ea670082055a12b4720419bef0827388a2e5c6ceedb9e2b` |
| schemas/raid.json | `2c32add575283dfc6d3bf0a296c18bacca2c8282bae6b01d8834558673ea8811` |
| schemas/review-findings.json | `72db003171d5bf34d36ff60530067fd04615e69a55cad6acb87b22d2d1e3d8be` |
| schemas/stage-result.json | `ca88c11275f586e22c967c283b1a7c1cd845b31413e2e0dadabc3080d4e5c95a` |
| tests/test_artifacts.py | `539e4e435017105fed4ae7ef723c34d6a2f3721a5c68850ec108d595da5933ec` |
| tests/test_delivery.py | `6f6ec239b093119eddcfe99634147997c943074e5ebfea306fbac33d05845faf` |
| tests/test_pipeline.py | `c453e8a48d6c911285fdbf78ed7e705c7c416f1fe2b163bce62df71c1388689e` |
| tests/test_workflow.py | `1bc390a1d4376207f3d44faf740d82e15460b1db66e3555aa017e97dfe8f96aa` |

## Final narrow completion — unavailable execution provenance

Latest verdict: **independent pass** for the exact manifest below. The preceding nonblocking failure-only provenance observation is resolved. Earlier observations and manifests remain historical; no human acceptance is inferred.

Code inspection and independent injected TimeoutExpired/OSError probes confirm each unavailable execution record now retains prepared UUID, timestamp, cwd, expanded argv, resolved executable, source_before/source_after, exception type and null exit code. Partial timeout stdout/stderr is decoded with explicit replacement and retained with full normalized-text hashes and truncation flags. A 13,001-byte timeout stdout produced a 12,000-character tail with its complete hash; invalid UTF-8 stderr matched its normalized replacement-text hash. OSError produced empty-output hashes. Both raised CheckFailure; neither became a pass. Mutation diagnostic entries are supplementary diagnostics, not separate process executions.

Post-repair focused independent tests for scoped application/check recording, failed-check preservation and test-source mutation all passed: **3 tests in9.620 seconds**. The earlier focused14 run and explicit policy/provenance/postwrite probes remain applicable to their recorded scope. Full52 historical suite evidence remains tied to its original manifest; the owner is separately rerunning the whole suite for current packaging. Review does not approve a wheel built later.

The full 48-target snapshot is `.asdlc-local/delivery-review-provenance-final-manifest.json`. It covers all frozen delivery/runtime/schema/prompt/test/example/pyproject targets. Recomputed hashes matched immediately before this append. The snapshot matches the preceding manifest because the failure metadata repair was already present by that snapshot capture; the earlier limitation text recorded the earlier inspected exception branch and is superseded by the explicit post-repair probe above.

| Latest reviewed target | SHA-256 |
|---|---|
| asdlc/adapters.py | `a1d526f8fff8b9633358393b79a5ed45cd42fd736dce51c449c98de11c9659ca` |
| asdlc/artifacts.py | `aa875db8fd67f590a90b3cd54913c55d98e226bcae58227e5bd6317e71301aa7` |
| asdlc/cli.py | `60fe1237951138de99b398c6d28cc6347d4c0d6d04831d7ba088c74e9d1d7133` |
| asdlc/code_version.py | `a17ef1a21f32247f12b12e9fade2c333cd318c8e27bde98e1521bfe8f8c76734` |
| asdlc/delivery.py | `9f5a05e363c5229961235892d91b6938bd9d2a10251ecb64caf28d236e986a0d` |
| asdlc/engine.py | `8fb95d8db7f99c43f085b915c38775f368844dc19ee346102380a7e3f968e716` |
| asdlc/pipeline.py | `b40c75a2688fdb82a8b7382ae1adf9b6efc52ec41217b4030bc61f328603e5df` |
| asdlc/prompts/architecture.md | `14878481ace41b4ed6c5ef417239592af270253bd7ae6ffd3fb9bf4dee3fab5e` |
| asdlc/prompts/business-requirements.md | `c7969fc9f245a56acb550263ded1cd376123a4503cae0a07a62b7f55455bf7df` |
| asdlc/prompts/challenger.md | `80a0b0de8abcc1efc692440221316cd4402e545f0789413611692ee9f3696aad` |
| asdlc/prompts/development.md | `452fece6d156c800f584945489b38d05301559ecd46c9115eff6c87cebb6a832` |
| asdlc/prompts/discovery.md | `23968a8e2efcfcb0a5db5271ff4f9f3f26bb9e0e07cf96594f829da27e2d6bad` |
| asdlc/prompts/orchestrator.md | `76b88d661651ffa6d837fd49bf5cad02aa3ee98e9f7abf0923ec3aef8868f8ca` |
| asdlc/prompts/sprint-planning.md | `af933fb2ae216b73ea91cb6ad673a3042ce80dcb2bf8035939ea511b83611483` |
| asdlc/prompts/sprint-review.md | `0e1f5e6baa3e6f17f76f2463a973a362072511a83267a646320551ed607a6972` |
| asdlc/prompts/testing.md | `9ad46f8ee42f54ab9189bb3c2cc66540b6eb4df0dad47e54e0f914d1149d481a` |
| asdlc/schemas/approvals.json | `0189178663c1112eef78f471aee9201befecb7ca5b869f1c1d0c98ef97200a99` |
| asdlc/schemas/decisions.json | `a8cc4c19b4d8258c117eeb1f7f40b6cf1dfa0aa8559d440a40de094c14ea5790` |
| asdlc/schemas/pipeline-state.json | `884ae3d37706d5adddb02e37fcbf6b7ebf9410ed640adc66dfbf9d6cde947562` |
| asdlc/schemas/project-state.json | `15d20c53c5b397186a40ff66f1f71059953c465b21599f0794c449347c6d4edb` |
| asdlc/schemas/questions.json | `81fc57f18dbb511a9ea670082055a12b4720419bef0827388a2e5c6ceedb9e2b` |
| asdlc/schemas/raid.json | `2c32add575283dfc6d3bf0a296c18bacca2c8282bae6b01d8834558673ea8811` |
| asdlc/schemas/review-findings.json | `72db003171d5bf34d36ff60530067fd04615e69a55cad6acb87b22d2d1e3d8be` |
| asdlc/schemas/stage-result.json | `ca88c11275f586e22c967c283b1a7c1cd845b31413e2e0dadabc3080d4e5c95a` |
| asdlc/store.py | `32120284e9b96dc663166fb9e0aa4b461ec63c3ce6e0ba557ecc8eae68b92619` |
| examples/product_delivery.py | `cccd5560d71def808cc79b7b79df4d7411a7af4e7f35f96ef88ee23beca6ac7b` |
| prompts/architecture.md | `14878481ace41b4ed6c5ef417239592af270253bd7ae6ffd3fb9bf4dee3fab5e` |
| prompts/business-requirements.md | `c7969fc9f245a56acb550263ded1cd376123a4503cae0a07a62b7f55455bf7df` |
| prompts/challenger.md | `80a0b0de8abcc1efc692440221316cd4402e545f0789413611692ee9f3696aad` |
| prompts/development.md | `452fece6d156c800f584945489b38d05301559ecd46c9115eff6c87cebb6a832` |
| prompts/discovery.md | `23968a8e2efcfcb0a5db5271ff4f9f3f26bb9e0e07cf96594f829da27e2d6bad` |
| prompts/orchestrator.md | `76b88d661651ffa6d837fd49bf5cad02aa3ee98e9f7abf0923ec3aef8868f8ca` |
| prompts/sprint-planning.md | `af933fb2ae216b73ea91cb6ad673a3042ce80dcb2bf8035939ea511b83611483` |
| prompts/sprint-review.md | `0e1f5e6baa3e6f17f76f2463a973a362072511a83267a646320551ed607a6972` |
| prompts/testing.md | `9ad46f8ee42f54ab9189bb3c2cc66540b6eb4df0dad47e54e0f914d1149d481a` |
| pyproject.toml | `20648b711a09c6bdf3b9166608a4897d7329186971a6aa9c44283978858575c3` |
| schemas/approvals.json | `0189178663c1112eef78f471aee9201befecb7ca5b869f1c1d0c98ef97200a99` |
| schemas/decisions.json | `a8cc4c19b4d8258c117eeb1f7f40b6cf1dfa0aa8559d440a40de094c14ea5790` |
| schemas/pipeline-state.json | `884ae3d37706d5adddb02e37fcbf6b7ebf9410ed640adc66dfbf9d6cde947562` |
| schemas/project-state.json | `15d20c53c5b397186a40ff66f1f71059953c465b21599f0794c449347c6d4edb` |
| schemas/questions.json | `81fc57f18dbb511a9ea670082055a12b4720419bef0827388a2e5c6ceedb9e2b` |
| schemas/raid.json | `2c32add575283dfc6d3bf0a296c18bacca2c8282bae6b01d8834558673ea8811` |
| schemas/review-findings.json | `72db003171d5bf34d36ff60530067fd04615e69a55cad6acb87b22d2d1e3d8be` |
| schemas/stage-result.json | `ca88c11275f586e22c967c283b1a7c1cd845b31413e2e0dadabc3080d4e5c95a` |
| tests/test_artifacts.py | `539e4e435017105fed4ae7ef723c34d6a2f3721a5c68850ec108d595da5933ec` |
| tests/test_delivery.py | `6f6ec239b093119eddcfe99634147997c943074e5ebfea306fbac33d05845faf` |
| tests/test_pipeline.py | `c453e8a48d6c911285fdbf78ed7e705c7c416f1fe2b163bce62df71c1388689e` |
| tests/test_workflow.py | `1bc390a1d4376207f3d44faf740d82e15460b1db66e3555aa017e97dfe8f96aa` |
