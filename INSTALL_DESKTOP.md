# Installing in the Claude desktop app (Mac or Windows)

The Claude desktop app supports custom skills with the same overall flow as claude.ai web. **Anthropic's official guide is the canonical source** and covers any UI differences as they evolve:

> **[Anthropic — Use Skills in Claude (Add and Use Custom Skills)](https://support.claude.com/en/articles/12512180-use-skills-in-claude#h_a4222fa77b)**

The Anthropic article currently documents the claude.ai web flow in detail; the desktop app's menu paths can differ slightly between releases, so the article is what to trust if anything below looks wrong.

---

## The short version

1. **Prerequisites — three Capabilities settings (one-time):**
   - Open the desktop app's settings (top menu bar → Claude → Settings… on Mac, or the gear icon on Windows).
   - Find **Capabilities** and toggle **"Code execution and file creation"** on.
   - In the same Capabilities section, toggle **"Allow network egress"** on.
   - Scroll down to **Domain allowlist** → **Additional allowed domains**, paste `vusm-curriculum-api.shanestenner.workers.dev`, and click **Add**. The default "Package managers only" mode blocks our API unless the hostname is listed explicitly. (Setting the dropdown to **"All domains"** also works, if you prefer.)

2. **Open the Skills configuration:**
   - Look for **Customize → Skills** (the same path as the web app).

3. **Upload the bundle:**
   - Click the **"+"** button at the top of the Skills list.
   - Choose **"+ Create skill"** → **"Upload a skill"**.
   - Select the `curriculum-intelligence-<your-name>.zip` file Shane sent you.

4. **Verify:**
   - The skill should appear as **"Curriculum Intelligence"** in the list, with a toggle (default: on).

5. **Try a query:**
   - Open a new chat and ask: *"How comprehensively does VUSM cover diabetic ketoacidosis?"*
   - Claude should return a VUSM-specific answer drawing on the curriculum knowledge graph.

---

## If your desktop app's UI looks different

The desktop app gets frequent updates and menu wording sometimes shifts:

- If you don't see **Customize**, look for **Settings** or a gear icon, then **Skills** as a sidebar item.
- If you see different button labels (e.g., "Add skill" instead of "+ Create skill"), follow what your app shows. The end goal is the same: upload the ZIP file.
- If you can't find a Skills section at all in your desktop app, try [claude.ai](https://claude.ai) in your web browser instead — same account, same setup, definitely supports custom skills.

When in doubt, **Anthropic's [official guide](https://support.claude.com/en/articles/12512180-use-skills-in-claude#h_a4222fa77b) is more current than this page.**

---

## Troubleshooting

**"Code execution must be enabled" error.**
You missed the prerequisite step. Go back to Settings → Capabilities → "Code execution and file creation."

**Upload says "Skill not valid" or similar.**
Make sure you're uploading the `.zip` file (not the unzipped folder). The zip should be named `curriculum-intelligence-<your-name>.zip` and is under 50 KB.

**Claude says it can't reach the API / "request failed."**
Most common cause: **the API hostname isn't in your Domain allowlist.** Settings → Capabilities → scroll to **Additional allowed domains** and confirm `vusm-curriculum-api.shanestenner.workers.dev` is listed. Also confirm **"Allow network egress"** is on.

If both are set correctly, it's probably transient. Try again in 30 seconds. The desktop app sometimes needs a restart after sleep/wake to re-establish network state.

**I want to remove the skill.**
Customize → Skills → Curriculum Intelligence → Remove. The bundle is deleted from your app. The API key is still issued server-side, so you could re-upload the same zip later — or email Shane to fully revoke the key.
