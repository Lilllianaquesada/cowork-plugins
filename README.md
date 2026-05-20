# CloudLinux Marketing — Cowork Plugins

Internal Cowork plugins maintained by the CloudLinux marketing team.

## What's in this repo

This repository is a **Cowork plugin marketplace**. It contains plugins that the CloudLinux marketing team uses inside Claude Cowork.

Currently included:

- **`cloudlinux-email-sequences`** — Builds CloudLinux and Imunify360 recurring email sequences (on-demand webinar nurture, lead-gen form nurture, post-webinar SQL comms) with the team's standard cadence, tone, terminology, and quality checks.

---

## Part 1 — One-time setup (Lily)

These steps only need to be done once, by the person who owns this repository.

### Step 1: Create the GitHub repository

1. Go to https://github.com/new
2. Fill in:
   - **Repository name:** `cowork-plugins` (or any name you like — just remember it)
   - **Description:** "CloudLinux marketing plugins for Claude Cowork"
   - **Visibility:** **Private** is recommended (only people you invite can see it). Public works too if you don't mind anyone reading the instructions.
   - Leave "Initialize this repository" unchecked.
3. Click **Create repository**.

After creation, GitHub will show you setup instructions. You'll use the "push an existing repository from the command line" option.

### Step 2: Push these files to GitHub

Open your terminal (Spotlight → "Terminal") and run the following commands:

```bash
cd "/Users/lilyquesada/Documents/Claude/Projects/LEADS SEQUENCES AUTOMATIONS/cowork-plugins"

git init
git add .
git commit -m "Initial commit: cloudlinux-email-sequences plugin"
git branch -M main
git remote add origin https://github.com/Lilllianaquesada/cowork-plugins.git
git push -u origin main
```

If you get an authentication prompt, GitHub will walk you through using a personal access token or signing in via GitHub Desktop. If you've never set up git on this machine, the easiest path is to install **GitHub Desktop** (https://desktop.github.com/) and use its "Add an existing repository from your hard drive" option, then click **Publish repository**.

### Step 3: Invite your team to the repo

If the repo is private, your teammates need access to install the plugin.

1. On GitHub, go to your repo → **Settings** → **Collaborators** (or **Manage access**).
2. Click **Add people** and invite each teammate by their GitHub username or email.
3. **Read access** is enough — they don't need to push changes.

### Step 4: Test the install on your own machine

Before sharing with the team, verify it works:

1. Open Claude Desktop.
2. Open the Cowork plugins menu and add the marketplace using the GitHub source. (See Step 1 in Part 2 below — same instructions apply to you.)
3. Install the `cloudlinux-email-sequences` plugin.
4. Open any chat and ask: "Build me an on-demand webinar nurture sequence for a webinar about Imunify360 malware cleanup." If the skill loads and asks for the required inputs, it's working.

---

## Part 2 — Install instructions (for the team)

Share these steps with each teammate.

### Step 1: Make sure Claude Desktop is up to date

Cowork requires the latest version of Claude Desktop.

- **macOS:** https://claude.ai/api/desktop/darwin/universal/dmg/latest/redirect
- **Windows:** https://claude.com/download

### Step 2: Add the marketplace

In Claude Desktop, open the Cowork plugins menu (Settings → Plugins, or the plugin icon in the Cowork interface) and add a new marketplace using the GitHub source:

- **Source type:** GitHub
- **Repository:** `Lilllianaquesada/cowork-plugins`

If your teammates are using Claude Code instead of Cowork, the equivalent command is:

```
/plugin marketplace add Lilllianaquesada/cowork-plugins
```

### Step 3: Install the plugin

From the plugin catalog, find **`cloudlinux-email-sequences`** and click **Install**.

In Claude Code, the equivalent command is:

```
/plugin install cloudlinux-email-sequences@cloudlinux-marketing-plugins
```

### Step 4: Use it

Open Cowork (any chat — no special project required) and describe the campaign you want to build. Examples:

- "Build me a lead-gen form nurture sequence for the VPS Bundle playbook."
- "I need a post-webinar SQL sequence for our Imunify360 malware cleanup webinar from last week."
- "On-demand webinar nurture, AccelerateWP, hosting providers audience."

The skill will automatically activate and walk you through the required inputs.

---

## Updating the plugin

When Lily updates the email sequence instructions (new product, new sequence type, updated rules):

1. Edit `plugins/cloudlinux-email-sequences/skills/cloudlinux-email-sequences/SKILL.md` locally.
2. Bump the `version` field in both:
   - `plugins/cloudlinux-email-sequences/.claude-plugin/plugin.json`
   - `.claude-plugin/marketplace.json` (the entry for `cloudlinux-email-sequences`)
3. Commit and push to GitHub:

   ```bash
   cd "/Users/lilyquesada/Documents/Claude/Projects/LEADS SEQUENCES AUTOMATIONS/cowork-plugins"
   git add .
   git commit -m "v1.1.0: <describe what changed>"
   git push
   ```

4. Tell the team to refresh — in Claude Code that's `/plugin marketplace update`, in Cowork it's the "Refresh" button on the marketplace.

---

## Repository structure

```
cowork-plugins/
├── README.md                                       (this file)
├── .claude-plugin/
│   └── marketplace.json                            (the marketplace catalog)
└── plugins/
    └── cloudlinux-email-sequences/
        ├── .claude-plugin/
        │   └── plugin.json                         (plugin manifest)
        └── skills/
            └── cloudlinux-email-sequences/
                └── SKILL.md                        (the actual instructions)
```

---

## Maintainer

CloudLinux Marketing — Lily Quesada-Gomez (lillianaqg@gmail.com)
