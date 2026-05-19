# Installing on claude.ai (web browser)

These are the click-by-click steps for installing the Curriculum Intelligence skill in your web browser. The main [README](README.md) has the short version; this is the detailed walkthrough.

**Authoritative source:** Anthropic's [Use Skills in Claude](https://support.claude.com/en/articles/12512180-use-skills-in-claude#h_a4222fa77b) article. If the UI labels below ever drift from what you actually see, follow Anthropic's article — they update it as Claude evolves.

Tested on Chrome, Safari, Firefox, and Edge.

---

## Prerequisites: Enable code execution + network egress (one-time)

You need two settings enabled on your account before the skill can talk to the curriculum API. Once configured, you don't need to revisit either.

### Code execution

1. Open **[claude.ai](https://claude.ai)** and sign in.
2. Click your profile icon (top-right) → **Settings**.
3. In the Settings sidebar, click **Capabilities**.
4. Toggle **"Code execution and file creation"** on.

![Capabilities settings with code execution enabled](assets/img/web-00-code-execution.png)

### Network egress

Still in **Settings → Capabilities**, find the **"Allow network egress"** toggle and make sure it's on.

This setting controls whether code running inside Claude's sandbox can reach the public internet. Our skill needs to call `https://vusm-curriculum-api.shanestenner.workers.dev` to fetch curriculum data — without this toggle, every query will load the skill but fail at the data-fetch step.

![Network egress toggle](assets/img/web-00b-network-egress.png)

**On personal plans (Free/Pro/Max), this toggle is usually on by default** and there's no per-domain allowlist to configure — the toggle is binary. You only need to verify it.

> **Team or Enterprise plans:** the egress setting is controlled by your org admin under **Organization settings → Capabilities**. The admin needs to either set egress to **"All domains"**, or add `vusm-curriculum-api.shanestenner.workers.dev` to the organization's specific-domains allowlist. They'll also need to enable **"Code execution and file creation"** and **"Skills"** if those aren't already on. Share this README with your admin if you need to escalate the request.

---

## Step 1: Open the Skills section

In the top navigation (or sidebar, depending on your account view), click **Customize**. Then click **Skills**.

![Customize → Skills navigation](assets/img/web-01-customize-skills.png)

You should see a list of any skills already on your account (probably empty for a new install).

## Step 2: Add a new skill

Click the **"+"** button at the top-right of the Skills list. A small menu appears.

![Add skill menu](assets/img/web-02-add-menu.png)

Click **"+ Create skill"** in that menu.

## Step 3: Upload the bundle

In the dialog that opens, click **"Upload a skill"** (rather than building one from scratch). A file picker opens. Navigate to where Shane's email saved your `curriculum-intelligence-<your-name>.zip` file (usually your Downloads folder) and select it.

![Upload dialog with zip selected](assets/img/web-03-upload-dialog.png)

Claude reads the bundle and shows a preview:

- **Name:** `curriculum-intelligence`
- **Description:** starts with *"Curriculum Intelligence for VUSM faculty — query the Vanderbilt medical school curriculum knowledge graph…"*

Click confirm/save.

## Step 4: Verify it appears in the list

The skill should now show up in your Skills list as "Curriculum Intelligence" with a toggle (default: on).

![Skill enabled in list](assets/img/web-04-skill-enabled.png)

## Step 5: Try a query

Open a new conversation (top-left "+ New chat") and ask:

> How comprehensively does VUSM cover diabetic ketoacidosis?

Claude should call the curriculum knowledge graph and respond with specific VUSM course names, session evidence, and Bloom's-level coverage. If you get a generic medical answer with no VUSM specifics, the skill probably didn't activate — go back to **Customize → Skills** and confirm the toggle is on.

---

## Troubleshooting

**"Code execution must be enabled" or similar error.**
The prerequisite step above (Capabilities → "Code execution and file creation") wasn't completed for your account. Go back to that section.

**The upload says "Skill not valid" or "Invalid skill structure."**
- Make sure you're uploading the **`.zip` file**, not the unzipped folder.
- The zip is named `curriculum-intelligence-<your-name>.zip`.
- File size should be under ~50 KB (the bundle is tiny).

**The skill is listed but Claude doesn't seem to be using it.**
- Try asking a more clearly VUSM-curriculum-flavored question: include the word "VUSM" or "curriculum" explicitly.
- Confirm the skill's toggle is on in Customize → Skills.

**Claude says it can't reach the API / "request failed."**
Most common cause first: **network egress is off or restricted.**

- **Free/Pro/Max:** Go to Settings → **Capabilities** and confirm **"Allow network egress"** is on (usually on by default).
- **Team/Enterprise:** Your org admin needs to either set network egress to **"All domains"** or add `vusm-curriculum-api.shanestenner.workers.dev` to the organization's specific-domains allowlist (Organization settings → Capabilities). The skill will load but every query fails until this is configured.

If both of those are correct, it's usually a transient network issue — try again in 30 seconds. If it persists for more than a minute, email Shane.

**I want to remove the skill.**
Customize → Skills → Curriculum Intelligence → Remove. The bundle is deleted from your account; if you want to come back, you can re-upload the same zip later (the key inside stays valid until the pilot ends or you ask Shane to revoke it).

If the UI doesn't match this guide exactly, Anthropic's [official guide](https://support.claude.com/en/articles/12512180-use-skills-in-claude#h_a4222fa77b) is the most current source.
