# Runtime state contract

The sole canonical runtime record is `../state.json` at the project root. It is created by ASDLC `init`, not copied from a JSON template. [Project schema](../../../schemas/project-state.json) defines its exact structure. `state/` is explanatory documentation, not a second database.

- Schema version: integer 1. Serial discovery only is currently executable.
- Collections: questions, decisions, RAID, approvals, traceability, results, artifact and review histories.
- Current fields: revision, status, input_hash, artifact, review, dispatch, repairs, inputs and config.
- `results` holds accepted submissions; no separate events.json exists in this runtime.
- Stage values/statuses in later Markdown templates are plans, not new runtime enum values.
- Hashes use canonical JSON SHA-256 through the tool; do not manually substitute file SHA-256 for content hashes.
- CLI mutations require expected revision; result submission requires the assigned dispatch/revision/input hash.
- Kernel lock, atomic commit and schema/provenance validation belong to the orchestrator.

`project-status.md` and `raid.md` become generated views once init is explicitly authorised. Before init, their marked draft templates may be edited. Archive human draft versions before activation; the runtime generates those two files. Init does not create business approvals. Resume regenerates views and invalidates changed shared inputs.

Do not hand-edit state.json or create plausible-looking approvals. Markdown decisions/reviews are evidence artifacts, not canonical mutations. Apply records using ASDLC commands only. [Project home](../index.md).
