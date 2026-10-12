# Contributing a theme

Thank you for adding to the Glass theme collection. Every theme here installs on a player with one press on the Catalog tab of the Glass Manager, and the players read this repository's index to know what is on offer. This page says what a theme zip must look like for that to work, and how it gets here.

## The short way

1. On the Themes tab of the Glass Manager, press **Package** on your theme. The zip downloads in the collection's layout, with a preview of every meter the theme holds, rendered on your own player.
2. Add the zip to the folder for its category and screen size, below, by pull request. Without a GitHub account, post it on the Volumio community forum and a maintainer places it.
3. Automation writes the catalog pages and the index. Players see the theme on their next Catalog refresh.

## Categories

| Folder | Holds | Use it for |
|--------|-------|------------|
| `templates_peppy_spectrum` | a meter theme together with its spectrum theme | any theme that draws a spectrum: **preferred** |
| `template_peppy` | a meter theme alone | a theme with no spectrum |
| `templates_spectrum` | a spectrum theme alone | a spectrum look meant for other themes |

The folder names are historic and stay as they are: the index and every player depend on them. Inside a category the path is `[width]/[height]/[name].zip`, the width padded to four digits:

```
templates_peppy_spectrum/0800/480/800x480_retro_wood.zip
template_peppy/1920/1080/1920x1080_cassette.zip
```

## What a zip holds

Package writes the layout below, and it is accepted in every category:

```
800x480_retro_wood.zip
  +-- 800x480_retro_wood/
        +-- preview.png
        +-- templates/
        |     +-- 800x480_retro_wood/
        |           +-- meters.txt
        |           +-- *.png, *.jpg (pictures)
        |           +-- fonts/ (optional)
        +-- templates_spectrum/
              +-- 800x480_retro_wood/
                    +-- spectrum.txt
                    +-- *.png (pictures)
```

A theme without a spectrum has no `templates_spectrum/` part. A zip made by hand may also hold the theme folder alone, `800x480_retro_wood/meters.txt` and its pictures at the top, with `preview.png` beside them; the index reads both layouts. Do not put a README in the zip: the pages are generated.

| File | Required | What it is |
|------|----------|------------|
| `meters.txt` | for a meter theme | the meters, one `[section]` each |
| `spectrum.txt` | for a spectrum theme | the spectrum looks, one `[section]` each |
| `preview.png` | yes | the picture shown in the catalog; Package renders one with every meter tiled |
| pictures | yes | everything the text names: background, foreground, needles, records, reels, masks |
| fonts | optional | a font the theme brings, named by `font.path` in its text |

The theme's folder name inside `templates/` and inside `templates_spectrum/` must be the same, and the same as the zip's name: Glass pairs a meter theme with its spectrum theme by that name.

## Naming

`WIDTHxHEIGHT_name`, with underscores and no spaces: `1280x720_retro_vfd`, `3840x2160_amber`. The size comes first because Glass reads it from the name: the Catalog filters by it, Fit scales by it, and Tailor cuts copies from it. No version numbers in the name; a new version replaces the zip.

## Installing, for reference

On a player, the Catalog tab of the Glass Manager installs any theme here with one press, and the Themes tab's **Upload a theme zip** installs a zip from your computer in any of the layouts above. By hand, the theme folder goes under `/data/INTERNAL/glass/templates/` and the spectrum folder under `/data/INTERNAL/glass/templates_spectrum/`.

## Bundles

One `meters.txt` may hold several `[sections]`: one theme, several meters, one card in the Manager, and the pages list every meter. A bundle is the way to offer one deck with several looks.

## Themes for another screen

Tailor, on the Themes tab, cuts a copy of any theme to another screen size, every coordinate and picture scaled, and Package sends the copy here. A cut copy is welcome as a theme of its own, named by its new size, with the original credited. The [Tailor](https://github.com/foonerd/glass/wiki/Tailor) page has what the cutter does and where the last mile is yours.

## Before you submit

- The zip was made by Package, or is laid out as above with the folder names matching.
- Every picture and font the text names is in the folder.
- The preview shows the theme with a track playing.
- The theme was looked at on a player at its own size: text readable, nothing cut off, needles and bars where they belong.
- Pictures and fonts that are not yours are credited, with a licence that allows sharing.

## Pull requests

Fork the repository, make a branch, add the zip at its path, push and open a pull request. Say what the theme is, its size and category, what player and screen it was tried on, and the credits for any picture or font that is not yours. Maintainers with push access add zips to `main` directly. After a merge the automation regenerates the pages and the index; nothing else needs editing.

## Pictures

| Picture | Format | Notes |
|---------|--------|-------|
| Background | PNG or JPG | the theme's full size |
| Foreground | PNG | with transparency, drawn over everything |
| Needle, bar | PNG | with transparency |
| Record, reel | PNG | with transparency; turned by Glass |
| Tonearm | PNG | with transparency; drawn at its pivot |
| Album art mask | PNG | with transparency |
| Preview | PNG or JPG | the theme's size or smaller |

## Reference

The [Glass wiki](https://github.com/foonerd/glass/wiki) has every key a theme may use: [Meters-Reference](https://github.com/foonerd/glass/wiki/Meters-Reference) for `meters.txt`, [Spectrum](https://github.com/foonerd/glass/wiki/Spectrum) for `spectrum.txt`, and [Themes](https://github.com/foonerd/glass/wiki/Themes) for the folders, the fonts and the review tools. The older summaries in this repository, [METERS.md](docs/METERS.md) and [SPECTRUM.md](docs/SPECTRUM.md), cover the keys the previous engine knew.
