# WII-001 — Platform Architecture

**Status: PROPOSED DESIGN BASELINE.** This document records the established product intent; it does not claim the platform features are implemented.

## Product definition
Worldview Infrastructure Intelligence (WII) is a map-first, evidence-backed intelligence platform for infrastructure. Location is the entry point; intelligence is the content; the map is the interface.

The platform must navigate from world and jurisdiction to region, city, street, property, worksite, structure, asset, and documented internal configuration. Selecting a location reveals the authorized records and infrastructure known to be associated with it.

## Primary user journey
1. Navigate or search to a location.
2. Inspect available infrastructure layers and coverage limitations.
3. Select an asset (pole, manhole, vault, conduit, cable, service line, transformer, valve, building utility, etc.).
4. Open the original engineering record, permit, inspection, photograph, field note, or as-built.
5. Compare original design, contractor-submitted record, reconstructed representation, field observation, and independently verified state.
6. Trace documented connections and review construction, inspection, maintenance, replacement, ownership, and schedule history.
7. Review work quality, deficiencies, corrections, and positive accomplishments under authorized access.

## System boundaries
WII is a platform umbrella, not a monolithic subsystem. Independent capabilities retain their own identity, contracts, data ownership, test suites, and deployment boundaries. Shared services provide identity, access policy, evidence/provenance, geographic references, temporal history, and interoperability.

## Core layers
- Experience: map, search, asset panels, document viewer, timeline, comparison, field and project workspaces.
- Geospatial: locations, geometry, coordinate reference systems, vertical datums, accuracy, temporal geometry, 2D/3D rendering.
- Infrastructure domain: asset types, ownership, networks, physical components, connections, lifecycle.
- Document intelligence: source acquisition, OCR, CAD/GIS parsing, drawing interpretation, reconstruction, comparison.
- Work intelligence: projects, contractors, crews, schedules, inspections, deficiencies, corrections, recognition.
- Evidence services: immutable originals, digests, provenance, lineage, verification, conflicts, corrections.
- Source intelligence: jurisdiction/source registry, APIs, portals, public-record processes, update monitoring.
- Security and governance: role/scope authorization, sensitive-data controls, audit, privacy, human authority boundaries.

## Map truthfulness
A map symbol is a representation, not proof. Every displayed geometry must expose its evidence class, source, date, accuracy, method, limitations, and status. Design alignment, submitted as-built, field observation, locator trace, survey, and verified asset geometry remain distinguishable. Unknown geometry must not be rendered as fact.

## Data separation
Original documents and acquired source artifacts are immutable. Extracted text, interpreted attributes, normalized records, reconstructed drawings, derived geometry, and user annotations are separate artifacts linked by lineage. Corrections append new events and do not silently rewrite history.

## Technology direction
A spatial relational core (PostgreSQL/PostGIS) is a candidate for authoritative structured records. A map rendering layer may use CesiumJS for globe/3D and/or MapLibre for 2D vector mapping. Object storage holds originals and derivatives. OCR/CAD/GIS processing, graph relationships, search, and monitoring are separate services. These are candidates, not final technology decisions; benchmark and threat-model before commitment.
