# WII Operational Foundation 0.1.0

This is the first executable, browser-local WII foundation. It is deliberately dependency-free: no npm packages, mapping SDK, UI framework, or third-party JavaScript library is used. The application code is original WII code and does not import the partially cloned command-center source.

## Run

Serve this directory over HTTP (not by opening the HTML file directly), for example:

```bash
python3 -m http.server 4173 --directory wii-app
```

Open `http://localhost:4173`.

## Working capabilities

- Interactive slippy-map viewport with pan, zoom, coordinate navigation, and map-click asset placement.
- User-entered infrastructure asset registry with stable local IDs and explicit evidence states.\n- Evidence-derived underground connection display from explicit asset/work-record cross-references; no manual route drawing.\n- Subsurface depth metadata with explicit depth evidence classes and vertical datum/units.
- Browser-local document storage using IndexedDB; SHA-256 digest computed at intake; original file can be downloaded again.
- Evidence ledger recording asset and document intake events.
- Work / field / inspection / deficiency / correction records with explicit dispositions.
- JSON workspace export/import, including document blobs.
- Responsive dark geospatial workspace.

## Data and evidence boundaries

- There are **no fabricated utility assets, utility routes, ownership claims, depths, or connections** preloaded.
- OpenStreetMap raster tiles are fetched from the hosted OSM tile service only for the visible viewport. This external service cannot be cloned into this repository. Visible attribution is provided. OSM tile availability is best-effort and subject to its usage policy; production/commercial use requires a suitable tile provider or self-hosted tile infrastructure. The provider is configurable in `src/app.js`.
- Browser-native APIs (DOM, IndexedDB, WebCrypto, File, Blob, localStorage) are runtime platform capabilities, not vendored dependencies.
- User-created records and document blobs remain in the current browser profile. There is no backend, cloud synchronization, authentication, access control, multi-user workflow, backup service, or server-side encryption yet.
- A coordinate is not proof of physical asset location. A field observation is not proof of owner, depth, material, occupancy, or connectivity.\n- Underground connection lines are derived only from explicit recorded asset/work references and remain unverified; proximity and shared route labels alone never create connections. No GPR scan, automatic blueprint extraction, or physical continuity verification is performed. Device GPS tracks are not survey-grade, and field video is not automatically geolocated or interpreted.
- A user-uploaded document is preserved and hashed; its contents are not yet OCR-extracted, parsed, georeferenced, or independently verified.
- Import/export is user-controlled and should be treated as sensitive. Do not upload restricted critical-infrastructure documents to an unapproved service.

## Clone-before-composition

The implementation has no third-party code dependencies. It does not consume the partial source clone under `source-clones/`. Any future library, model, service adapter, or repository component must be separately preserved and registered before WII uses its WII-owned working copy. Hosted services that cannot be cloned require an explicit integration boundary, provider terms/version/config record, and replacement plan.

## Status

Executable foundation; not a production-ready infrastructure intelligence platform. No national data ingestion, official utility feeds, blueprint reconstruction, network tracing, AI agents, role-based access control, audit-grade server ledger, or production deployment is claimed.
- Field capture workspace: device GPS breadcrumb runs, timestamped field markers, attached video/photo evidence, SHA-256 media digests, video-playback timestamp linking, map route display, and field-run export.
