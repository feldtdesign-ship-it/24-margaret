# 24 Margaret Street, the Joy record

A public-records audit of the former Joy Elementary School, Fairbanks, compiled in one day, 12 September 2026. Draft. Not an offer.

**Live page:** https://feldtdesign-ship-it.github.io/24-margaret/

- `index.html` – the whole page. The carrying-cost meter, the building, the sixteen-month clock, the 2019 bond trail, the Borough Code pathways, what happens next, and the six blanks only the Borough can fill.
- `docs/joy-independent-analysis-v2.md` – the written analysis the page is built from, version 2: the Series U maturity schedule and 1 May 2029 call, Joy's pro rata share, Ordinance 2000-012 closed, the parcel record, Ordinance 2025-15 verbatim, the Title 16 clock.
- `docs/joy-independent-analysis-v1-first-pass.md` – version 1, kept as written.
- `assets/model/joy_map.glb` – the neighbourhood model, 174 KB Draco. The camera moves through it as you scroll, one stop per section.
- `assets/map/` – three plates rendered from the same Blender scene: ground and water, context buildings, Joy in gold. Ortho, 760 m across, north up. They are the poster when WebGL is unavailable, and the material for the card.
- `og.jpg` – the link preview card, the three plates composited.

## Run it

The model is a `.glb`, so a double-clicked `file://` page will not load it. Serve the folder:

```
python3 -m http.server 8000
```

Then open <http://localhost:8000/>.

## Deploy

GitHub Pages, deploy from branch, root of `main`. `.nojekyll` is in place so the asset folders are served.

## The model

Exported from the `Joy_MapPlate` scene in the Blender file (`Joy_Cam_*` cameras live in the main scene, same coordinate space). Four collections go out: `PLATE_ground`, `PLATE_bldg`, `Joy_Original_1960`, `Joy_Glazing`. Object names are prefixed `GROUND__`, `BLDG__`, `JOY__`, `GLZ__` at export so the page can colour them; the file is left with its original names.

Two things the page corrects in three.js rather than in the file:

- Context footprints are flat polygons about 11 m below Joy's ground level. They get a temporary 6 m solidify at export and are lifted to Joy's ground in the page. Heights are nominal.
- The landuse polygons are single tilted faces. The page flattens them onto the ground plane.

Roads, rail and water lines in the file are edge-only and do not export. The rendered plates carry them.

## Camera

glTF is Y-up. A Blender `(x, y, z)` becomes `(x, z, -y)` in three.js. The waypoint array `WP` in `index.html` is already in three.js space. The first five stops are the named Blender cameras: context aerial, top ortho, south-west hero, east low, north-east aerial. Each stop carries a `side` value that slides the camera so Joy lands in the half of the screen the card does not cover.

## Where the numbers come from

Every source is linked in Section Eight of the page and at the end of the version 2 document. The bond figures are the Borough's own: the 30 June 2025 audit (Note 10, Schedule 5) and the FY 2026-2027 budget (pages 426 to 431). The parcel is FNSB Property Search PAN 0093289. Joy's share of the outstanding bonds is pro rata arithmetic on the 2019 allocation and is labelled as such. The Borough's own figures are the Borough's. The $167,000 carrying-cost total is our arithmetic on the Borough's stated monthly rate and is an estimate, not an audit. Nothing here is legal or tax advice.

Compiled by dx/dt LLC.
