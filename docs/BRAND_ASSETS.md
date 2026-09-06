# ZaibWall Brand Assets

This directory is reserved for the approved visual assets.

## Required logo files

When the approved source logo files are available, place them here using these stable names:

```text
assets/brand/zaibwall-mark.svg
assets/brand/zaibwall-mark-light.svg
assets/brand/zaibwall-mark-dark.svg
assets/brand/zaibwall-lockup.svg
assets/brand/zaibwall-app-icon.png
assets/brand/zaiblabs-mark.svg
```

For the app itself, prefer SVG for scalable marks and PNG only where a platform store/icon pipeline requires raster output.

## Source-of-truth rule

Do not generate replacement logo geometry in code. The approved logo artwork supplied by the product owner is canonical.

## App icon

The app icon should use the standalone ZaibWall Z mark, centered with appropriate platform safe area/padding. Generate required Android adaptive-icon and iOS App Store exports from the approved master artwork.

## Zaib Labs

The user's separately created Zaib Labs logo is the parent/studio mark. Keep it visually distinct from the ZaibWall product mark. Do not merge the two logos into one application icon unless explicitly requested.

## Missing binary assets

The repository currently contains the documentation/specification layer. Binary logo files should be added only from the approved source artwork so the implementation does not accidentally use an approximate or incorrect logo.
