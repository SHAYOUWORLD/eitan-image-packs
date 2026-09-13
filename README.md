# eitan-image-packs

Public image assets maintained by SHAYOUWORLD for the eitan learning apps,
including Tanren. This repository contains static assets, not a learner-data
service. Public availability is separate from the image provenance and license
notes below; it does not grant an additional blanket license.

## Current delivery: `packs/v1/` — optional illustration packs

Current Tanren builds download a whole learning unit only after the user chooses
**Save** in **My Page → Settings → Example-sentence illustration management**
(`マイページ → 設定 → 例文イラスト管理`). Opening settings or studying does not
automatically download illustrations. Wi-Fi is the default; cellular downloads
require the user's separate choice. Saved images can be viewed offline.

```text
https://raw.githubusercontent.com/SHAYOUWORLD/eitan-image-packs/main/packs/v1/<sha256>.scenepack
```

- Each filename is the SHA-256 of its complete payload. A pack starts with
  `TNSCENE1`, followed by the image bytes in the order specified by the catalog.
- `packs/v1/catalog.json` records pack filenames, sizes, hashes, and image keys.
  Tanren ships its catalog inside the app; it does not fetch this remote catalog
  at runtime. The app verifies the complete pack and each image before saving.
- Images shared by multiple saved units occupy storage once. Deleting a unit
  keeps images needed by another saved unit. Deleting illustrations does not
  delete learner records, answers, settings, or purchases. A unit can be saved
  again later.

### Compatibility and maintenance

Keep already published hashed pack files unchanged and available: installed app
versions refer to those exact filenames, sizes, and hashes. Publish changed
content under a new hash, and update the app's bundled catalog through its normal
release process. Do not rename, overwrite, or remove old packs merely to clean up
this repository. The legacy paths below also remain available for older apps.

Do not add learner-specific URLs, query parameters, authentication, analytics,
or tracking code to asset delivery. See [delivery privacy](PRIVACY.md) for the
network metadata handled by GitHub and the limits of repository-side controls.

## Legacy: `scenes/` — individual scene illustrations (flat-scene-v1)

One illustration per vocabulary word, depicting the word's example sentence as a
memory cue. Served directly via raw URLs:

```
https://raw.githubusercontent.com/SHAYOUWORLD/eitan-image-packs/main/scenes/<key>.webp
```

By default, `<key>` = word lowercased, non-ASCII-alphanumeric characters replaced
with `_`. Explicit sense overrides prevent collisions: the verb `carry on` uses
`carry_on_continue`, while the noun `carry-on` keeps `carry_on`.
`scenes/manifest.json` lists every available key. Older apps used these individual
URLs and the manifest for prefetching. Current Tanren uses the optional unit packs
above and does not fetch individual word URLs during study.

### Reproducibility

- Model: AnythingXL (SDXL), local ComfyUI
- Recipe: steps 26, CFG 7, euler_ancestral, 1344x768 → 672x384 webp q82,
  base seed = first 4 bytes of SHA1(key)
- Fixed style prefix/suffix and negative prompt are pinned in the app repo's
  `tools/comfyui/generate_scenes.py`. Reviewed alternatives may add a documented
  seed offset; the selected effective seed and prompt are recorded in the
  generation log kept with the workstation outputs.
- Images contain no readable text by design (quiz answers must not leak).

### License note

Images are AI-generated with a community SDXL checkpoint for use as learning-app
assets. No third-party trademarks, real persons, or reproductions of existing
artworks are intended.

## Legacy: word illustration packs (flat-illust-v1)

Per-word mascot illustration zips for the earlier eitan-app, distributed via
GitHub Releases (eiken_5 .. eiken_pre1). Retained for earlier apps; current Tanren
uses `packs/v1/`.
