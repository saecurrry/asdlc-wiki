---
project_id: asdlc
status: draft
---

# ASDLC RAID

Editable documentation bootstrap; no canonical runtime records activated.

- **WIKI-I01 (issue, closed)**: templates now use the existing project-root state.json contract and exact runtime schemas. Earlier split drafts are archived; runtime code and historical baseline are preserved. No live initialisation performed.
- **WIKI-D01 (dependency, open)**: requirements, architecture and backlog need their separate exact-version human gates before live delivery. Foundation report acceptance is now recorded; it does not waive those gates.

[Project home](index.md)

- **WIKI-D02 (dependency, closed)**: foundation report approval received from the user on 5 October 2026. [Exact target/evidence and scope](approvals/foundation-report-approval.md).

- **DESIGN-I01 (issue, closed)**: prior reviews do not cover revised full-pipeline design. Owner ASDLC agent; independent challenge passed after correcting two material gaps; [exact report](reviews/design-update-review.md). Business acceptance remains separate.
- **DESIGN-D01 (dependency, open)**: stage approval/conditional-advancement and configurable retry policy need concrete reviewed options. Owner business owner when an actual package is presented; not a current request to repeat requirements.
- **DESIGN-R01 (risk, open)**: illustrative state/templates could be mistaken for executable pipeline. Owner ASDLC agent; schema explicitly marks examples illustrative; runtime v1 unchanged.

- **DESIGN-D02 (dependency, closed)**: existing updated design package approved by the user: [exact acceptance](approvals/design-update-approval.md). Implementation policy/scope remain separate.

- **ARTIFACT-I01 (issue, open)**: populated project initiative and epic documents are absent; table summaries/templates exist. Owner ASDLC agent; create I1–I3/E1–E6 records and submit applicable review before marking them accepted.

- **PRODUCT-I01 (issue, open)**: supplied package appears oriented to developing ASDLC rather than running a user business project. Owner ASDLC agent; correct operator onboarding/package boundary and deliver/validate all-stage project execution. Source/templates alone do not establish product readiness.

- **LIFECYCLE-D01 (dependency, open)**: serial lifecycle increment is implemented and independently reviewed, awaiting actual human acceptance of [exact report/evidence](approvals/lifecycle-review-request.md). Owner user; no approval recorded.
- **LIFECYCLE-I01 (issue, open)**: built-in adapter remains read-only; actual scoped coding/test workers, artifact splitting and full project distribution remain agent-owned implementation work.


## DEL-RECOVERY-001 — source integration recovery

Kind: risk. Status: open. Owner: ASDLC agent. Source: [delivery increment limits](sprints/delivery-report.md#limits-and-acceptance-boundary).

Raised 6 October 2026. Per-file replacements are atomic and raised failures roll back under the canonical lock; abrupt termination can leave partial application changes because no durable multi-file journal exists. Different projects do not share an application lock. Operate one project per target and inspect/reconcile source after interruption. Next implementation should add reviewed write-ahead recovery and target ownership before broader unattended use. No implicit live-project acceptance.
