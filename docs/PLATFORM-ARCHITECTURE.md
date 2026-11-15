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

## Technology direction — existing engines plus professional rendering

**Architecture correction:** WII is not starting its geospatial engine from scratch. Existing Worldview/KCN repositories already contain geospatial and globe-engine work. The task is to audit, preserve, complete, qualify, and integrate those engines, then extend their visual capabilities with professional graphics and a game-engine rendering environment. Do not replace existing engines with a newly proposed stack merely because a library is familiar.

### Existing engine lineage to audit and reuse
- `Evank253/kcn-worldview-command-center`, branch `Python-3`, source commit `2261e9344a079d2f6d622d944c5b0a431bac1aa1`: contains existing Cesium/globe implementation files including `app/src/cesiumGlobe.ts`, `app/src/globe.ts`, `app/src/layerRegistry.ts`, `app/src/cesium-demo.ts`, plus tests, build configuration and a Cesium demo. WII currently has only a partial preserved source snapshot; the original source repository remains untouched.
- `Evank253/world-view`, branch `Products`, inspected tree commit `31d951a263c57b6d5ad2fc1c702a8a6ab85af307`: contains earlier map component, app and supporting Worldview modules. Audit for unique reusable functionality; do not assume it is a production geospatial engine.
- `Evank253/worldviewcommandcenteroftechnologies`, branch `Products`, inspected tree commit `50750ddc2a5efbfc9df46f56feb32c58e3e8bdc2`, and `Evank253/worldview-command-center-os-pro-version-`, branch `Products`, inspected tree commit `48003eb381cac27ff672fdf3bfc611d9c04a955f`: preserve and inspect as related Worldview lineage. Their tree contents alone do not establish production readiness or feature completeness.
- Other discovered repositories with empty or minimal trees are not to be treated as completed engines.

### Rendering and graphics architecture
Keep the authoritative geospatial/infrastructure model independent of any renderer. Use adapters so multiple visual clients can consume the same versioned, evidence-linked geometry and metadata:
1. **Existing Worldview geospatial engine(s):** primary location, layer, coordinate, asset, route, temporal and geospatial interaction foundation. Inventory existing code and tests before extending.
2. **Professional graphics/rendering toolchain:** high-quality material and texture authoring, physically based materials, terrain/mesh processing, photogrammetry/point-cloud preparation, lighting, procedural vegetation, model optimization, level-of-detail generation, and export pipelines. Every asset retains source, license, version, hash, coordinate reference, scale and lineage.
3. **Game-engine visualization client:** evaluate Unreal Engine as the high-fidelity visualization/simulation environment, not as the authoritative infrastructure database or replacement for the existing map engine. It can provide physically based rendering, advanced lighting/shadows, foliage, collision/physics, interactive scene controls, simulation and immersive visualization. Maintain a separate lightweight web experience for normal browser access.
4. **Geospatial bridge:** evaluate Cesium for Unreal as a bridge between a WGS84 globe/3D Tiles geospatial content and Unreal's rendering/runtime. The official Cesium documentation describes this integration, including real-world 3D Tiles, photogrammetry, terrain, imagery, buildings and Unreal interaction features. This is a candidate integration path, not yet integrated into WII.
5. **Interchange contracts:** define versioned interfaces for WGS84/ECEF/local engineering coordinate frames, vertical datum, units, georeferencing transforms, GeoJSON, 3D Tiles, glTF/glb and source-linked feature metadata. Never lose asset IDs, evidence state, precision, uncertainty, temporal version or provenance during export/import.

### Rendering truth and fidelity
Higher visual fidelity must never be confused with higher evidentiary confidence. Photorealistic terrain, generated buildings, simulated poles, reconstructed cable paths and procedural trees must carry explicit provenance and classification. Synthetic or illustrative objects must be visibly marked. A renderer may improve appearance, navigation, inspection and simulation; it cannot independently prove asset ownership, underground location, cable continuity, clearance compliance or as-built condition.

### Clone-before-composition integration sequence
1. Preserve each source repository/ref/commit and obtain complete source archives, including binary assets and licenses where available.
2. Create isolated WII-owned clones or working copies; record tree manifests, blob hashes, licenses, dependencies, build instructions and SBOM. Never modify upstream originals.
3. Audit existing geospatial engines and rendering capabilities; identify duplicated or conflicting components before selecting the integration boundary.
4. Benchmark game-engine candidates against WII requirements: geospatial precision, large-world streaming, visual quality, vegetation/terrain, performance, platform support, licensing, accessibility, offline/private deployment and maintainability.
5. Prototype the geospatial bridge with a small, synthetic, clearly labeled test scene before connecting real sensitive infrastructure data.
6. Verify coordinate accuracy, scale, vertical datums, feature metadata preservation, evidence overlays, performance and source attribution.
7. Keep web and high-fidelity rendering clients independently buildable and testable. Human authority and evidence services remain outside renderer control.

**Current status:** existing Worldview geospatial source has been identified and partially preserved, but complete clone intake and integration verification are still open. The Unreal/Cesium bridge and professional graphics pipeline are architectural candidates; they have not yet been installed, cloned, integrated or tested in WII.
