# ZaibWall Product Specification

> Source of truth for the OpenCode implementation agent. Read this before changing application architecture, UI, dependencies, or data flow.

## 1. Product

**ZaibWall** is a lightweight, premium wallpaper discovery and application app for Android and iOS. Wallpapers are AI-generated and delivered remotely; AI should not dominate the visual identity or UX.

Core promise: **beautiful wallpapers, zero clutter.**

Publisher/studio direction: **Zaib Labs**. Developer identity: **Safiullah Korai**.

## 2. Product principles

1. Offline-first: previously loaded, saved, and recently used wallpapers remain useful without internet.
2. Small app package: never bundle the wallpaper catalog into the Flutter application.
3. Low-memory friendly: optimize image sizes, decoding, lists, caching, animations, and blur.
4. Minimal UX: no account required for v1; no social feed; no unnecessary settings.
5. Premium visual quality: restrained glassmorphism, not the generic purple/AI-dashboard aesthetic.
6. Online content is dynamic: categories, featured/new content, metadata and wallpaper URLs come from the backend.
7. Platform correctness: Android and iOS wallpaper-setting capabilities must be verified before implementation; use native platform bridges where required.
8. Monetization must not destroy UX: AdMob is primarily associated with wallpaper-apply moments and must use frequency/cooldown controls.
9. Free-first: use free/open-source packages and free service tiers while the product is pre-revenue. Do not introduce paid infrastructure unless explicitly approved.
10. No secrets in the repository. Production keys/configuration must use secure platform/build configuration.

## 3. V1 scope

### Home
- Featured wallpaper
- New wallpapers
- Recently used
- Compact category strip
- Online/offline state
- Pull to refresh when online

### Categories
Initial categories: Nature, Minimal, Dark, Abstract, Space, Cars, Architecture, Animals, Gaming, Anime, Aesthetic, AMOLED.

### Search
Simple text search over wallpaper title/tags/category. Avoid a complex search service in v1.

### Wallpaper detail
- Full preview
- Save/unsave
- Set Wallpaper
- Home Screen
- Lock Screen
- Both
- Loading/progress/error states

### Saved
Local saved wallpapers. No login required.

### Recently used
Local history of wallpapers successfully applied, newest first, with a sensible maximum count.

### Offline
When internet is unavailable, show locally available Saved, Recently Used, and cached wallpapers. Never present an empty/dead app merely because the network is unavailable.

### Settings
- Theme: System / Light / Dark
- Rate Us
- Share App
- Privacy Policy
- About
- Other Apps
- Feedback
- Report Wallpaper
- Storage/cache management if useful

## 4. Explicit non-goals for v1

Do not implement unless later approved:
- Accounts/authentication
- Profiles
- Comments
- Likes/following
- In-app AI generation
- Live/video wallpapers
- Social feed
- Complex personalization engine
- Excessive customization
- Large bundled asset library

## 5. Image strategy

Use a three-level remote image pipeline:
- thumbnail for grids
- preview for detail screen
- full-resolution image only when required for applying/saving

Do not decode full-resolution images for every visible grid card.

Recommended publishing pipeline:
AI generation -> human review -> crop/resize -> thumbnail/preview/full variants -> optimization -> object storage/CDN -> metadata publication.

The exact CDN/object-storage provider may change. Keep it behind a repository/data-source abstraction.

## 6. Offline model

Distinguish these concepts:
- Cache: disposable locally cached images.
- Saved: user explicitly saved wallpaper; should survive normal cache eviction.
- Recently Used: local record of successfully applied wallpaper IDs and local availability.

On startup:
1. Read local state immediately.
2. Render useful local content without waiting for network.
3. If online, refresh remote metadata/content in the background.
4. Merge remote and local state safely.

## 7. Monetization

Google AdMob is planned. Ads must be configured according to current platform/store requirements and consent/privacy rules.

Preferred v1 behavior:
- no persistent banner over the main wallpaper experience
- an interstitial may become eligible around wallpaper-apply actions
- use a cooldown/frequency cap
- never show an ad during a critical loading/error state
- do not make ad loading block the entire app indefinitely
- use test ad IDs during development

The exact ad frequency must be configurable rather than hard-coded throughout UI code.

## 8. Success criteria

A first-time user should be able to:
1. Open the app.
2. See useful wallpapers quickly.
3. Open a wallpaper.
4. Save it.
5. Apply it.
6. Return later with no internet and still see Saved/Recently Used content.

The app should feel fast on low-end Android devices and older supported iPhones, not only modern flagship hardware.
