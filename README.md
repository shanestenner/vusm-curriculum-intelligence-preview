# VUSM Curriculum Intelligence — Private Preview

A Claude skill that lets you ask questions about what we teach at the Vanderbilt University School of Medicine: course coverage, MEPO alignment, where a clinical topic appears across the four-year curriculum, faculty expertise by concept, and gaps in coverage. The skill talks to a server I (Shane Stenner) maintain; your access is scoped to read-only curriculum queries and is revocable any time.

> **Private preview.** This skill is being shared with a handful of VUSM faculty for feedback. Please don't redistribute the bundle you received — each install carries an individual API key that's tied to you.

---

## What you'll need (30 seconds)

- A Claude account — either the **desktop app** (Mac or Windows) or **claude.ai** in your web browser. Both work; pick whichever you already use.
- The personalized `.zip` file Shane sent you (named `curriculum-intelligence-<your-name>.zip`).

That's it. No Terminal, no GitHub account, no command-line tools.

---

## Install (5 steps)

1. **Open Claude.** In the desktop app, this is the app icon. In the browser, go to [claude.ai](https://claude.ai) and sign in.

2. **Open Settings → Skills.** In the desktop app: top-bar menu → Settings → Skills. In the browser: profile icon (top-right) → Settings → Skills.

   ![Settings → Skills panel](assets/img/01-settings-skills.png)

3. **Click "Create new skill"** (or "Upload skill" — wording varies between platforms).

4. **Drag in the zip** Shane sent you. Claude will read the skill name and description and confirm.

   ![Upload skill dialog](assets/img/02-upload-skill.png)

5. **You're done.** Claude now has the "Curriculum Intelligence" skill available. The skill activates when you ask curriculum-related questions — no special command needed.

   ![Skill activated indicator](assets/img/03-skill-activated.png)

Platform-specific notes if you hit a snag:
- **claude.ai web** — see [INSTALL_CLAUDE_AI.md](INSTALL_CLAUDE_AI.md).
- **Desktop app** — see [INSTALL_DESKTOP.md](INSTALL_DESKTOP.md).

---

## Try it (30 seconds of validation)

Once the skill is installed, open a new conversation in Claude and try one of these. Each should return a substantive answer drawing on the curriculum knowledge graph:

- *"How comprehensively does VUSM cover diabetic ketoacidosis?"*
- *"Which courses introduce inflammation, and when in the spiral curriculum?"*
- *"Who teaches behavioral neurology at VUSM?"*
- *"What MEPOs is the Foundations of Medical Knowledge phase aligned with?"*
- *"Where do we cover health equity across the curriculum?"*

If Claude responds with something that **doesn't** sound like it knows about VUSM-specific courses, sessions, or MEPOs — the skill probably isn't loaded. Open Settings → Skills again and confirm "Curriculum Intelligence" is listed and toggled on.

---

## What we'd love your feedback on

After you've used the skill for a session or two, please take ~5 minutes to fill out the REDCap form. It's anonymous unless you choose to add your name. See [FEEDBACK.md](FEEDBACK.md) for the link and what we're hoping to learn.

We're especially interested in:
- Did Claude get the curriculum content **right**? (Misstatements about coverage are the most important thing to flag.)
- Were the answers **useful** for the questions you'd actually want to ask in your work?
- Anything that felt **slow, broken, or surprising**?

---

## A note on security and your data

- Your zip contains an **individual API key** scoped to you. It only allows read access to the curriculum knowledge graph — it cannot upload, modify, or access any student data.
- Every query you make is logged with your consumer ID (so I can spot problems), but the log doesn't see the *content* of Claude's response — only which endpoint you called.
- If your laptop is lost, stolen, or you'd like access revoked for any reason: **email me and I'll revoke within the minute**. After revocation, the bundle stops working immediately.
- Please don't share the zip with anyone — if a colleague would also like to participate, ask me to issue them their own.

---

## FAQ

**Does this access student records or PHI?**
No. The curriculum knowledge graph contains course objectives, session metadata, concept mappings, and aggregated faculty teaching attributions. There is no student-level data in the API.

**What does it cost?**
Nothing to you. The Cloudflare Worker costs me pennies per month; it's a research/internal tool.

**Will the answers always be right?**
Claude can hallucinate, even with strong context. Treat answers like a smart colleague's first-pass take — useful as a starting point, but verify before citing in formal documents. Flag anything that looks wrong in the REDCap feedback form.

**Pilot end date?**
About 90 days from when I issued your key. I'll email a few weeks before to ask whether you'd like to extend or wrap up.

**Can I uninstall the skill?**
Yes, any time, from Settings → Skills → Curriculum Intelligence → Remove. The API key is still issued server-side; let me know and I'll revoke it.

---

## Questions?

Email Shane Stenner — same address that sent you the bundle.
