# Contributing and learning

## Proposed contributions

Use a branch and pull request for shared standards, patterns and reusable knowledge. Describe the problem, evidence, applicability, limitations and validation. Keep standard ownership separate from agent judgement.

## Learning lifecycle

1. Capture a lesson under projects/<project-id>/lessons/ with source and evidence.
2. Propose a reusable entry using [the knowledge template](templates/knowledge-entry.md).
3. Independently challenge accuracy, scope, duplication and contradictions.
4. Record review; obtain owner approval for mandatory standards; merge the contribution.
5. Maintain review dates and mark superseded entries with a replacement link.

Statuses: proposed, reviewed, deprecated. Reviewed means the recorded review passed; it does not imply universal applicability. Record human approval separately when required. A failed experiment may be useful knowledge when its limitations are explicit.

## Content conventions

Use lowercase hyphenated filenames, stable IDs, YAML frontmatter and relative Markdown links. Add new entries to their folder index. Each entry has one clear purpose. Use Mermaid for diagrams where useful. Link evidence to exact repository revisions or artifact hashes.

## Project state

The sole canonical runtime record is projects/<id>/state.json, conforming to the version 1 tool schema. state/ contains contract documentation; legacy split records are archived, inert references. Initialise through ASDLC, never by filling a JSON template. Current runtime implements discovery only; later-stage documents remain planning contracts. Markdown explains and summarises canonical data. Do not manually change generated status/RAID after integration without updating the canonical records through the orchestrator. Pre-init status/RAID drafts are editable and clearly labelled; archive them before authorised init replaces them with generated views. Source documents remain separately editable. See [template guide](templates/index.md) and [schema contract](schemas/index.md).

## Concurrent edits

Pull before editing; use isolated branches for worker contributions. Reconcile changes before publishing. Never resolve conflicts by discarding another writer's decisions or evidence. Git commits version documents; they do not by themselves constitute business approval.
