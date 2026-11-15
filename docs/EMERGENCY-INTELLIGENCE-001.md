# EOI-001 / EDI-001 / EOVI-001 — Emergency Intelligence Architecture

**Specification status:** ARCHITECTURAL REQUIREMENTS RECORDED — NOT IMPLEMENTED, TESTED, QUALIFIED, OR HUMAN-RATIFIED.  
**Platform:** WII-001 — Worldview Infrastructure Intelligence  
**Governing principle:** EMERGENCY FIRST. INTELLIGENCE IMMEDIATELY. EVIDENCE THROUGHOUT.

## 1. Purpose

When an infrastructure emergency or outage is reported, WII must immediately present the incident location and available supporting intelligence on the map. The foreman must not have to navigate through a job packet before seeing the incident location.

The emergency experience is map-first and progressively enriched. The incident location and essential report details appear first; supporting infrastructure, network relationships, source documents, history, site conditions, and crew information load independently as available.

This specification defines three separate but coordinated capabilities sharing one canonical incident record.

## 2. System boundaries and responsibilities

### EOI-001 — Emergency Outage Intelligence

The overarching incident intelligence and coordination capability.

Responsibilities:
- Register emergency and outage incidents.
- Maintain a shared incident record and incident lifecycle.
- Monitor multiple simultaneous incidents.
- Record reported severity, impact, affected service or infrastructure sector, and status.
- Identify potentially related incidents for investigation without asserting causation.
- Coordinate cross-sector intelligence.
- Preserve incident history, updates, conflicts, and disposition.

EOI-001 does not independently authorize dispatch, declare an outage cause, or assert network impact without evidence and authorized operational input.

### EDI-001 — Emergency Dispatch Intelligence

The operational dispatch capability.

Responsibilities:
- Receive and record authorized emergency assignments.
- Identify crews reported available through connected dispatch data.
- Compare assignment requirements with crew, vehicle, equipment, and material readiness.
- Preserve original assignments and append reassignment events.
- Generate a distinct emergency job packet.
- Track mobilization, arrival, work, delays, restoration, and closeout.
- Connect emergency response to the Crew Day Timeline, JSSI-001, VRI-001, ETR-001, YTI-001, DSI-001, PFE-001, BCI-001, and ARI-001.

A dispatch recommendation is not a dispatch authorization. The system must record the authorized issuer and the actual dispatch event.

### EOVI-001 — Emergency Outage Visualization Intelligence

The immediate map and situational-awareness experience.

Responsibilities:
- Automatically open the incident map for the assigned foreman when an authorized assignment is received.
- Center the map on the reported incident location.
- Display the reported outage area separately from verified damage geometry.
- Highlight documented infrastructure and evidence-supported relationships.
- Surface mapped assets, source documents, engineering drawings, historical repairs, inspections, deficiencies, access restrictions, traffic conditions, and other available context.
- Display nearby crews only when connected, authorized dispatch data supports the information.
- Support multiple simultaneous incidents and incident-specific map focus.

EOVI-001 is a visualization and retrieval interface. Rendering an asset or relationship does not independently verify its physical existence, condition, ownership, connectivity, or operational impact.

## 3. Canonical emergency incident record

All three systems reference one shared incident identifier and append their own events. Minimum record fields:

- Incident ID and schema version.
- Incident type and infrastructure sector.
- Reported date/time and time zone.
- Reporter/source and reporting organization, when known.
- Reported location, coordinate reference, location method, and accuracy/uncertainty.
- Incident severity/priority as reported or assigned by an authorized role.
- Description and reported service impact.
- Affected asset IDs, each with an explicit relationship and verification state.
- Incident geometry, geometry source, and geometry classification.
- Source artifacts and document references.
- Related incident references, with relationship basis and status.
- Dispatch assignments and authorized issuer.
- Crew, vehicle, equipment, and material references.
- Safety review and permit/document references.
- Field observations, photographs, video, and evidence digests.
- Restoration events and supporting evidence.
- Cost/billing impact references.
- Incident status, disposition, and authorized closeout.
- Append-only event history and correction/supersession references.

Do not silently overwrite reported information. Corrections and new findings are appended with actor, timestamp, reason, and links to superseded values.

## 4. Immediate visibility and progressive loading

### Priority 1 — Immediate incident context
- Incident identifier.
- Reported location and location uncertainty.
- Incident type, severity/priority, reported time, and dispatch status.
- Initial map focus.

### Priority 2 — Nearby documented infrastructure
- Assets within a configurable, disclosed search area.
- Asset identifiers, geometry evidence state, source and date.
- Layer coverage and source availability.

### Priority 3 — Known affected assets and network relationships
- Explicitly documented connections.
- Upstream/downstream relationships only where source evidence supports direction and continuity.
- Suspected or candidate relationships shown separately from confirmed/documented relationships.

### Priority 4 — Engineering documents and construction records
- Original plans, as-builts, permits, work orders, construction packages, and related source artifacts.
- Direct links from mapped assets to the preserved original documents.

### Priority 5 — Historical records
- Prior repairs, inspections, deficiencies, corrections, maintenance, and related incidents.

### Priority 6 — Site and access conditions
- Traffic, road restrictions, access, weather, permits, and site hazards where reliable sources and permissions allow.

### Priority 7 — Crew and equipment context
- Nearby crew locations and availability, vehicle status, equipment readiness, and dispatch options, only when connected and authorized data is available.

Each independently loaded source/layer must report one of:
- LOADED
- LOADING
- UNAVAILABLE
- OUTDATED
- AWAITING_VERIFICATION
- ACCESS_RESTRICTED
- ERROR

Failure or delay of a lower-priority source must not block incident registration or initial map activation. The interface must not display stale data as current.

