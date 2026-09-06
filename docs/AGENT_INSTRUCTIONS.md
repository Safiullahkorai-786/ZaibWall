# OpenCode Agent Instructions — ZaibWall

You are implementing ZaibWall, a production-quality Flutter wallpaper app. Treat `docs/` as the project source of truth.

## Before coding
1. Read `docs/PRODUCT_SPEC.md`.
2. Read `docs/BRAND_GUIDE.md`.
3. Read `docs/ARCHITECTURE.md`.
4. Read `docs/UI_UX.md`.
5. Read `docs/ROADMAP.md`.
6. Inspect the existing repository before changing files.
7. Verify current stable Flutter/Dart compatibility and current package APIs before selecting versions.

## Engineering behavior
- Plan before making broad changes.
- Prefer small, reversible commits.
- Keep domain/data/platform boundaries clean.
- Do not put Supabase, AdMob, local database, or MethodChannel calls directly in widgets.
- Do not introduce paid infrastructure without explicit approval.
- Do not commit secrets.
- Use test implementations/mocks for external services.
- Run formatter, analyzer, tests and relevant platform builds after meaningful changes.
- Fix root causes rather than suppressing analyzer errors.
- Do not add dependencies when Flutter/Dart/platform APIs already solve the problem adequately.
- Check package maintenance, platform compatibility and license before adding third-party packages.

## Design behavior
- Follow `BRAND_GUIDE.md` exactly.
- No purple AI aesthetic.
- Wallpaper imagery is the visual hero.
- Use glassmorphism selectively and provide reduced-blur behavior for low-end devices.
- Do not invent additional navigation tabs without a product decision.
- Prefer simple, fast interactions over feature density.

## Performance behavior
- Treat low-end/older devices as first-class targets.
- Thumbnail-first image loading.
- Lazy lists/grids.
- Bounded cache.
- Avoid large memory allocations and unnecessary rebuilds.
- Avoid full-resolution image decoding until needed.
- Profile before optimizing blindly.

## Offline behavior
Local content must render without waiting for network. Saved and Recently Used are local-first. Remote refresh is background work.

## Ads
AdMob is monetization, not a core dependency. Use test IDs during development. Keep ad frequency configurable and compliant with current platform/privacy/store rules. Never fake ad success or make an ad failure look like a wallpaper failure.

## Platform behavior
Do not claim that Home/Lock/Both is supported on a platform until it has been verified on the target OS/device. Implement honest platform-specific behavior.

## Definition of done
A feature is not done when it merely compiles. It must:
- fit the architecture
- follow the brand
- handle loading/error/offline states
- avoid obvious performance regressions
- be testable
- work on both target platforms when applicable
- document any platform limitation
