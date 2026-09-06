# ZaibWall Technical Architecture

## Stack

- Flutter (stable channel; agent must verify current stable version before implementation)
- Dart
- Riverpod for state management/dependency injection
- Supabase for remote metadata/backend services where the free tier is sufficient
- Local database: choose a lightweight, actively maintained Flutter-compatible option after verifying current package/platform support; Isar or Hive are acceptable candidates, but the agent must validate the current ecosystem before locking one
- Image cache: use a maintained Flutter image-cache package or a carefully bounded native/disk cache abstraction
- AdMob: official/current Google Mobile Ads Flutter integration, using test IDs in development
- Native platform bridge: MethodChannel/platform interface for wallpaper-setting functionality where Flutter/plugin support is insufficient

## Architectural style

Feature-first + repository pattern + dependency inversion.

```text
UI
  -> Riverpod providers/controllers
      -> Repositories
          -> Remote data source (Supabase/API)
          -> Local data source (database)
          -> File/image cache
          -> Platform services
```

The UI must not directly call Supabase, platform channels, or ad SDK APIs.

## Suggested structure

```text
lib/
  app/
    app.dart
    router.dart
    providers.dart
  core/
    constants/
    errors/
    network/
    theme/
    utils/
    widgets/
  features/
    home/
    categories/
    search/
    wallpaper_detail/
    saved/
    recently_used/
    settings/
  data/
    models/
    repositories/
    datasources/
      remote/
      local/
  services/
    ads/
    connectivity/
    image_cache/
    wallpaper/
    sharing/
    rating/
  main.dart
```

The exact structure may evolve, but keep boundaries explicit.

## Remote data

Minimum tables:

### wallpapers
- id
- title
- category_id
- image_url
- preview_url
- thumbnail_url
- width
- height
- orientation
- tags
- is_featured
- is_active
- created_at
- updated_at

### categories
- id
- name
- slug
- thumbnail_url
- sort_order
- is_active

Optional later fields should not be added merely for speculation.

## Security

- Enable Row Level Security for Supabase tables.
- Public/mobile clients should receive only the data required by the app.
- Never embed service-role keys in Flutter.
- Keep write/admin operations outside the public mobile client.
- Use a separate admin/content workflow for publishing wallpapers.

## Data flow

### Online
```text
App start
 -> local state rendered immediately
 -> connectivity check
 -> remote metadata refresh
 -> repository merges remote/local state
 -> UI updates
```

### Offline
```text
App start
 -> local database/cache
 -> Saved + Recently Used + cached wallpapers
 -> no blocking network spinner
```

### Wallpaper apply
```text
User opens detail
 -> choose Home/Lock/Both
 -> verify required image is locally available
 -> optionally prepare/show eligible ad
 -> native wallpaper service
 -> success
 -> write Recently Used locally
```

Do not mark a wallpaper Recently Used until the apply operation succeeds.

## Platform abstraction

Create an interface such as:

```dart
abstract interface class WallpaperPlatformService {
  Future<bool> setHome(String localImagePath);
  Future<bool> setLock(String localImagePath);
  Future<bool> setBoth(String localImagePath);
  Future<bool> isSupported(WallpaperTarget target);
}
```

Do not assume iOS and Android expose identical wallpaper-setting capabilities. Verify current platform behavior and App Store/Play policies before implementation. Where a requested target is unsupported, provide a truthful platform-specific UX instead of a fake success.

## Performance requirements

- Lazy-load lists/grids.
- Use thumbnails in grids.
- Never decode full-resolution images unnecessarily.
- Limit concurrent image downloads.
- Bound disk cache.
- Protect Saved content from ordinary cache eviction.
- Avoid large in-memory image collections.
- Avoid nested/unbounded scroll views.
- Minimize expensive blur/backdrop filters on low-end hardware.
- Avoid unnecessary rebuilds; use Riverpod selectors/family providers where appropriate.
- Keep animations short and limited.
- Profile release builds on physical low/mid-range Android hardware.

## Configuration

Environment-specific values must be injectable/build-configurable:
- Supabase URL
- Supabase anon/public key
- AdMob application/ad unit IDs
- feature flags
- content/API endpoints

Never commit private secrets.
