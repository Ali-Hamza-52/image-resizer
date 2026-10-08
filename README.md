# App Store Screenshot Resizer

A single-file web app that turns your app screenshots into every size App Store Connect accepts. Everything runs in your browser. Your images are never uploaded anywhere.

## Quick start

1. Open `appstore-resizer.html` in any modern browser (Chrome, Edge, Safari, Firefox).
2. Drop your screenshots onto the upload area, click it to browse, or paste an image with Ctrl+V / Cmd+V.
3. Choose devices, sizes and output settings.
4. Click **Generate screenshots**.
5. Download images one by one, or click **Download all** to get a .zip.

There is nothing to install. An internet connection is only needed for the fonts and for the **Download all (.zip)** button. Single downloads work offline.

## Supported sizes

| Device | Displays | Portrait | Landscape |
|---|---|---|---|
| iPhone with Dynamic Island | 6.1″ / 6.3″ | 1179 × 2556, 1206 × 2622 | 2556 × 1179, 2622 × 1206 |
| iPhone Duo | — | 1398 × 2034, 2007 × 2853 | 2034 × 1398, 2853 × 2007 |
| iPad | 12.9″ / 13″ | 2048 × 2732, 2064 × 2752 | 2732 × 2048, 2752 × 2064 |
| Apple Watch | Ultra 4, Series 12, 9, 6, 3 | 410 × 502, 422 × 514, 416 × 496, 396 × 484, 368 × 448, 312 × 390 | — |

App Store Connect accepts up to 10 screenshots per device. The app enforces the same limit.

## Settings

**Devices.** Turn each device on or off with its switch. Click a size chip (for example `312×390`) to skip just that size.

**Fit**

- **Fill & crop.** Fills the whole frame and trims the edges if the shapes differ. A badge shows how much was cropped when it's 3% or more.
- **Fit & pad.** Keeps the whole screenshot and adds bars in the pad color you choose.
- **Stretch.** Resizes to the exact size. This can distort the image.

**Orientation**

- **Auto.** Portrait screenshots become portrait sizes, landscape screenshots become landscape sizes.
- **Portrait** or **Landscape.** Forces one orientation.
- **Both.** Creates both orientations.

Apple Watch is always portrait.

**Format.** PNG, or JPG at 95% quality. Every image is saved fully opaque, because App Store Connect rejects screenshots with transparency.

## Output

The zip is organized by device:

```
appstore-screenshots.zip
├── iphone/home_1179x2556.png
├── duo/home_1398x2034.png
├── ipad/home_2048x2732.png
└── watch/home_410x502.png
```

Each file is named `<original name>_<width>x<height>.<ext>`.

## Tips

- For the cleanest results, start from the largest screenshots you have. Scaling up softens the image.
- If you see a large "% cropped" badge, switch to **Fit & pad**, or take a screenshot with a closer aspect ratio.
- If you change settings after generating, a notice appears. Click **Generate** again to update the images.

## Troubleshooting

| Problem | Fix |
|---|---|
| **Download all** shows a "couldn't load the zip tool" message | Connect to the internet and reload the page, or download images one at a time. |
| A size failed to render | The source image may be too large for your browser's canvas. Use a smaller screenshot. |
| The page looks unstyled | The fonts couldn't load while offline. The app still works with system fonts. |

## Tech

Plain HTML, CSS and JavaScript in one file. Images are resized with the Canvas API. The zip is built with [JSZip](https://stuk.github.io/jszip/) 3.10.1, loaded from cdnjs. Light and dark mode follow your system, with a toggle in the top right.
