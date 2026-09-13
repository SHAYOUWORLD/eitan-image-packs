# Optional scene packs v1

These files repackage the existing reviewed illustrations at source revision
97f3d9b67273e561cb4bf7992afdf341bba40040 without changing image bytes.

Each opaque SHA-256 filename is immutable. The app downloads a whole selected
vocabulary pack only after an explicit user action; it does not request individual
learning words. HTTP requests still disclose network metadata and the selected
pack to the host. No learner records, responses, or profiles are contained here.

Format: ASCII `TNSCENE1` followed by WebP data in sorted key order. `catalog.json`
provides the exact key order, individual sizes/hashes and full pack size/hash.
Clients pin this catalog, verify all hashes, and reject unknown/corrupt payloads.
The app stores images once across selected packs and retains shared files until
no selected pack references them.

Generated with the app repository's `tools/bundle_scene_images.py` from its vendored
image snapshot. The original scenes remain intact for compatibility with older apps.
The image provenance and license notes in the root README continue to apply.
