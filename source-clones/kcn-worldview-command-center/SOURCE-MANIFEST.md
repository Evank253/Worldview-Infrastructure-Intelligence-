# Source Snapshot Manifest — KCN Worldview Command Center

**Snapshot class:** PARTIAL TEXT SOURCE PRESERVATION  
**Source repository:** https://github.com/Evank253/kcn-worldview-command-center  
**Source branch:** `Python-3`  
**Source commit:** `2261e9344a079d2f6d622d944c5b0a431bac1aa1`  
**Destination:** `source-clones/kcn-worldview-command-center/`  
**Source mutation:** NONE

All entries below were fetched from the exact source commit and copied byte-for-byte as UTF-8 text through GitHub's file API. The listed SHA is the source Git blob SHA returned by the source repository. Destination path mirrors source path.

| Source path | Source blob SHA |
|---|---|
| app/.gitignore | dd8fe26f7f5628b9e0dca659a7c1d42a712335ae |
| app/Dockerfile | ecfe2fe1f3ffa5e0786df8c45f8aea97cbae66c8 |
| app/Dockerfile.server | b2bca3a359a58f1332e00272a5358145bc5fc664 |
| app/README.md | 91ba4aa70ea397a0a020f36f84af302eb1a6e9b7 |
| app/cesium-demo.html | d4b0626ed6a8ddb089d1713d296343d31865939c |
| app/docker-compose.yml | aa662189ffeed0da0d7cee168d949f8a8e9c415c |
| app/eslint.config.js | 4ade3a1c2138ee9b7bf64cbe5e2c17f81ff889ca |
| app/index.html | 505eab539b30d5b202346ecbe8a092e4dd5dd49c |
| app/nginx.conf | 04dcfeaac7d799ef9f438117e539fdd77debe8c5 |
| app/package.json | 2ec7b9b2c9ffae1c97c67e9cc125cb0cbed0e297 |
| app/package-lock.json | f8414d2a1a87b1a8a12d7cb8af7c1946a241923e |
| app/server/api/flights.ts | 7f0f6e4b026a6207f543d2b85cb359b5de880186 |
| app/server/api/threats.ts | a5999477238b260975aa1f9dd8758c3978a596a5 |
| app/server/index.ts | 946f65431c8164bb8b7e5ea45569cdb149159e13 |
| app/server/test/flights.test.ts | 37090c735789c562707ab55caaa4535b2e8ae6a6 |
| app/server/test/threats.test.ts | d14ae1d9ba8a323fe08c1e32eaeb21fb44aab607 |
| app/src/attackArc.ts | 52a023aba9294e718611813b56303c74361b840c |
| app/src/cesium-demo.ts | ee4bbd4134069eeaf6b7aa80d443487052964800 |
| app/src/cesiumGlobe.ts | 3f798f329b234fd03f3281cbc2af0cd4d14617d8 |
| app/src/data/cyberEvents.ts | 55378cc5758978a148ecf3fdbc8e9edc3c00ebc1 |
| app/src/data/osint.ts | d43fc703afb497655c60e6fc42ca0db76122589d |
| app/src/data/types.ts | a3b3343de0746ddb54dedaae28a0b899b3db8578 |
| app/src/globe.ts | 16f51c989c6f9ed4d3a1204396fc03e888bc26d9 |
| app/src/layerRegistry.ts | 8b9276594b0e6e79d52b26926ebce3c97b3929c |
| app/src/main.ts | 52acff1e5fffa1f720cc4a2d9e24a0602d2ca901 |
| app/src/test/attackArc.test.ts | 788cd12e923dffa388e2127a2294c33a48437740 |
| app/src/test/cyberEvents.test.ts | 5ec99191e8a94b546957dba70ee3e5533e5bbda9 |
| app/src/test/globe.test.ts | c1d26c43ed8248b4acb3269521506f1ba0272521 |
| app/src/test/layerRegistry.test.ts | 8885d742555509745492e713b35ff2890651fc7c |
| app/tsconfig.json | 9c90c2a1c24512f1019c8cd8710eca7fed6a7c2b |
| app/vite.config.ts | 22d8a4fa223f4fd00a3477be3ac846ad834e421c |
| Worldview/README.md | 513adc1c9784168e77681249c96d558c7d7236a6 |

## Not yet copied

- Binary texture assets: `app/public/textures/earth_clouds_1024.png`, `earth_day_4096.jpg`, `earth_night_4096.jpg`, `earth_normal_2048.jpg`, `earth_specular_4096.jpg`.
- `app/public/textures/ATTRIBUTION.md` (must be copied with the texture assets).
- Any other files outside the listed source paths and the exact source commit inventory.
- No build, unit-test run, browser render, or independent verification was performed on the destination snapshot.

## Important source caveats preserved in the source README

The source app distinguishes live OpenSky records from curated fallback records and explicitly labels simulated cyber-event geolocations as demo-only. Its CesiumJS viewer is documented as not yet wired into the main app and not visually verified in a browser. The copied code remains a source snapshot, not WII production functionality.

## Next action

Complete binary asset and attribution preservation, inventory all other potentially relevant Worldview and KCN source repositories, then assess and integrate from isolated clones. Do not treat this first snapshot as the complete set of everything the creator has built.
