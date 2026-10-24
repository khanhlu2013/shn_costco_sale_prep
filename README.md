# Shop Hoa Nắng — Costco Sale Prep

A one-page tool that prepares Costco sale photos: it stamps the Shop Hoa Nắng logo, one sale-date
line, and a price for each photo. Everything happens in the browser, so photos are never uploaded anywhere.

**How to use it** (the page is in Vietnamese):

1. Drop in the photos (or a whole folder), or click **Chọn ảnh**.
2. Type the sale date once in **Ngày sale (in lên mọi ảnh)**. It goes on every photo, top-left.
3. For each photo, type the price in **Giá** and press **Enter** for the next photo.
   `340` is stamped as **340k**, top-right. leave the box empty for a photo with no price; **← Ảnh trước** goes back;
   the thumbnails along the bottom jump straight to a photo.
4. Click **Lưu cả N ảnh (file zip)**. One photo saves as a JPEG; several save as `costco-sale-YYYY-MM-DD.zip`.

The preview shows exactly what gets saved. Leaving the date and a price empty just leaves them off.

## Publish it on GitHub Pages (one time)

1. On [github.com](https://github.com), click **+** → **New repository**. Name it `costco-sale-prep`,
   keep it **Public**, leave "Add a README file" unchecked, and click **Create repository**.
2. Click **uploading an existing file**, drag in `index.html`, `logo.png` and `README.md`, and click **Commit changes**.
3. **Settings → Pages**: Source **Deploy from a branch**, branch **main**, folder **/ (root)**, then **Save**.
4. After a minute or two the address appears at the top of the Pages settings:
   `https://<your-username>.github.io/costco-sale-prep/`. Bookmark it in her Chrome.

Only upload those three files. `SPEC.md`, `size-comparison.jpg` and the hidden `.claude` folder are just for you.

## Change the logo later

Save the new logo as **`logo.png`** (transparent background), then in the repository click
**Add file → Upload files**, drop it in, and click **Commit changes**. Press ⌘⇧R on the page to see it right away.

## Adjust the look

All the settings are together at the top of the script in `index.html`.

**Logo watermark**

| Setting | Default | What it does |
|---|---|---|
| `CORNER_SIZE` | `0.45` | Corner logo width, as a share of the photo's shorter side. |
| `CORNER_OPACITY` | `0.5` | Corner logo strength. 1 is solid, lower is more see-through. |
| `TILE_OPACITY` | `0.08` | Faint repeated background logos. Keep it low (about 0.02–0.1). |
| `TILE_WIDTH` | `0.12` | Size of each faint background logo, as a share of the photo width. |
| `MAX_EDGE` / `JPEG_QUALITY` | `2048` / `0.9` | Saved photo size (longest side, in pixels) and quality. |

**Sale date and price**

| Setting | Default | What it does |
|---|---|---|
| `DATE_TEXT_SIZE` | `0.045` | Sale-date letter size, as a share of the photo's shorter side. Long lines shrink or wrap to fit. |
| `DATE_BG` / `DATE_COLOR` | navy / cream | Banner and text colors (the logo's own colors). |
| `PRICE_TEXT_SIZE` | `0.07` | Price letter size, as a share of the photo's shorter side. |
| `PRICE_BG` / `PRICE_COLOR` | red / white | Price tag and text colors. |
| `PRICE_SUFFIX` | `k` | Added after whatever she types. |
| `FONT_FAMILY` | `Montserrat` | Font for the date and price (from Google Fonts, includes Vietnamese). |
| `LABEL_MARGIN` | `0.03` | Gap from the top and side edges. |
| `LABEL_PADDING` / `LABEL_HEIGHT` / `LABEL_RADIUS` | `0.45` / `1.6` / `0.3` | Space inside the banner/tag, its height, and how rounded its corners are. |

Colors are written like `"#D9261C"`; any web color works.

## Try changes on your Mac before publishing

Don't double-click `index.html` (Chrome blocks the logo that way). In Terminal:

```bash
python3 -m http.server 8771 --directory ~/Documents/"Costco Sale Prep"
```

Then open http://localhost:8771, and reload (⌘R) after each change. Press Ctrl+C in Terminal to stop.

## Notes

- Works in Chrome, Edge and Safari. iPhone (HEIC) photos work too.
- Saved copies don't keep the original photo information (camera details, GPS location).
- Outside resources, pinned to exact versions: [JSZip 3.10.1](https://cdnjs.com/libraries/jszip) for zip files,
  [libheif-js 1.19.8](https://www.jsdelivr.com/package/npm/libheif-js) for HEIC photos, and the
  [Montserrat](https://fonts.google.com/specimen/Montserrat) font from Google Fonts.
