# Wiki structure and document ownership

| Location | Purpose | How to use / change |
|---|---|---|
| README.md | Entry point | Start with current project/status and this map |
| projects/<id>/index.md and build-plan.md | Current project navigation and living plan | Resume current evidence, blockers and next permitted action |
| Project discovery/, requirements/, architecture/, backlog/, sprints/ | Current working artifacts; default reading/editing locations | Use exact versions, review independently and record separate human gates |
| Project decisions/, reviews/, approvals/, lessons/ | Decision and evidence registers | Preserve attribution and history; add records to indexes |
| Project state.json | Discovery runtime canonical record after init | Orchestrator/schema/revision/lock only; do not edit manually |
| Project state/ | Contract notes and inert legacy references | Never treat legacy split templates as executable state |
| Commit-specific Git links | Exact historical source versions for approval and review provenance | Resolve the recorded commit and verify the recorded hashes |
| standards/ | Mandatory obligations after recorded owner approval | Unapproved proposals/indexes are not mandatory standards |
| patterns/ | Reviewed reusable approaches | Record applicability, evidence and limitations |
| knowledge/ | Reviewed learning for reuse | Capture project lessons first; challenge before promotion |
| templates/ | Current reusable artifact contracts | Copy to new projects; never activate state by copying JSON |
| schemas/ | Exact runtime contracts and provenance | Upgrade from an explicitly reviewed runtime version |
| .obsidian/ | User's local vault configuration | Preserve personal settings; not workflow state |

Keep one current project home and living plan. Indexes link to source artifacts rather than duplicating mutable documents. Historical Git versions can contain older status wording: current status and later exact-version approvals establish the current position. Dead links or unknown owners remain explicit work, not invented facts.

Use standard relative Markdown links and stable IDs. Current runtime only executes serial discovery; later stage documents are planning contracts. Git publication and human acceptance are separate actions. [Home](README.md).

For ASDLC, use [current requirements](projects/asdlc/requirements/requirements.md), [HLD](projects/asdlc/architecture/hld.md), [backlog](projects/asdlc/backlog/backlog.md) and [full foundation report](projects/asdlc/sprints/foundation-report.md). Historical approval and review versions are linked to fixed Git commits; current documents live in these stage folders.
