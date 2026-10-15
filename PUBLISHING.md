# Publishing guide: The Digital Monolith README

## File map (repository-relative)

```
README.md                              main profile README (one optional external widget)
README_fallback.md                     same design, zero external widgets
PUBLISHING.md                          this file (leave it out of the repo if you like)
assets/hero-monolith.png               01 hero, 1920x720, rendered from hero-monolith.svg
assets/hero-monolith.svg               source of the hero (animated floating forms)
assets/azfar-3d-character.png          standalone character, transparent background, 1200x1800
assets/azfar-3d-character.svg          source of the character
assets/character-detail.png            close-up portrait, 920x1080 (not used in the README; yours to use)
assets/character-detail.svg            source of the portrait
assets/idx-02.svg                      giant "02" index
assets/constellation.svg               03 stack atlas (six disciplines)
assets/project-attendx.png             conceptual artwork (not a screenshot)
assets/project-aura.png                conceptual artwork (not a screenshot)
assets/project-countryguesser.png      conceptual artwork (not a screenshot)
assets/project-portfolio.png           conceptual artwork (not a screenshot)
assets/model-monolith.svg              rotating 3D preview (60-frame SVG loop)
assets/monitor.svg                     activity panel (static snapshot)
assets/closing-channel.svg             05 closing scene
models/monolith.stl                    real 3D model (GitHub's interactive STL viewer)
```

(`artifact-0N-*.svg` are the sources of the four project PNGs; keep them in the repo if you want to re-render.)

## What was and wasn't generated

- **No image-generation model was available.** Every image is original artwork drawn as SVG code. The PNGs are renders of those SVGs made with headless Chromium.
- **The character is a stylized, clay-shaded 2.5D illustration, not a real 3D render.** It has no mesh, no ray-traced lighting and no photographic detail. It is an original fictional persona, not your likeness. If you have a Blender/Ready Player Me/Spline export or a reference photo, send it and I can rebuild the art around it.
- **Parallax is an illusion in static artwork.** GitHub READMEs can't scroll-animate.
- **The README hero is a PNG, so it is static.** The SVG source has gentle floating motion if you ever host it elsewhere.

## Preview

1. Open any `assets/*.svg` in a browser to check artwork and animation.
2. Push to a throwaway branch or repo first: GitHub's renderer is the only one that matters. VS Code's Markdown preview (`Ctrl+Shift+V`) can differ.

## Publish

Your profile repo `Azfarmoin/Azfarmoin` already exists with the earlier README and `assets/header.svg`, `assets/stats.svg`, `assets/footer.svg`.

```bash
git clone https://github.com/Azfarmoin/Azfarmoin.git && cd Azfarmoin
git rm -f assets/header.svg assets/stats.svg assets/footer.svg   # old design
# unzip azfar-profile-readme.zip over the repo (README.md, assets/, models/), then:
git add -A
git commit -m "Redesign profile: The Digital Monolith"
git push origin main
```

Open https://github.com/Azfarmoin and hard refresh (GitHub proxies images and caches them for a few minutes).

## Verified project facts

| Project | Status | Source |
|---|---|---|
| AttendX | Repo exists: `github.com/Azfarmoin/attendancex`. Description, stack and features taken from its README. No live demo, no repo description. | Fetched 2026-10-14 |
| Portfolio | `https://portfolioweb-71c1.vercel.app/` loaded and returned its page title ("Azfar Moin / Full-Stack Developer") and description. Content is client-rendered, so sections weren't read. Source repo unknown. | Fetched 2026-10-14 |
| Aura | `github.com/Azfarmoin/Aura` returns 404. Placeholder only. | Fetched 2026-10-14 |
| CountryGuesser | `github.com/Azfarmoin/CountryGuesser` returns 404. Placeholder only. | Fetched 2026-10-14 |
| Repo count (13) | Shown on your profile page; labelled as a snapshot in `monitor.svg`. | 2026-10-14 |

## Checks that could not be performed

- Your repository list could not be enumerated (GitHub's repos API and search were blocked/limited from this environment). There may be repos for Aura / CountryGuesser under other names.
- The portfolio site's content (sections, links, source) could not be read beyond its title and description, and a direct request from the shell was refused, so no live-demo claims are made beyond "the page loads".
- Nothing was viewed on GitHub itself. Renders were checked in headless Chromium only.
- The portfolio website was not modified. I have no access to its source or deployment. See "Optional: interactive 3D on the portfolio" below.

## To finish (needs your input)

| Item | What's needed |
|---|---|
| Aura / CountryGuesser | Real repo names or URLs (or make them public) |
| Portfolio source | Link to its repo, if public |
| AttendX demo | A live URL if you deploy it; then flip its status to `DEPLOYED` |
| Screenshots | Real screenshots under `assets/` to replace the conceptual project art |
| Repo count | `13` in `monitor.svg` is a dated snapshot; edit the text when it changes |

## Verification checklist

**Images**
- [ ] The hero, character, atlas, project art, monitor and closing scene all show (no broken-image icons)
- [ ] The character reads clearly in both GitHub light and dark themes (its PNG is transparent)
- [ ] The 3D preview loops; clicking it opens `models/monolith.stl` in GitHub's viewer

**Links** (click each)
- [ ] Hero image, `PORTFOLIO` and the connection link open the Vercel site
- [ ] Nav: `IDENTITY`, `STACK`, `PROJECTS` jump to their headings; `GITHUB`, `LINKEDIN` resolve
- [ ] AttendX repository, all-repositories, profile and AttendX commits links resolve

**Mobile** (GitHub app / phone browser)
- [ ] Hero, headline and nav are readable
- [ ] The identity two-column block is usable. If the character column feels cramped, use `README_fallback.md` as a base and stack them
- [ ] The atlas text is small on phones; the `TEXT INDEX` dropdown carries the same content
- [ ] Project tables are usable

**Compatibility**
- [ ] Contribution chart loads (optional widget). If not, the links under it still work, or use the fallback

## External services

- **ghchart.rshah.org**: optional contribution chart in `README.md` only. If it is down, one image breaks and nothing else changes. `README_fallback.md` has none.
- Everything else is in the repo. No JavaScript, no badges, no stats-card services.

## Optional: interactive 3D on the portfolio (not done)

The README can't run JavaScript, so a real-time character belongs on the portfolio site, which I can't edit from here. If you share its source repo (or paste its code), the sensible plan is:

1. Add a Three.js canvas with a lazy-loaded, optimised `.glb` character (a modeled mesh, not this illustration) and a gentle idle animation.
2. Mouse/touch-driven rotation and subtle camera parallax.
3. `prefers-reduced-motion` support and a static PNG fallback (`azfar-3d-character.png` works for this) for low-powered devices.
4. Only load Three.js if it fits the site's existing framework.

## Swapping to the fallback

```bash
mv README.md README_widgets.md && cp README_fallback.md README.md
```
