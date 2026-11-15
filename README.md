# Worldview Infrastructure Intelligence (WII)

**The Intelligence Layer for the World's Infrastructure.**

WII is a geographically anchored infrastructure intelligence platform. Its primary interface is a navigable world map; its content is the evidence-backed intelligence associated with locations, infrastructure assets, engineering documents, construction activity, inspections, workforce accomplishments, and infrastructure history.

## Core interaction

**Select a location → inspect infrastructure → select an asset → open source documents → compare documented, reconstructed, and observed conditions → trace relationships and history → review work, inspection, schedule, and recognition records.**

## Foundational principles

1. **CLONE BEFORE COMPOSITION.** Existing work is preserved as an immutable source snapshot before integration or modification.
2. Preserve originals; create derivatives separately.
3. Discovery is not acquisition. Acquisition is not verification. Verification is not qualification or ratification.
4. Unknown, unavailable, inaccessible, disputed, and not-measured states remain explicit.
5. Visual presentation must never imply stronger evidence than the underlying source supports.
6. Accountability is evidence-based and two-sided: document deficiencies and recognize excellent work.
7. Protect critical infrastructure information, worker privacy, and source-specific access rights.
8. The platform complements, but does not replace, 811 notification, utility locating, permits, inspections, engineering approval, or excavation clearance.

## Architecture

- `docs/PLATFORM-ARCHITECTURE.md` — platform vision and system boundaries.
- `docs/SYSTEM-REGISTER.md` — proposed subsystem register.
- `docs/UNIVERSAL-CONSTRUCTION-WORK-RECORD.md` — shared work, contractor, asset, inspection, deficiency, and schedule record model.
- `docs/EVIDENCE-AND-PROVENANCE.md` — evidence states, provenance, lineage, and verification.
- `docs/SECURITY-PRIVACY-AND-ACCESS.md` — access, sensitive infrastructure, and workforce privacy.
- `docs/CLONE-BEFORE-COMPOSITION.md` — source preservation and integration protocol.
- `docs/ROADMAP.md` — staged implementation plan.
- `source-clones/` — preserved copies of existing Worldview work, kept isolated from the new application until reviewed.

## Status discipline

This repository distinguishes **PROPOSED**, **DISCOVERED**, **ACQUIRED**, **PRESERVED**, **IMPLEMENTED**, **TESTED**, **INDEPENDENTLY_VERIFIED**, **QUALIFIED**, and **HUMAN_RATIFIED**. No planned feature is represented as implemented merely because it appears in the architecture.

## Initial source lineage

The first preserved source is the creator's `Evank253/kcn-worldview-command-center` repository, branch `Python-3`, commit `2261e9344a079d2f6d622d944c5b0a431bac1aa1`. Its existing Worldview application and supporting files are copied under `source-clones/kcn-worldview-command-center/` with source paths and blob hashes recorded in the source manifest. The original repository is not modified.

## Working rule

**CLONE BEFORE COMPOSITION. PRESERVE THE ORIGINAL. ESTABLISH THE EVIDENCE BEFORE THE LINEAGE.**
