# ZaibWall Implementation Roadmap

## Phase 0 — Foundation
- Initialize Flutter project for Android/iOS.
- Establish linting, formatting, analysis options and folder boundaries.
- Add theme/design tokens.
- Add environment configuration strategy.
- Create architecture tests/checklist.

## Phase 1 — UI prototype
- Build Home, Categories, Search, Detail, Saved, Settings.
- Use local mock wallpaper data.
- Implement brand system and responsive layouts.
- No backend or ads yet.

## Phase 2 — Remote catalog
- Create Supabase schema/migrations.
- Implement repository/data-source boundaries.
- Fetch categories and wallpaper metadata.
- Add pagination/incremental loading.
- Add image thumbnail/preview/full URL handling.

## Phase 3 — Local/offline layer
- Add local database.
- Add Saved and Recently Used repositories.
- Add bounded disk image cache.
- Add connectivity observation.
- Make local rendering immediate on cold start.
- Implement online-to-local synchronization/merge rules.

## Phase 4 — Wallpaper application
- Implement Android native integration.
- Verify Home/Lock/Both behavior on supported Android versions.
- Implement iOS integration only according to actual supported capabilities and current store/platform rules.
- Add clear unsupported-state UX.
- Record Recently Used only after successful application.

## Phase 5 — Monetization
- Integrate current official Google Mobile Ads Flutter package/API.
- Use test IDs in development.
- Implement consent/privacy requirements applicable to target markets/platforms.
- Add configurable ad cooldown/frequency.
- Ensure ad failure never destroys the core wallpaper flow.

## Phase 6 — Content operations
- Establish a private admin/content publishing workflow.
- Upload approved AI-generated wallpapers.
- Generate optimized thumbnail/preview/full variants.
- Publish metadata without requiring a mobile app update.

## Phase 7 — Quality/performance
- Test offline/online transitions.
- Test cache eviction and Saved protection.
- Profile memory while scrolling large catalogs.
- Test slow networks and image failures.
- Test low-end Android devices and older supported iPhones.
- Verify accessibility and text scaling.

## Phase 8 — Release readiness
- Privacy policy
- Store metadata/screenshots
- App icon/assets
- AdMob production configuration
- Crash/error monitoring if a suitable free tier is available
- Legal/store policy review
- Release signing and CI

## Phase 9 — Post-launch
Only after real usage data exists:
- Trending
- Better recommendations
- Additional categories
- Optional rewarded ads
- Content quality improvements
- Storage controls
- More platform-specific enhancements

Do not add features simply because they are technically possible. Let user behavior justify expansion.
