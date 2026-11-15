# Evidence, Provenance, Lineage and Verification

**Status: PROPOSED GOVERNANCE CONTRACT.**

## Evidence classes
ORIGINAL_SOURCE; ACQUIRED_ARTIFACT; EXTRACTED; AI_INFERRED; CONTRACTOR_REPORTED; FIELD_OBSERVED; LOCATOR_OBSERVED; SURVEYED; INDEPENDENTLY_VERIFIED; OWNER_ACCEPTED; HUMAN_RATIFIED; CONFLICTING; UNKNOWN; NOT_MEASURED; UNAVAILABLE; ACCESS_DENIED; HISTORICAL_SUPERSEDED.

These labels are not interchangeable and must retain who/what assigned them and under which procedure.

## Provenance fields
Permanent artifact ID; source/custodian; source URL or record identifier; acquisition method and timestamp; publication date; revision; content digest; license/access basis; CRS, units and datum; geographic accuracy; extraction method and tool/model/version; transformation history; reviewer; verification scope; known limitations; conflicts; lineage parents and derived children.

## Rules
- NOT_MEASURED is not PASS.
- Discovery is not acquisition; acquisition is not verification; verification is not qualification; qualification is not ratification.
- Preserve failed, partial, conflicting, inaccessible and rejected evidence.
- Do not silently upgrade an inferred location or geometry to verified.
- Keep original design, submitted as-built, field observation, locator result, survey and verified record as separate claims.
- Corrections append a superseding or corrective event; they do not erase the original record.
- Human approval is represented by an explicit receipt containing decision, artifact digest, scope, policy version and disposition.

## Integrity
Compute and retain cryptographic digests at acquisition and after controlled transformations. Record the digest of the exact artifact reviewed. Preserve immutable originals and reproducible derivative lineage. A matching digest proves byte identity, not factual correctness.
