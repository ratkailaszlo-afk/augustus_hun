# Augustus Hungarian Localization (hu)

This branch adds full Hungarian localization support for Augustus and fixes
Hungarian diacritic rendering issues.

## What Is Included

- Hungarian language detection in `locale.c`
- Hungarian language enum and translation loader wiring
- Hungarian translation table: `src/translation/hungarian.c`
- Hungarian language file loading support (`c3.hun`, `c3_mm.hun`, editor files)
- Hungarian-specific encoding mode to fix wrong accented character rendering

## Build

```bash
cd /path/to/augustus
cmake -S . -B build
cmake --build build -j
```

## Install (macOS app bundle)

Copy the built executable into your `augustus.app`:

```bash
cp -f build/augustus.app/Contents/MacOS/augustus /path/to/augustus.app/Contents/MacOS/augustus
```

## Game Data Requirements

This localization expects Hungarian Caesar III text resources in the game
directory, e.g.:

- `c3.eng`
- `C3_mm.eng`

Optional dedicated Hungarian files are also supported:

- `c3.hun`
- `c3_mm.hun`
- `c3_map.hun`
- `c3_map_mm.hun`

## Verification

On startup, `augustus-log.txt` should contain:

- `Detected language: Hungarian`
- `Detected encoding: 12503`

## Notes

- The `12503` internal encoding mode is intentionally added for Hungarian.
  It uses cp1250 conversion rules with Hungarian-compatible font mapping.
- This prevents common wrong letter substitutions in UI text.
