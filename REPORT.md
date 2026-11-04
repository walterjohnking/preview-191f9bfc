# Harlow & Vale - delivery report (floor-plan transition)

## Walter confirmation
Isaac transcript `7bd95e19-706f-40f6-aadf-164ef7c8e7b5`: Walter answered poll t426s1461 with **"Go with the floor plan match"**. Door hero removed; plan match mode added. Published to same private preview.

## Preview
- URL: https://walterjohnking.github.io/preview-191f9bfc/
- Demo (full site path): https://walterjohnking.github.io/preview-191f9bfc/?demo=1
- Plan match: https://walterjohnking.github.io/preview-191f9bfc/?start=plan
- Plan + demo: https://walterjohnking.github.io/preview-191f9bfc/?demo=1&start=plan
- Repo: https://github.com/walterjohnking/preview-191f9bfc (robots Disallow /, noindex)
- Local: /workspace/crowncraft/reel-harlow-vale/
- HTTP: **200**

## Changes
1. Removed door split-open hero entirely.
2. Calm static hero photo (`images/hero-static.webp`, Unsplash open living, no people) + "Find the one."
3. `?start=plan`: clean 430px phone frame, paper-white floor plan, no UI chrome; held ~1.1s as match target; then rooms draw/highlight with photos.
4. `?demo=1&start=plan`: plan anim → listing tour rooms → Sat 11:00 booking.
5. `?demo=1` (no start): static hero → suburb → listing → dusk → rooms → booking (~15s, no door).

## Demo durations
- `?demo=1`: **14768 ms** (~14.8 s)
- `?demo=1&start=plan`: **13777 ms** (~13.8 s)

## Exports (print / desk match)
- PNG: `/workspace/crowncraft/reel-harlow-vale/exports/floor-plan.png` (4400×4800, paper-white, same SVG proportions)
- PDF A4: `/workspace/crowncraft/reel-harlow-vale/exports/floor-plan-A4.pdf`

## Screenshots (430×932 @2.5)
- `shots/20-hero-static.png` — new calm hero
- `shots/21-plan-first-frame.png` — `?start=plan` held still (match target)
- `shots/22-plan-mid-anim.png` — kitchen highlight + photo mid-anim
- `shots/23-demo-end.png` / `shots/24-demo-plan-end.png`

## Checklist
- No concept/demo/fictional visible copy: **PASS**
- Phone fit, no door chrome on plan match: **PASS**

## Trade-offs
1. Hero uses open-plan interior stock (not a Melbourne facade); calm and people-free.
2. Day↔dusk remains CSS grade on same day photo.
3. Print export redraws the SVG geometry in PIL at the same viewBox proportions (exact room rects from the on-screen plan).

## Plan overlay fix (no zoom-out jump)
- Plan SVG stays full-size and fixed; room photo slides up as absolute bottom overlay card with soft shadow (no plan scale/translate/reflow).
- Measurements @430×932@2.5, every 100ms while plan held+animating: rect constant `{x:35,y:268,w:360,h:396}` (0 unstable during sequence). Demo-from-plan zeros only after `hidePlanMatch()` teardown.
- Screenshots: `shots/21-plan-first-frame.png`, `shots/22-plan-mid-anim.png`
- Durations: demo=1 **14768 ms**; demo=1&start=plan **13776 ms**
