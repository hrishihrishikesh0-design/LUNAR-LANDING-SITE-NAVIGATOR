# 🌑 Lunar Landing Site Navigator

An intuitive, zero-install web tool for comparing lunar south-pole landing sites and dates. It shows where the **Sun** and **Earth** sit relative to the local horizon, so mission planners, educators and the public can quickly judge **solar power potential** and **direct-to-Earth (DTE) communication windows**.

Built for the *Lunar Landing Site Navigator* challenge.

## Features
- **Timeline**: one bar per site over a 7–120 day window, colour-coded: Sun + Earth, Sun only, Earth only, neither.
- **Sky view**: horizon panorama (azimuth vs. elevation) with Sun/Earth paths and a play/scrub control.
- **Comparison table**: % Sun, % Earth, % both, longest dark period, longest no-link period; ranked automatically.
- **Terrain mask** slider (0–8°) to mimic local horizon blocking.
- **Presets** (Shackleton rim, Malapert massif, Nobile rim, de Gerlache rim, Haworth rim, Cabeus, Mons Mouton, Chandrayaan-3) plus **custom lat/lon**.
- Light and dark themes (follows your system), responsive, no build step, no dependencies, works offline.

## Run it
```bash
git clone https://github.com/<your-username>/lunar-landing-site-navigator.git
cd lunar-landing-site-navigator
# open index.html directly, or serve it:
python3 -m http.server 8000   # then visit http://localhost:8000
```

### Deploy on GitHub Pages
Repo → **Settings → Pages → Deploy from a branch → `main` / `(root)`**. The site goes live at `https://<your-username>.github.io/lunar-landing-site-navigator/`.

## Project layout
```
index.html   page structure
style.css    theme tokens and layout
app.js       ephemeris model, rendering, UI
docs/MODEL.md  equations and limitations
```

## How it works
Sun and Earth directions are computed in the Moon-fixed frame (lunar phase, libration, solar declination), then converted to local elevation/azimuth for each site. See [docs/MODEL.md](docs/MODEL.md).

> ⚠️ **Accuracy:** this is a simplified analytic model (roughly ±1–2° and a few hours). It is for comparison, education and early planning, **not** flight-grade analysis.

## Roadmap
- [ ] Replace the analytic model with SPICE (e.g. precomputed kernels or CSPICE/WASM) or JPL Horizons data
- [ ] Real terrain horizon profiles from LOLA DEMs instead of a uniform mask
- [ ] Sun angular size, partial illumination, Earth eclipses
- [ ] Day-by-day power/comms calendar and CSV/PNG export
- [ ] Shareable URLs (sites, dates, mask in the hash)
- [ ] Educator mode with guided explanations

## Contributing
Issues and PRs welcome. Keep it dependency-free and readable. If you change the model, update `docs/MODEL.md` and note how you validated it.

## License
[MIT](LICENSE)
