# `.mockshot` project format (for MockShot Studio)

A `.mockshot` file is a UTF-8 JSON document. MockShot Studio opens it in the Mac app (double-click or File > Open) and in the browser editor at https://mockshot.studio (open or drag the file in). Generating one lets the user start from your slide plan instead of a blank canvas.

A full example is in [example.mockshot](example.mockshot).

## Root

| Field | Type | Value |
| --- | --- | --- |
| `schemaVersion` | number | Always `1` |
| `metadata.displayName` | string | Project name, e.g. `"Acme – App Store"` |
| `activePresetId` | string | Export size for the whole file (table below) |
| `exportBackground` | object | Optional default background: `{ "presetId": "<id>" }` or `{ "presetId": "custom", "customColor": "#RRGGBB" }` |
| `slides` | array | At least one slide |
| `activeSlideIndex` | number | `0` |

Each file has one export size. To cover several stores, write one file per store.

| `activePresetId` | Export size | Use `mock.deviceId` |
| --- | --- | --- |
| `preset-app-store-iphone-17-portrait-default` | 1290×2796 (App Store iPhone 6.9") | `iphone-17` |
| `preset-app-store-mac-2880x1800` | 2880×1800 (Mac App Store) | `macos-window` |
| `preset-app-store-iphone-duo-outer-portrait` | 1398×2034 (iPhone Duo outer) | `iphone-duo-outer` |
| `preset-app-store-iphone-duo-inner-portrait` | 2007×2853 (iPhone Duo inner) | `iphone-duo-inner` |
| `preset-google-play-phone-portrait-default` | 1080×1920 (Google Play phone) | `google-pixel-generic` |

## Slide

```json
{
  "id": "slide-1",
  "screenshot": { "kind": "empty" },
  "mock": { "deviceId": "iphone-17", "scale": "relaxed" },
  "layout": { "mode": "auto-stack", "copyBelowMock": false, "textAlign": "center" },
  "mainMessage": { "text": "Split bills in ==seconds==", "position": "above-mock", "fontSizePx": 37 },
  "caption": { "enabled": false, "text": "", "position": "below-main" },
  "zoomCallouts": []
}
```

| Field | Required | Notes |
| --- | --- | --- |
| `id` | yes | Unique string per slide |
| `screenshot` | yes | `{ "kind": "empty" }`, or `{ "kind": "embedded", "mimeType": "image/png", "dataBase64": "<base64>" }` to include a captured screen. Embedding makes the file large, so usually leave it empty and let the user drop screenshots in. |
| `mock.deviceId` | yes | Matches the size, see the table above |
| `mock.scale` | yes | `relaxed` (default), `tight` or `ultra-tight`: how large the device is drawn |
| `mainMessage.text` | yes | The headline. `==word==` highlights a word and `[[word]]` puts it in a box. Use `\n` for a manual line break. |
| `layout` | no, but set it | Decides where the text goes: `{ "mode": "auto-stack", "copyBelowMock": false }` puts the headline above the device, and `true` puts it below. `textAlign` is `left`, `center` or `right`. |
| `mainMessage.position` | yes | Older field: `above-mock` or `below-mock`. If `layout` is set, `layout` decides the placement, so keep the two consistent. |
| `mainMessage.fontSizePx` | yes | 12 to 96. `37` is the app's default. |
| `caption` | yes | Supporting line. `enabled` is a boolean, and `position` is `above-main` or `below-main`. |
| `zoomCallouts` | yes | `[]` |
| `exportBackground` | no | Per-slide background. Same shape as the root field. |

Background preset ids include `gradient-cool-pearl`, `gradient-warm-cream`, `gradient-dark-midnight`, `gradient-dark-navy`, `pure-white`, `deep-black`, `solid-navy`, `matte-cobalt`, `matte-teal`, `matte-scarlet`, and for Mac `desktop-sequoia`, `desktop-coast-morning`. Unknown ids fall back to the default, so they don't break the file.

Write the file next to the user's project (for example `store-screenshots/acme-app-store.mockshot`). Don't overwrite an existing `.mockshot` without asking.
