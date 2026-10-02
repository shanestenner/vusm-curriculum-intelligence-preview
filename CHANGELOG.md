# VUSM Curriculum Intelligence — Release Notes

Pilot-user-facing release notes for the `curriculum-intelligence` skill bundle. The Worker API's `/curriculum-intelligence/version` endpoint links here as `release_notes_url`.

---

## v1.2.0 – 2026-10-01

### New
- **One-call concept lookup** – ask about a concept and the skill gets its courses, phases, Bloom's levels, sample passages and related concepts in a single request (it used to take several). Answers come back faster.
- **Abbreviations and everyday terms** – "MI", "DKA", "heart attack" and similar now land on the right concept. When a term could mean two things (MS can be multiple sclerosis or mitral stenosis), the skill tells you which one it picked, or asks.
- **Readable passage samples** – each concept comes with short excerpts from real teaching materials, drawn from different courses.
- **Faculty in the same request** – "Who teaches X?" now comes back with the concept itself (still course-level, as before).
- **Clinical topic list** – USMLE and LCME vertical-trace questions now start from the full list of topics, so the skill no longer guesses topic names.

### Improved
- **Fewer invented citations** – the skill sticks to figures it actually retrieved, and says so when it doesn't have the data.
- **Fewer dead ends** – when a name doesn't match, the skill tries other spellings and abbreviations before telling you the curriculum doesn't cover it.

### Fixed
- Questions about clinical topics no longer set off long runs of failed requests.
- Blank search terms are caught before they go out.

### Known issue
Questions pinned to last academic year (2024-25) can occasionally miss a concept that is there. Questions about the current year aren't affected. A fix is on the way.

### Migration
If you're in the pilot, you'll get the v1.2.0 bundle and a fresh key directly. It replaces v1.1.0, with nothing to change in your settings. Older bundles show an "update available" banner on their first answer.

### What drove these changes
Pilot and test questions showed the skill spending several steps just finding the right concept before it could answer, and sometimes guessing at names. v1.2.0 moves that matching into the curriculum service, so the skill starts from the right concept.

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
