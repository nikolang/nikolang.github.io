# he-maps

Map tiles for the VRChat world "Into the Hollow Earth". One pair of files per
landing site; the world downloads them at runtime with VRCImageDownloader.

| File | Content |
|---|---|
| `<Site>_umfeld_2k.png` | 2048 × 2048 RGBA, 20 × 20 km around the site (9.77 m per pixel), north up, west left. RGB = surface albedo (sRGB, without water), A = emissive (linear 0–1, relative glow) |
| `<Site>_hoehe_rg_2k.png` | 2048 × 2048 RGBA, same area. Height code = R · 256 + G, height in metres = (code − 24000) / 4 (0.25 m steps, sea level of the inner world = 0, positive towards the centre). B = water mask (255 = water), A = 255. Load without mipmaps, point filtering |

The terrain of the hollow earth is fictional. It was generated from the open
data sets below, rearranged and modified.

**Terrain elevation**
NOAA National Centers for Environmental Information (2022), ETOPO 2022
15 Arc-Second Global Relief Model, DOI 10.25921/fd45-gt74. Public domain
(U.S. Government work).

**Surface colour**
NASA Earth Observatory, Blue Marble: Next Generation (Reto Stöckli, NASA
Goddard Space Flight Center). NASA Visible Earth.
