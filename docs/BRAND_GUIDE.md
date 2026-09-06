# ZaibWall Brand Guide

## Brand architecture

- Product: **ZaibWall**
- Studio/publisher direction: **Zaib Labs**
- Developer identity: **Safiullah Korai**
- Do not use "AI" as the main visual or naming theme. AI is the content-generation pipeline, not the product personality.

## Visual personality

Premium, calm, modern, editorial, minimal, confident and slightly futuristic.

Avoid:
- purple AI gradients
- neon cyberpunk styling
- excessive glow
- dashboard-like cards everywhere
- excessive glass blur
- crowded controls

Prefer:
- wallpaper-first layouts
- generous spacing
- dark/slate surfaces
- restrained translucent glass
- subtle borders
- rounded geometry
- strong image presentation
- minimal iconography

## Existing brand-kit baseline

The previously defined ZaibWall direction uses **Midnight + Electric Lime**.

Core colors:
- Midnight Navy: `#0B1220`
- Deep Slate: `#121B2F`
- Electric Lime: `#C7F36B`
- Soft Lime Highlight: `#E7F9B4`

Use the above as the canonical starting palette. Do not invent a competing purple palette.

### Usage
- Midnight Navy: primary dark background
- Deep Slate: elevated surfaces and secondary backgrounds
- Electric Lime: primary accent, selected states, key CTA emphasis
- Soft Lime Highlight: restrained highlight/hover/pressed treatment

For light theme, derive neutral surfaces from the same brand system rather than introducing a new colorful identity. Keep contrast accessible.

## Typography

Primary typeface direction from the brand kit:
- **Plus Jakarta Sans** — preferred primary font
- **Manrope** — approved alternative if a technical constraint makes Jakarta Sans unsuitable

Use a consistent type scale. Suggested semantic roles:
- Display: bold, short headlines only
- Heading: semibold
- Body: regular/medium
- Label: medium/semibold

Do not mix multiple unrelated font families.

## Logo system

The ZaibWall mark is a standalone geometric **Z monogram** built from two interlocking diagonal ribbon-like forms. The center negative space creates a subtle tile/spark/wallpaper impression. Geometry should have rounded corners/ends and remain recognizable at small sizes.

Required asset variants when source files are available:
- app icon / square mark
- standalone transparent mark
- monochrome dark mark
- monochrome light mark
- horizontal lockup with `ZaibWall`
- social/store icon exports

Do not redraw the mark in Flutter with arbitrary SVG geometry. Treat the approved source asset as canonical.

## Glassmorphism rules

Glass is a supporting material, not the entire UI.

Use it for:
- floating navigation
- compact filter/category controls
- overlay controls on wallpaper previews
- important floating actions

Avoid blur on every card or every list item. On low-end devices, provide a visually similar translucent surface with reduced/no blur.

Recommended visual recipe:
- translucent neutral surface
- subtle 1px border
- modest backdrop blur only where performance permits
- soft shadow/elevation
- 16–24px corner radius depending on component

## Iconography

Use a single consistent icon family. Prefer platform-appropriate outlined/rounded icons. Do not mix random icon packs.

## Motion

Motion should be subtle and purposeful:
- short fade/scale transitions
- image loading crossfade
- pressed states
- navigation transitions

Respect reduced-motion/accessibility preferences where platform support permits.

## Brand copy

Tone: concise, calm, confident.

Preferred examples:
- `Beautiful wallpapers. Zero clutter.`
- `Find your next wallpaper.`
- `Saved for offline.`
- `You're offline — showing available wallpapers.`

Avoid exaggerated AI marketing language.
