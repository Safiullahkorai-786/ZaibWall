# ZaibWall UI / UX Specification

## Navigation

Keep primary navigation to three destinations:

1. Home
2. Categories
3. Saved

Settings is a top-level action from the Home/app bar rather than a fourth primary tab.

## Home hierarchy

1. Compact app header + Settings
2. Featured/hero wallpaper
3. Categories horizontal strip
4. Recently Used
5. New Wallpapers
6. Empty/offline states where appropriate

Do not create a long homepage containing every possible section.

## Wallpaper grid

Use a responsive, memory-conscious grid. Cards should prioritize image area over text. Metadata should be minimal.

## Detail screen

Wallpaper is the hero. Controls float over or below it using restrained glass surfaces.

Primary action: `Set Wallpaper`

Secondary actions: Save/share where appropriate.

Target selection:
- Home Screen
- Lock Screen
- Both

The selection should be simple and understandable, not a settings form.

## Offline UX

When offline:
- retain app navigation
- show a small offline status rather than a blocking dialog
- render Saved and Recently Used from local storage
- render available cached content
- disable/handle actions that truly require network without making the whole app unusable

Suggested copy: `You're offline — showing available wallpapers.`

## Empty states

Saved empty: `No saved wallpapers yet.` + browse action.

Recently Used empty: `Your recently applied wallpapers will appear here.`

Offline with no cache: `You're offline and there are no cached wallpapers yet.` + explain that content will appear after reconnecting.

## Theme

System / Light / Dark.

Dark theme should be the strongest visual expression of the brand, using Midnight Navy and Deep Slate with Electric Lime as a controlled accent.

Light theme should remain clean and premium, not simply invert every dark color.

## Glass components

Use glass for floating/important controls, not every surface. Provide a reduced-blur/no-blur fallback for performance.

## Accessibility

- readable contrast
- semantic labels for icon buttons
- minimum practical touch targets
- avoid color-only state indicators
- support system text scaling without catastrophic overflow
- respect platform accessibility/reduced-motion behavior where feasible

## Error handling

Never show raw exceptions to users.

Examples:
- network failure -> offline/try again state
- image failure -> placeholder + retry
- wallpaper service failure -> actionable platform-specific error
- ad failure -> continue the requested flow when safe; ads are not a core dependency

## UX rule

Every screen must answer one question quickly. If a proposed component does not improve discovery, saving, applying, offline usefulness, or necessary app management, remove it.
