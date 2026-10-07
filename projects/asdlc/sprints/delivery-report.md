---
project_id: asdlc
artifact_id: REPORT-DELIVERY-001
status: draft-awaiting-independent-report-review
human_acceptance: pending
---

# Scoped product delivery increment

ASDLC v0.2.0 now turns an approved sprint into checked application files and executed test evidence. Codex proposes complete UTF-8 file changes in a read-only session; the orchestrator alone validates and integrates them. Initiative, epic and story inventories also produce separate generated project documents.

## Delivered behaviour

- An approved sprint supplies exact write paths and test argument arrays in an `asdlc-delivery` contract. File proposals carry existing-byte hashes; new files use null. Missing scope, stale code, ignored new files, protected metadata, Windows aliases and links are refused.
- Approved checks execute on a separate source copy before integration. Original source hashes must remain unchanged; unapproved output files are refused, with disposable Python/pytest caches allowed. Evidence records execution identity/time, working directory, resolved executable, actual arguments, pre/post source hashes, exit status and output hashes/truncation flags.
- Matching proposals integrate under the canonical project lock, with atomic replacement of each file. Raised partial-write failures roll back completed writes while preserving concurrent edits. Canonical commit followed by a view failure retains recorded code and regenerates views on resume. Brief Windows sharing violations receive bounded atomic-replacement retries; persistent errors still fail.
- Development test failures retain result/decision/RAID evidence and return to bounded owner correction. Integrated-test failure retires affected delivery authority and returns to development with its consumed budget. Exhaustion holds. Question-only results pause without executing tests or changing code. Rejected structured results remain inspectable on resume.
- `asdlc-artifacts` inventories materialise initiatives, epics and stories with stable IDs, parent checks, generated views and immutable content versions. Upstream identities cannot be reused for another artifact. The enclosing stage approval binds the inventory; individual files never self-approve.
- Workers/reviewers receive explicit role constraints and the configured versioned serial retry/gate rule. The cap remains init-configurable and input-bound; implementation defaults do not establish business consent or delegated acceptance.

## Verification

[Exact source/test/package evidence](evidence/delivery-test-run.json): **52 tests passed** on the final 48-file reviewed manifest. [Independent code review](../reviews/delivery-review.md) passed after resolving six material findings around paths, rollback, identity, correction routing, source mutation and question handling. Additional provenance/policy probes passed. Earlier transient Windows failures and superseded manifests remain recorded.

[Sample evidence](evidence/product-delivery-sample.json): a separate calculator application completed seven gate pauses and process restarts, produced initiative/epic/story views, generated application/test files and executed checks. **Development, testing and sprint-review workers and independent reviewers used actual installed Codex.** Earlier-stage documents/reviews and **all approval actors were synthetic**; this is not live human acceptance or a fully real Codex discovery-to-acceptance run.

An earlier real sample exhausted its testing correction budget because execution-copy provenance and policy context were insufficient. It remains blocked and preserved. The repaired implementation passed a fresh sample; no exhausted budget was reset to manufacture a pass.

[Fresh installation](evidence/delivery-install.json): the wheel installed into a separate Python environment and loaded bundled contracts from a separate application directory. That installation probe uses a synthetic adapter. Wheel SHA-256: `bf1c3461f08cd5a758fa306fc46e8d5299677d7a5fe0a3cfe93923f75e8fd02b`.

## Limits and acceptance boundary

This is serial, local, exact-file UTF-8 delivery with already-available test dependencies. Binary changes, submodule operations, dependency installation, source-generating builds, legacy-state migration, concurrency and broader conditional/delegated policy remain separate work. Test commands are trusted project code; a copied source tree is not an OS security boundary. Passing commands require independent assessment of coverage and sufficiency.

There is no durable multi-file rollback journal or shared application lock across different projects. Abrupt termination during integration can require manual reconciliation of partial source changes; stale source is refused by the built-in delivery path rather than automatically accepted. Operate one project against a target at a time. Stronger crash recovery remains outstanding.

No real business project was activated, no live stage approval fabricated, and no push, merge, deployment or global configuration change performed. Existing lifecycle/operator approvals remain unchanged. This new increment requires exact-version human acceptance after its independent report review.
