# Agent operating instructions for the ASDLC wiki

This wiki is the persistent documentation and knowledge workspace for ASDLC agents. Use it proactively during authorised project work; the user may browse it in Obsidian. Do not rely on chat history as workflow state.

## Start and resume

1. Read the wiki README, this file, CONTRIBUTING, and only the target project's index/status.
2. If project-root state.json exists, load and validate it through the ASDLC orchestrator; it is authoritative. Markdown is a view/source artifact, never a substitute for gate checks.
3. If no runtime state exists, treat status/RAID as explicitly marked editable drafts. Do not invent execution records or initialise/overwrite them without authorised scope.
4. Reconcile exact source/artifact/code versions, pending questions/findings, approvals and next permitted action. A changed source needs invalidation and impact assessment.
5. Retrieve applicable standards/patterns and narrowly relevant knowledge. Record entry IDs, versions and approval/review status. Do not load the entire vault.

ASDLC's supplied requirements are already established. Do not restart its business discovery because a new chat or wiki connection occurred. Future projects use short question rounds for genuinely unknown intent.

## Storage and ownership

Canonical runtime data is projects/<id>/state.json, schema version 1, created by the tool. state/ documents the contract; legacy split JSON templates are archived and never executable. Current runtime executes serial discovery only. Later-stage Markdown contracts do not enable later-stage dispatch.

Only the orchestrator writes canonical state, approval records, transitions and generated project-status.md/raid.md. Workers return structured proposals; reviewers return findings. Use schema/revision/dispatch/digest checks and a kernel lock; never make direct JSON edits to bypass a gate. Archive human draft views before authorised init replaces them. Preserve previous source artifacts/reviews/evidence; do not overwrite historical baselines.

## Writing and retrieval

Use templates/ for focused artifact contracts. Use stable IDs, YAML frontmatter, portable relative links and Mermaid for useful diagrams. Keep facts, proposed assumptions, unknowns and decisions visibly distinct. Document required inputs, permitted actions, outputs, evidence and exit criteria. Link outcome → requirement → epic → story → test → exact change. Document dates only when the event actually happened.

For stage corrections, supply approved inputs and previous draft/findings explicitly as historical context; never treat stale artifacts as current approvals. Reviewers may pass with no findings. Material findings return to the owner; missing business choices return to the human. Two automatic repair rounds maximum, then escalate unresolved material findings. Author completion and reviewer pass never imply human acceptance.

## Knowledge maintenance

Record concrete project lessons first. Propose shared knowledge/patterns with evidence, applicability, limits, alternatives and revisit triggers. Independently challenge before promotion. Mandatory standards require recorded human owner approval of the exact entry version; unapproved index content is not a mandatory standard. Update folder indexes and preserve superseded entries with replacement links. Failed experiments are useful when honestly bounded.

## Git and publication

Preserve existing local work; inspect status before edits and reconcile concurrent changes. Follow explicit user/session permissions. Local edits do not imply push/merge/deploy authority. Branch/PR practices apply when publication is authorised. Do not change global machine configuration. This repo is public: keep credentials, private personal/confidential data and sensitive operational details out of publishable records.
