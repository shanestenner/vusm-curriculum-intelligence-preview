# VUSM Curriculum Intelligence — Release Notes

Pilot-user-facing release notes for the `curriculum-intelligence` skill bundle. The Worker API's `/curriculum-intelligence/version` endpoint links here as `release_notes_url`.

---

## v1.1.0 — 2026-05-27

### New
- **Visualizations** — phase comparison charts, heat maps, and tiered HTML/Mermaid/ASCII fallback rendering based on what your client can display. Try: *"Show me a phase distribution of behavioral neurology topics."*

### Improved
- **Citation discipline** — fewer fabricated numeric comparisons. The skill is significantly more careful about claims like "MEPO X has N objectives inline vs M in the API response"; when it doesn't have the data, it'll say so instead of confabulating.
- **Section selectivity** — better default choice of which reference file to read on `/search` queries. Fewer "I'm not sure" responses to questions the curriculum graph can actually answer.
- **Turn-1 collapse fix** — the skill no longer collapses into a summary too early on multi-part questions.

### Fixed
- Slug-split concept handling for hyphenated concept names (e.g. `non-small-cell-lung-cancer`).
- Removed a wrong-scope env-var fallback that could leak admin tokens.
- Visualization reliability when the client can't render HTML or Mermaid (falls back cleanly to ASCII tables).

### Migration
None — drop-in replacement. Your existing per-consumer key + pilot expiry date carries over unchanged. The skill will show an "update available" banner on its first response after you install v1.1.0 (that's the cue the bundle is active).

### What drove these changes
v1.1.0 reflects ~6 days of faculty-side dogfood testing of the same flows pilot users have been exercising. Every change in v1.1.0 targets a failure mode observed in real curriculum-query traffic during pilot test-flights or in the engineering dogfood loop.

---

## v1.0.0 — 2026-05-20

Initial pilot release. Skill renamed from `curriculum-query` → `curriculum-intelligence` across all surfaces. Worker API serves `/curriculum-intelligence/*` routes with the legacy `/curriculum-query/*` routes preserved as permanent backward-compatible aliases.

### Pilot launch details
- 3 colleague pilots onboarded with `read:curriculum-intelligence + read:faculty` scoped tokens (90-day keys).
- REDCap "VUSM Curriculum Intelligence — Pilot Feedback" instrument live.
- Companion preview repo (this one) provides install instructions, screenshots, and example queries.

### Capabilities at v1.0.0
- Course coverage queries (which courses teach concept X).
- MEPO alignment lookups.
- Concept distribution across phases (FMK / FCC / IMM).
- Department offerings + faculty expertise (via stages 53-59 Faculty entity pipeline).
- Spiral curriculum progression tracking.
- Gap analysis vs USMLE/LCME benchmarks.

---

For the engineering retrospective of how v1.1.0 came together (iter-7 → iter-8 → iter-9 dogfood iterations + release ceremony execution), see the development repo's `knowledge_graph/docs/2026-05-27_v1.1.0_release.md`. That doc is operator-facing; this file is pilot-user-facing.