## 5. Evidence and relationship rules

Every infrastructure feature and relationship displayed in the emergency context must retain, where available:
- Source artifact or source record ID.
- Source organization and source date.
- Source revision/version.
- Relevant infrastructure asset identifiers.
- Acquisition or observation method.
- Verification state.
- Confidence/uncertainty classification and its basis.
- Last verification date.
- Geometry accuracy, coordinate reference system, and vertical datum when relevant.

Required distinctions:
- REPORTED
- DOCUMENTED
- FIELD_OBSERVED
- LOCATOR_ESTIMATED
- GPR_INTERPRETED
- EXPOSED_MEASURED
- SURVEY_VERIFIED
- INFERRED
- DISPUTED
- UNKNOWN
- NOT_MEASURED

A reported outage location is not automatically the verified damage location. Geographic proximity, common labels, visual alignment, or incomplete records must not create network connectivity. Unknown remains UNKNOWN.

## 6. Emergency workflow

1. Emergency report received.
2. EOI-001 creates the incident record and records the report source.
3. EOVI-001 opens the incident map immediately using the reported location.
4. Priority 1 incident context appears without waiting for other sources.
5. Infrastructure, network relationships, documents, history, and site context load progressively and independently.
6. EDI-001 evaluates crew/equipment information from authorized connected sources.
7. An authorized dispatcher issues and records an assignment.
8. The emergency job packet is created and linked to the incident.
9. Crew arrival, safety review, work, delays, photographs, and field observations are recorded.
10. Field evidence updates the incident view while preserving original evidence and provenance.
11. Restoration is recorded with supporting evidence and authorized disposition.
12. Incident closeout preserves the complete event history and unresolved unknowns.

## 7. Multiple incidents and possible correlation

The system must support multiple active incidents on one map, with filtering by sector, severity, status, time, and jurisdiction.

Potentially related incidents may be grouped for investigation only when the system records:
- The relationship hypothesis.
- Supporting and contradicting evidence.
- The source and time of each observation.
- The relationship status: CANDIDATE, UNDER_REVIEW, SUPPORTED, REJECTED, or UNKNOWN.
- The authorized reviewer and disposition, when applicable.

Temporal or geographic proximity alone is not proof of a shared cause.

## 8. Operational continuity and connected systems

The canonical incident record must connect to:
- DSI-001 — Dynamic Dispatch & Job Rescheduling Intelligence.
- Crew Day Timeline.
- Project and work-order records.
- VRI-001 — Vehicle Readiness Intelligence.
- ETR-001 — Equipment & Tool Readiness Intelligence.
- YTI-001 — Yard & Time Intelligence.
- JSSI-001 — Jobsite Safety & Site Intelligence.
- PFE-001 — Photographic & Field Evidence Intelligence.
- ARI-001 — Accident & Incident Reporting Intelligence.
- BCI-001 — Billing & Cost Impact Intelligence.
- Infrastructure asset, document, evidence, history, and field-capture records.

Each subsystem retains its own event provenance and record authority. A shared incident ID links records; it does not permit one subsystem to silently rewrite another subsystem's records.

## 9. Security, privacy, and operational safety

- Access is scoped by role, organization, project, incident, and data sensitivity.
- Sensitive infrastructure and crew-location data must not be exposed publicly.
- Crew location is available only through authorized integrations and lawful policy.
- Emergency map views must clearly show data age and availability.
- The system must support degraded/offline operation using previously synchronized, access-authorized records, while clearly identifying stale or unsynchronized data.
- The map must not delay emergency calls, emergency services, or required field safety actions.
- The software does not replace dispatch authority, utility-owner procedures, permits, locate requirements, competent-person assessments, or emergency-response protocols.

## 10. Acceptance tests — mandatory before operational claim

1. An emergency report creates a canonical incident record with source and timestamp.
2. The incident map opens at the reported location and exposes location uncertainty.
3. Priority 1 information appears without waiting for supporting sources.
4. Infrastructure layers load independently and expose their individual status.
5. Original engineering documents can be opened from mapped assets without replacing or altering originals.
6. Network tracing distinguishes source-documented relationships from inferred, suspected, disputed, and unknown relationships.
7. Multiple simultaneous incidents can be displayed and individually inspected.
8. Crew reassignment preserves the original dispatch and complete event history.
9. Field evidence links to the correct incident and job packet, preserving original files and checksums.
10. Restoration cannot be represented as verified without supporting evidence and authorized disposition.
11. Failure or interruption of one data source does not prevent incident registration or initial map activation.
12. Stale, restricted, missing, or unavailable data is never presented as current verified intelligence.
13. Unauthorized users cannot access restricted incident, infrastructure, or crew-location information.
14. Event history, corrections, and closeout remain auditable after export/import or synchronization.

## 11. Implementation boundary and current status

This document is an architectural specification only. It does not claim that emergency ingestion, dispatch integrations, automatic map activation, network tracing, crew tracking, outage correlation, or restoration verification are implemented.

The current WII browser foundation is local-only and has no authenticated multi-user backend or authoritative utility/dispatch feeds. Any prototype must use synthetic incident and infrastructure records, visibly marked as synthetic, until appropriate data sources, permissions, security controls, and verification workflows exist.

Implementation must follow:
1. CLONE BEFORE COMPOSITION.
2. Preserve originals and record source lineage.
3. Use WII-owned working copies.
4. Keep incident, dispatch, visualization, and evidence responsibilities separated by explicit contracts.
5. Test with synthetic data before any sensitive or live infrastructure integration.
6. Preserve all failures, missing evidence, and unresolved verification gaps.

**Architectural principle: EMERGENCY FIRST. INTELLIGENCE IMMEDIATELY. EVIDENCE THROUGHOUT.**
