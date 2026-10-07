---
project_id: asdlc
artifact_id: REPORT-DISTRIBUTION-001
status: accepted
human_acceptance: approved
---

# Installed operator assets

Accepted on 6 October 2026: [exact approval record](../approvals/distribution-approval.md). The original presented bytes are retained by that record; this header is the accepted presentation.

The installed CLI previously resolved default specialist prompts from the current directory. It now uses nine bundled operator contracts, so a new business application can invoke ASDLC without copying the framework's development backlog or running from its checkout. Explicit prompt-directory overrides remain available.

The wheel includes runtime code, schemas and prompts. A separate Python environment installed it, initialised schema v2 against a separate synthetic application/wiki, and loaded the installed discovery contract from that application's directory. The probe substitutes a synthetic result adapter: it does not invoke Codex, approve a live gate or deliver application code.

Evidence: [clean installation](evidence/distribution-install.json), [exact source manifest and 38 passing regression tests](evidence/distribution-source-manifest.json), [independent packaging review](../reviews/distribution-review.md). Wheel SHA-256: `3b6a8090f12696d7fdaa224d103e89a477923c177b43c05e7b0221375b02a1ec`.

The root prompt sources and packaged copies are checked for exact byte equality. The historical v1 contract generator now refuses to overwrite current v2 contracts. Build outputs remain local and ignored.

Remaining product readiness work: scoped coding/test workers, separate initiative/epic/story outputs, a full independently challenged product demonstration and legacy migration. The previous exact lifecycle review/approval request remains a separate historical package; this increment changes installed prompt resolution and requires its own acceptance. Local implementation continues under the current user brief. No publication or live activation performed.
