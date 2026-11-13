# Store screenshot specs

Checked against the official pages on **2026-11-13**. Both stores change these without much notice, so confirm in App Store Connect / Play Console before uploading and mention that to the user.

Sources:

- Apple: https://developer.apple.com/help/app-store-connect/reference/app-information/screenshot-specifications
- Google: https://support.google.com/googleplay/android-developer/answer/9866151

## App Store (iOS / iPadOS)

General: 1 to 10 screenshots per device size and localization. `.png`, `.jpg` or `.jpeg`. No alpha channel or transparency. If the UI is the same across sizes, upload only the largest size and App Store Connect scales it down for smaller ones.

| Slot (Apple's label) | Example devices | Portrait sizes (px) | Status |
| --- | --- | --- | --- |
| iPhone with Dynamic Island (large display), often called 6.9" | 17 Pro Max, 16 Pro Max, Air | 1320×2868, 1290×2796, 1260×2736 | Recommended: upload this set |
| iPhone with Face ID (large display), 6.5" | 11 Pro Max, XS Max | 1284×2778, 1242×2688 | Required only if no 6.9" set is provided |
| iPhone with Dynamic Island (medium display), 6.3" | 17, 17 Pro, 16 | 1206×2622, 1179×2556 | **Uncertain**: see note |
| iPad 13" | iPad Pro 13" | 2064×2752, 2048×2732 | Required if the app runs on iPad |
| iPhone Duo (outer / inner) | iPhone Duo | 1398×2034 / 2007×2853 | Optional now. Apple says it will be required from April 2027 for apps built with the iOS 27.1 SDK or later. Adds a badge to the product page. |

Landscape uses the same numbers swapped.

> **Note (uncertain):** As of 2026-11, Apple's page says "At least one screenshot for iPhone with Dynamic Island (medium display)" is required. The same page also says the medium slot falls back to scaled screenshots from the large slots. Until this is clear, upload a 6.9" set and check in App Store Connect whether the medium slot shows as missing. If it does, also export 1206×2622.

## Mac App Store

- 1 to 10 screenshots, 16:10, landscape.
- One of: 1280×800, 1440×900, 2560×1600, **2880×1800**.
- Same format rules as iOS (no transparency).

## Google Play

- Phone: **2 to 8** screenshots. JPEG or 24-bit PNG (no alpha). Each side from 320 to 3840 px, and the long side can be at most 2× the short side.
- For promotion eligibility (recommended): at least **4** screenshots at **1080 px** or larger. Portrait 1080×1920 (9:16) or landscape 1920×1080 (16:9). For games: at least 3, showing gameplay.
- Text on screenshots: Google says taglines should not take up more than **20%** of the image.
- Tablets / Chromebooks: at least 4, 1080 to 7680 px, 16:9 or 9:16.
- Feature graphic: **1024×500**, JPEG or 24-bit PNG, required.
- Wear OS, TV, Automotive and XR have their own rules. See the source page.

## Things not to put in screenshots

- Another platform's name or devices (no Android hardware in App Store images, and the reverse).
- Prices, "free" or discounts, unless they're true in every region where the listing appears.
- Rankings or awards you can't cite.
- Real people's personal data in demo content.
