# VCI-001 — Vegetation Clearance Intelligence

Status: INITIAL BROWSER-LOCAL OBSERVATION WORKSPACE IMPLEMENTED; AUTOMATED VEGETATION DETECTION NOT IMPLEMENTED.
Branch: `wii/operational-foundation-001`

## Purpose

Record and organize potential vegetation conflicts affecting documented aerial infrastructure routes, particularly aerial fiber. VCI connects route/segment context, vegetation observations, measurements, imagery/field evidence, review dispositions and work records.

## Current implementation

- Dedicated Vegetation Intelligence navigation view.
- User-entered route and pole-span identifiers.
- Coordinate, vegetation type, evidence method, observation date, optional measured distance and cable height, confidence, and notes.
- Browser-local persistence in localStorage under `wii-vci-observations`.
- Evidence-ledger event for each observation and disposition update.
- Disposition updates and JSON report export.
- No third-party dependency introduced.

## Explicit limitations

- No computer-vision model, aerial imagery ingestion, LiDAR processing, canopy segmentation, cable geometry reconstruction, clearance computation, growth prediction, work-order integration, or automated route-wide assessment.
- A distance measurement is stored as entered; it is not evaluated against a generic threshold.
- Confidence is a user-entered characterization, not a calibrated probability.
- User-entered route and pole-span labels do not establish a physically verified route.
- No tree-trimming recommendation is automatically authorized.
- Browser-local data is not a secure multi-user or audit-grade backend.

## Required future data model

Each observation should include:
- Stable observation ID and immutable creation event.
- Route ID, segment ID, source asset IDs, and route-geometry version.
- Geometry and coordinate reference system, positional accuracy and datum.
- Vegetation object geometry/type/species when known, height/canopy extent, capture date and source.
- Cable geometry/version, attachment heights, sag/tension context if measured, and measurement method.
- Imagery/LiDAR source ID, acquisition date, resolution/point density, licensing and digest.
- Applicable owner standard, standard revision, jurisdiction, clearance rule and reviewer.
- Calculated result with algorithm/model version, input digests, uncertainty and limitations.
- Separate statuses for potential finding, field inspection, confirmed encroachment, standards review, authorized work, completed work and independent closeout.
- Reviewer identity/authority, decision receipt, work order, before/after evidence and correction history.

## Analysis pipeline (future)

1. Resolve the documented aerial route and pole-to-pole geometry.
2. Acquire authorized, dated imagery and/or LiDAR; preserve source artifacts and metadata.
3. Reconstruct vegetation objects and cable corridor with uncertainty.
4. Calculate candidate spatial conflicts only where inputs and coordinate systems support it.
5. Apply the correct owner/jurisdiction clearance standard only when supplied and verified.
6. Rank inspection priorities with explainable factors; do not silently equate a model score with risk or violation.
7. Require qualified field review and authorized decision before trimming work.
8. Capture work completion and independent closeout evidence.
9. Preserve all prior observations and route/vegetation versions.

## Safety and governance

Potential encroachment is not a confirmed violation. A confirmed field observation is not automatically a standards violation. A standards violation is not itself authorization to trim. Tree work must be assigned to qualified personnel under applicable utility, electrical, arboricultural, traffic-control and jurisdictional requirements. Never direct unqualified people to approach energized lines or perform trimming.

CLONE BEFORE COMPOSITION. Preserve original imagery, LiDAR, engineering documents and field evidence; create WII-owned derivatives with source lineage.