# Screenshots

Reference shots used in the install walkthroughs:
[`../../README.md`](../../README.md),
[`../../INSTALL_CLAUDE_AI.md`](../../INSTALL_CLAUDE_AI.md),
[`../../INSTALL_DESKTOP.md`](../../INSTALL_DESKTOP.md).

Captured during the first pilot install on claude.ai web (2026-05-19).
The desktop app's UI is similar but not pixel-identical; use Anthropic's
[current support article](https://support.claude.com/en/articles/12512180-use-skills-in-claude#h_a4222fa77b)
if the desktop labels drift.

## Generic walkthrough (README.md)

These are the three highest-signal images, used in the short README:

- `01-customize-skills.png` — Customize → Skills with the "+" button
- `02-upload-skill.png` — Upload skill dialog ("Drag and drop or click to upload")
- `03-skill-activated.png` — Skill installed with toggle on + detail pane

## claude.ai web detailed walkthrough (INSTALL_CLAUDE_AI.md)

Pre-step navigation:

- `web-prereq-01-profile-menu.png` — Profile menu showing Settings
- `web-prereq-02-settings-sidebar.png` — Settings → Capabilities highlighted

Capabilities configuration:

- `web-00-capabilities-toggles.png` — "Code execution and file creation" + "Allow network egress" both on
- `web-00b-domain-allowlist.png` — Domain allowlist showing `vusm-curriculum-api.shanestenner.workers.dev` in Additional allowed domains

Skill upload flow:

- `web-01-customize-skills.png` — Customize → Skills with "+" button and "Add skill" tooltip
- `web-02-add-menu-cascade.png` — Full menu cascade: "+" → "+ Create skill" → "Upload a skill"
- `web-03-upload-dialog.png` — Upload skill modal ("Drag and drop or click to upload")
- `web-04-skill-enabled.png` — Skills list with curriculum-intelligence installed + detail pane

Optional "Try it" / success illustrations:

- `web-05-try-query.png` — Chat composer with `/curriculum-intelligence` + the DKA sample query
- `web-06-try-response.png` — Example response showing VUSM-specific course-level evidence

## Capture notes

When refreshing these (UI drift, new flows, etc.):

- Blur or crop out: account email, profile photo, session sidebar items,
  any other personally-identifying information.
- The `web-04-skill-enabled.png` shot intentionally shows the full skill
  detail pane — that's where colleagues see name/description/toggle state
  matching what the bundle metadata advertises.
- The `web-00b-domain-allowlist.png` shot deliberately shows the API
  hostname pre-populated; that's the key install step colleagues hit if
  the skill installs but queries fail.

The canonical install flow lives in Anthropic's article (linked above).
If their UI changes substantively, that page updates before this one does.
