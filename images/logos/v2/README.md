# InboxAlly logos, v2

Published at `https://assets.inboxally.com/images/logos/v2/<file>`.

## Colors

| Use | Color |
| --- | --- |
| Blue (INBOX, the I) | `#0062ff` |
| Dark (ALLY, the A) on light backgrounds | `#292929` |
| White (ALLY, the A) on dark backgrounds | `#ffffff` |
| Red (the paper plane) | `#ff3333` |

## Wordmark

`logo__inboxally.svg` (light backgrounds) and `logo__inboxally_dark.svg` (dark backgrounds), with
PNG and JPEG exports.

## Square mark: the IA with the plane

Built from the wordmark's own paths, at one scale: its I, A and plane, with the I moved under the
A so that its left edge meets the A's bottom-left corner and their tops align. The plane keeps its
place over the A, as in the wordmark.

| File | What it is | Use it for |
| --- | --- | --- |
| `logo_square__inboxally.svg` | The mark, cropped to its edges, dark A | Light backgrounds, when the layout adds its own spacing |
| `logo_square__inboxally_dark.svg` | The same, white A | Dark backgrounds |
| `icon__inboxally.svg`, `icon__inboxally-{48,96,192,512,1024}.png` | The mark centered on a transparent square, at 80% of its height | App and connector icons on light backgrounds |
| `icon__inboxally_dark.svg`, `icon__inboxally_dark-{48,96,192,512,1024}.png` | The same, white A | App and connector icons on dark backgrounds |
| `icon__inboxally_badge.svg`, `icon__inboxally_badge-512.png` | The mark on a white rounded square | Anywhere the background is unknown, such as a directory listing |
| `icon__inboxally_apple-touch.svg`, `icon__inboxally_apple-touch-180.png` | The mark on a white square (iOS rounds the corners) | `apple-touch-icon` |
| `favicon.svg` | The icon, with the A switching to white in dark mode (`prefers-color-scheme`) | `<link rel="icon" type="image/svg+xml">` |

The dark A disappears on a dark background, so use a `_dark` file or the badge there, never the
light mark. `logo_square__inboxally.png` and `logo-light-1000x1000.png` are the earlier raster
exports of the same mark.
