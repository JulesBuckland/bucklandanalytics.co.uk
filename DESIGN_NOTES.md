# Buckland Analytics Website — Design Notes

## Context
- Solo spatial analytics consultant, zero clients, zero revenue
- Cold email pipeline sends prospects to this page
- 90+ emails sent with 0% reply rate — the page must convert
- Two niches: WH:LG retrofit targeting, GIS site selection
- Target audience: local authority officers, retrofit installers, commercial property operators

## Design decisions (Sep 2026 rebuild)

### Why the rebuild
Previous version had a hex map with fake data in tooltips (fabricated fuel poverty %,
EPC bands, retrofit cost estimates generated from a PRNG). Anyone in the industry
would spot these immediately. Also lacked: social proof, sample deliverable, visible
credentials, methodology.

### Key changes
1. **Sample ranking table** — the centerpiece. Real Greater Manchester neighbourhood
   names with plausible scores based on published data ranges. Clearly labelled as
   illustrative sample output. This is what converts: prospects see what they'd get.

2. **Simplified hex map** — kept as visual element but tooltips only show area name +
   priority band (Top 10% etc). No fake specific numbers.

3. **Credentials prominent** — Buro Happold alumni, DiD methodology, data sources
   listed. Moved from buried footer text to visible section.

4. **Methodology section** — lists actual data sources (ONS, EPC Register, Census,
   IMD, BEIS). Builds trust with data-literate audience.

5. **Tighter structure** — fewer sections, each earning its place. No generic
   "how it works" padding.

### Design system
- Display: Newsreader (editorial authority, not the typical AI-generated look)
- Body: Inter (readable, proven for data contexts)
- Mono: IBM Plex Mono (data/numbers)
- Accent: Deep blue (#1E40AF) — analytical, trustworthy
- Light mode primary, dark mode supported
- Score gradient: blue → amber → red (high priority = warm)

### Deployment
- GitHub Pages: JulesBuckland/bucklandanalytics.co.uk
- CNAME: bucklandanalytics.co.uk
- Push: `git -c http.sslBackend=schannel push origin master`
- Single index.html, no build step, no dependencies

### Sample data provenance
The ranking table uses real Greater Manchester ward/MSOA names. Score values are
illustrative but calibrated to published ranges:
- Fuel poverty: BEIS sub-regional estimates (Oldham/Rochdale genuinely top in England)
- EPC bands: DLUHC EPC register statistics
- Housing age: Census 2021 dwelling age profiles
- Vulnerability: IMD 2019 health/disability domain

All labelled as "Illustrative sample" — not claimed as real analysis output.
