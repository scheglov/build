## 0.3.2

- Support for build 0.9.0

## 0.3.1+1

- Bug Fix: Update AssetGraph version so builds can be run without manually
  deleting old build directory.
- Bug Fix: Check for unreadable assets in an async method rather than throw
  synchronously

## 0.3.1

- Internal refactoring of RunnerAssetReader.
- Support for build 0.8.0
- Add findAssets on AssetReader implementations
- Limit Asset reads to those which were available at the start of the phase.
  This might cause some reads which uses to succeed to fail.

## 0.3.0

### Bug Fixes

- Fixed a race condition bug [175](https://github.com/dart-lang/build/issues/175)
  that could cause invalid output errors.

### Breaking Changes

- `RunnerAssetWriter` now requires an additional field, `onDelete` which is a
  callback that must be called synchronously within `delete`.

## 0.2.0

Add support for the new bytes apis in `build`.

### New Features

- `FileBasedAssetReader` and `FileBasedAssetWriter` now support reading/writing
  as bytes.

### Breaking Changes

- Removed the `AssetCache`, `CachedAssetReader`, and `CachedAssetWriter`. These
  may come back at a later time if deemed necessary, but for now they just
  complicate things unnecessarily without proven benefits.
- `BuildResult#outputs` now has a type of `List<AssetId>` instead of
  `List<Asset>`, since the `Asset` class no longer exists. Additionally this was
  wasting memory by keeping all output contents around when it's not generally
  a very useful thing outside of tests (which retain this information in other
  ways).

## 0.0.1

- Initial separate release - split off from `build` package.