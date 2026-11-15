# WII — Field Capture and Run Trace 001

Status: INITIAL BROWSER-LOCAL IMPLEMENTATION. DEVICE GPS, MEDIA ATTACHMENT, AND USER-PLACED FIELD MARKERS ARE AVAILABLE IN THE DEVELOPMENT WORKSPACE. NO BACKEND SYNC OR SURVEY-GRADE POSITIONING IS CLAIMED.

## Purpose

Field crews must be able to document the route and work they actually traverse without manually reconstructing the entire run afterward. WII supports a GPS breadcrumb trace, time-stamped field markers, and attached run footage/photos. A crew member can also select a location on the map and place a field marker there while a run is active.

This is complementary to automatic historical reconstruction:
- Historical/documentary evidence reconstructs what records say was designed, installed, investigated, or changed.
- Field capture records what a crew observed or did on a particular run.
- WII correlates these evidence streams but never silently treats one as proof of the other.

## Current field workflow

1. Open **Field capture**.
2. Enter project/work-order and crew/operator identifiers.
3. Select **Start field run** and grant browser location permission.
4. The browser records GPS positions with timestamp, reported horizontal accuracy, altitude/altitude accuracy, heading, and speed when supplied by the device.
5. GPS points are sampled when the device has moved at least 3 m or 15 seconds have elapsed.
6. Select **＋ Marker at current GPS** to place a marker at the latest GPS fix.
7. Or select a map location, choose **Place field marker here**, then use **Place marker at selected map location**.
8. Choose marker type and method; enter notes and any registered asset ID.
9. Attach video or photographs to the active run. Originals are stored in browser IndexedDB and SHA-256 digests are recorded.
10. Play attached video in the run timeline. The current playback time is copied into the marker footage-timestamp field so the next marker can be linked to that moment in the clip.
11. End the run. Export the run metadata and attached media using the field-run export.

GPS trace and field markers are rendered on the map. Runs interrupted by a browser restart are retained and marked INTERRUPTED; they are not silently resumed.

## Evidence and uncertainty

- Device GPS is not survey-grade positioning. Accuracy metadata is preserved; the display must not imply greater precision than the device reports.
- GPS trace shows the device path, not necessarily the exact cable, duct, pole alignment, or work location.
- A video timestamp links a field marker to a moment in an attached clip; it does not automatically identify objects or extract coordinates from footage.
- A user-selected map point is a user-entered field marker, not a verified surveyed coordinate.
- A field observation does not by itself establish underground depth, cable identity, ownership, occupancy, splice configuration, or continuity.
- Locator and GPR methods remain separate observation types; actual equipment readings and interpretation artifacts must be captured and reviewed.
- Media is preserved locally in the browser. It is not uploaded to a central server or shared with other users in this foundation.
- GPS collection is permission-based and should be started/stopped explicitly. Field-run and worker-identifying information must be protected by future role-based access, retention, and consent policies.

## Next engineering stages

- Frame extraction and computer-vision-assisted marker suggestions, always reviewable and linked to source frames.
- Video GPS/EXIF and telemetry synchronization, where available, with clock-offset estimation and uncertainty.
- Offline-first encrypted field sync to a governed backend.
- Bluetooth GNSS / RTK receiver support and survey-grade coordinate reference systems.
- Structured locator, GPR, sonde, rod, mandrel, pothole/exposure, depth and measurement capture.
- Route snapping only when supported by evidence and with raw unsnapped observations preserved.
- Automatic correlation with design drawings, as-builts, historical work orders, pole spans, splice cases and underground asset graph.
- Per-observation lineage, review, correction, dispute and independent verification workflows.

CLONE BEFORE COMPOSITION. Preserve original field media and source records. Derived frames, extracted metadata, AI interpretations, and reconstructed geometry remain separate artifacts linked to their originals.