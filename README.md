# jasperprop

LoRaWAN propagation study tool — a single-page web app for planning gateway
coverage over real terrain.

![Jasper](brand/jasper-icon-cyan.svg)

## Features

- **Click-to-place gateways** on an interactive map (Leaflet / OpenStreetMap),
  or import sites from a **KMZ/KML** file. Multiple gateways merge into one
  best-server coverage picture.
- **Real terrain**: elevations are decoded from the public
  [AWS Terrain Tiles](https://registry.opendata.aws/terrain-tiles/)
  (Terrarium) dataset — no API key required.
- **Propagation model**: free-space path loss + ITU-R P.526 single knife-edge
  diffraction over the terrain profile, with 4/3-earth curvature.
- **Shaded RSSI iso-areas** with vector contour lines every 10 dB, and an
  adjustable **Reliable Coverage Edge** slider (heavy dark line, green inside,
  orange/red outside).
- **Link profiles**: click any point to draw the terrain cross-section from
  the selected gateway, with Fresnel-zone clearance and a worst-obstruction
  callout.
- Per-gateway antenna height/power/gain; shared radio settings configured for
  **US915** (902–928 MHz ISM).

## Run it

It's one file — open `index.html` in a browser, or serve the folder:

```sh
python3 -m http.server 8777
# then http://localhost:8777
```

## Caveats

The model ignores clutter (buildings, foliage), multipath, and rain. Treat
results as planning estimates and validate critical links in the field.
