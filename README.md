# eitan-image-packs

Public image assets for the private eitan learning apps.

## scenes/ — example-sentence scene illustrations (flat-scene-v1)

One illustration per vocabulary word, depicting the word's example sentence as a
memory cue. Served directly via raw URLs:

```
https://raw.githubusercontent.com/SHAYOUWORLD/eitan-image-packs/main/scenes/<key>.webp
```

By default, `<key>` = word lowercased, non-ASCII-alphanumeric characters replaced
with `_`. Explicit sense overrides prevent collisions: the verb `carry on` uses
`carry_on_continue`, while the noun `carry-on` keeps `carry_on`.
`scenes/manifest.json` lists every available key (used by apps to prefetch packs
without probing 404s).

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
GitHub Releases (eiken_5 .. eiken_pre1). Superseded by scenes/ for new apps.
