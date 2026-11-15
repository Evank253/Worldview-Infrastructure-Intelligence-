# WII — Subsurface Visualization and Location Intelligence

Status: INITIAL UI AND LOCAL RECORD WORKFLOWS IMPLEMENTED. REAL SUBSURFACE SENSING, AUTOMATED RECORD ACQUISITION, AND VERIFIED NETWORK RECONSTRUCTION ARE NOT IMPLEMENTED.

## User-facing map modes

The map includes independent toggles:
- **Surface:** standard geographic basemap and registered assets.
- **Underground X-ray:** a subdued surface context with registered underground-related asset markers and an explicit provenance notice.
- **GPR view:** a distinct display mode reserved for actual ground-penetrating radar, utility-locator, survey, and interpreted subsurface datasets.

These controls are visualization modes, not sensors. The current browser app does not emit radar signals, penetrate the ground, infer buried paths from satellite imagery, or claim to know underground routes. The current overlays display only user-registered records whose type is categorized as underground, water, electrical, or telecommunications. Their evidence state remains visible in the inspector.

## Location intelligence popup

Selecting an unoccupied map location opens a location inspector rather than forcing an asset registration. The current implementation:
- Displays selected coordinates.
- Searches registered assets and records within a 250 m context radius.
- Lists documents explicitly geotagged within that radius or attached to nearby registered assets.
- Displays city/county/engineering/utility/contractor issuer metadata where entered.
- Shows the latest dated work record among nearby registered assets, including person/crew and organization when recorded.
- Offers a route to register an asset at that coordinate or attach a geotagged document.
- Makes missing records explicit; no result is not proof that no infrastructure or work exists.

The 250 m radius is a convenience search, not a claim of physical connection, jurisdiction, service area, ownership, or applicability. It must become a configurable search policy with geometry-aware document coverage and jurisdictional boundaries in the production service.

## Document provenance fields

Document intake supports:
- Issuing source category: city, county, engineering team, utility owner, contractor, field team, other, or unknown.
- Issuer/department/organization.
- Document type, including blueprint/plan, as-built, permit/filing, county record, engineering report, inspection, work order, field note/photo.
- Revision/issue reference.
- Jurisdiction/service-area label.
- Optional geographic coordinates.
- Original file name, MIME type, size, SHA-256 digest, attached asset ID and local original blob.

A user-entered issuer label is not proof that the issuing agency authored, approved, or accepted the document. Production ingestion must verify official source origin, document signatures/record IDs, publication dates, revision status, and acquisition provenance.

## Work history

Work/inspection records now support person or crew identifier, employer/engineering organization, work-order/project reference, date, activity, disposition, and description. The inspector presents the most recent matching documented work record.

This is a record of what has been entered, not a complete personnel history. Unknown person/crew must remain unknown. Worker identity and performance data require role-based access, purpose limitation, correction/dispute processes, retention policy, and audit logging. Do not expose private worker details publicly.

## Production subsurface reconstruction requirements

To create a real underground X-ray / GPR experience:
1. Acquire authorized engineering plans, permits, as-builts, utility-owner records, survey files, and field-investigation artifacts. Preserve originals and issuer metadata.
2. Acquire actual GPR survey data, electromagnetic locator observations, sonde/rod/mandrel traces, pothole records, and/or survey-grade measurements where available.
3. Preserve equipment model, calibration, operator, survey date, method, antenna frequency, scan direction, spacing, depth calibration, soil conditions, signal quality, datum, coordinate reference system, and uncertainty.
4. Distinguish design depth, contractor-reported depth, locator-estimated depth, GPR-interpreted depth, exposed/measured depth, and survey-verified depth.
5. Reconstruct paths as evidence-linked 3D geometry with depth and vertical datum. Never silently convert plan alignment into measured physical location.
6. Label path segments by source and state: DESIGN, SUBMITTED_AS_BUILT, LOCATOR_INDICATED, GPR_INTERPRETED, FIELD_EXPOSED, SURVEY_VERIFIED, DISPUTED, or UNKNOWN.
7. Show confidence and positional uncertainty as an envelope/corridor, not false-precision lines.
8. Do not claim GPR proves cable identity, ownership, occupancy, splice configuration, or end-to-end continuity. Independent field evidence is required.
9. Require qualified review before excavation or other ground-disturbing work. Display appropriate one-call/811 and utility-owner safety workflow requirements; visualization is not excavation clearance.

## Location document acquisition roadmap

The location popup is currently local-data driven. It does not yet query city, county, state, utility, engineering, permit, or inspection repositories. Production source connectors must have source-specific lawful access, rate limits, authentication, terms, retention, update timestamps, and evidence manifests. Each acquired record must retain its original source URL or file reference, jurisdiction, record number, issue/revision date, acquisition time, digest, license/access classification, and verification status.

CLONE BEFORE COMPOSITION. Preserve source files and source-system identifiers. Derived metadata, extracted text, and reconstructed geometry remain separate linked artifacts.