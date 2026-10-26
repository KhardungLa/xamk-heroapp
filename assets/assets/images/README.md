# Images

Anything dropped in here is bundled automatically — `pubspec.yaml` declares the
whole folder, not individual files, so adding artwork needs no code change.

```dart
Image.asset('assets/images/logo.png', height: 32)
```

## Formats

**PNG** works out of the box. Supply resolution variants beside the base file
and Flutter picks the right one per device:

```
assets/images/logo.png        # 1x
assets/images/2.0x/logo.png   # same image, twice the pixels
assets/images/3.0x/logo.png
```

Reference the 1x path only; the variants are found by convention.

**SVG** is drawn with the `flutter_svg` package, already a dependency — the
Hub logo and its brackets are. Use `SvgPicture.asset(...)` rather than `Image.asset`.
`flutter_svg` does not read CSS, so an exported SVG whose fills sit in a
`<style>` block of classes needs them written onto each element as `fill`
attributes first. See the README's "The Hub masthead".

## What does *not* belong here

The home-screen icon and the launch screen are not assets — they are
platform files under `android/` and `ios/`. See the README's
"Bringing in artwork" section.
