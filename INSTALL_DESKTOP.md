# Installing in the Claude desktop app (Mac or Windows)

These are the click-by-click steps for installing the Curriculum Intelligence skill in the desktop app, with screenshots. The main [README](README.md) has the short version; this is the detailed walkthrough.

Tested on Claude desktop for Mac and Windows.

---

## 1. Open the desktop app

Open the Claude app and sign in with the account you'd like to use. Personal or Vanderbilt SSO both work fine.

## 2. Open Settings

- **Mac**: top menu bar → **Claude** → **Settings…** (or `Cmd-,`)
- **Windows**: top-right gear icon, or hamburger menu → **Settings**

![Desktop Settings menu](assets/img/desktop-01-settings.png)

## 3. Navigate to Skills

In the Settings window's sidebar, click **Skills**.

![Settings → Skills](assets/img/desktop-02-skills.png)

## 4. Upload the bundle

Click **Create new skill** (or "Upload skill" — wording may vary by version). A file picker opens. Navigate to where Shane's email saved your `curriculum-intelligence-<your-name>.zip` and select it.

![Upload dialog](assets/img/desktop-03-upload.png)

The desktop app reads the bundle and shows a preview: name should be "**curriculum-intelligence**", description should mention "Curriculum Intelligence for VUSM faculty." Confirm.

## 5. Verify

The skill should now appear in your Skills list as "Curriculum Intelligence" with a toggle switch (default: on).

![Skills list](assets/img/desktop-04-skill-enabled.png)

## 6. Try a query

Open a new chat and ask:

> How comprehensively does VUSM cover diabetic ketoacidosis?

Claude should pull curriculum data and give you a substantive answer with course names, session-level evidence, and Bloom's-level coverage. If you get a generic answer that doesn't mention VUSM courses, the skill probably didn't activate — check Settings → Skills and confirm the toggle is on.

---

## Troubleshooting

**The upload says "Skill not valid" or similar.**
Make sure you're uploading the **`.zip` file** (not the unzipped folder). The zip is named `curriculum-intelligence-<your-name>.zip`.

**The skill is listed but Claude doesn't seem to be using it.**
Try asking a more clearly VUSM-curriculum-flavored question: include the word "VUSM" or "curriculum" explicitly. The skill activates on those keyword triggers.

**Claude says it can't reach the API / "request failed."**
This is usually a transient network issue. Try again in 30 seconds. If it persists for more than a minute, email Shane. The desktop app sometimes also needs an app restart to re-establish network state after a sleep/wake.

**I want to remove the skill.**
Settings → Skills → Curriculum Intelligence → Remove. The bundle is deleted from the app; the API key is still issued server-side, so if you want to come back, you can re-upload the same zip later. To fully revoke (so the key stops working entirely), email Shane.
