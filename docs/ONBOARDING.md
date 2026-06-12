# Welcome to Keck Marketing & Analytics on GitHub 👋

This guide covers everything you need to start working in our GitHub org — from setting up your tools to making your first contribution. It's written so both technical and non-technical team members can follow along, especially since most of us use AI assistants (Cursor, Claude) to handle the git commands for us.

You don't need to memorize git commands. You just need to understand **what's happening and why**, so you can describe what you want to your AI assistant and review what it does.

---

## 1. Before You Start

Make sure you have:

- A **GitHub account**, added as a member of the `Keck-Marketing-and-Analytics` org (if you're reading this, you likely already have access)
- **Git installed** on your computer ([download here](https://git-scm.com/downloads)) — your AI assistant needs this even if you never type a git command yourself
- **Cursor** or **Claude Code** (or both) set up on your machine

### Connecting Cursor or Claude Code to GitHub

**Cursor:**
1. Open Cursor and open the folder where you want your project to live (e.g., `Documents/Keck-Projects/`)
2. Open the integrated terminal (`Ctrl+`` ` `` or `Cmd+`` ` ``)
3. The first time you interact with GitHub from your machine, it'll prompt you to authenticate — follow the browser sign-in flow with your GitHub account
4. Once authenticated, you can just ask Cursor things like *"clone the Provider-Match-Dashboard repo from our org"* and it'll handle it

**Claude Code:**
1. Install Claude Code (`npm install -g @anthropic-ai/claude-code` or follow [the official install guide](https://docs.claude.com))
2. Run `claude` in your terminal inside your project folder
3. Authenticate with GitHub the same way — Claude Code will prompt you if it needs git/GitHub access
4. You can ask it directly: *"clone [repo name] from Keck-Marketing-and-Analytics and set it up"*

Once connected, **you can do almost everything below just by describing it in plain English** to your AI assistant. The sections below explain what's actually happening so you understand what you're approving.

---

## 2. Getting a Project Onto Your Computer (Cloning)

"Cloning" means downloading a full copy of a project — including its history — onto your computer so you can work on it.

**What to say to your AI assistant:**
> "Clone the [project name] repo from the Keck-Marketing-and-Analytics GitHub org into my projects folder"

That's it. You now have a local copy you can open, edit, and run.

---

## 3. Starting a New Project (Creating a Repo)

Before creating a brand-new repo, check whether the work fits inside an existing project — most new features/dashboards are additions to existing repos, not new ones. If it genuinely is a new standalone project:

1. Go to the [Keck-Marketing-and-Analytics org page](https://github.com/Keck-Marketing-and-Analytics) → **Repositories** → **New repository**
2. Always set visibility to **Private**
3. Give it a clear, descriptive name (lowercase, hyphens — e.g., `propensity-recommender`, not `Propensity_Recommender_FINAL`)
4. Initialize with a README — this is where you'll describe what the project does and how to run it
5. If we have an org template repo set up, start from that instead of "New repository from scratch" — it comes with our standard `.gitignore`, PR template, and folder structure already in place

If you're not sure whether something needs a new repo, ask in the team channel first — it's easy to merge folders later, harder to un-merge repos.

---

## 4. The Core Workflow: Branches, Changes, and Pushing

This is the part that feels most "technical" but is actually simple once you get the mental model.

### The mental model

Think of `main` as the **official, working version** of the project — the one everyone trusts and that other people's work depends on. Nobody edits `main` directly. Instead, everyone makes their changes on their own **branch** — basically a personal copy/sandbox — and then proposes merging it back in once it's ready and reviewed.

### Step-by-step

**1. Make sure you're starting from the latest version**
> "Pull the latest changes from main before I start working"

**2. Create a branch for your task**

Branch names should describe what you're doing, with a short prefix:
- `feature/` — new functionality (e.g., `feature/add-spend-chart`)
- `fix/` — bug fixes (e.g., `fix/iso-week-calculation`)
- `docs/` — documentation only (e.g., `docs/update-readme`)

> "Create a new branch called feature/add-spend-chart and switch to it"

**3. Make your changes**

This is where you and your AI assistant do the actual work — writing code, updating a dashboard, editing docs, etc. Work normally; nothing here is different from how you'd usually code or write.

**4. Commit your changes regularly**

A "commit" is a saved checkpoint with a description of what changed. Commit often, in small logical chunks, rather than one giant commit at the end.

> "Commit these changes with the message: add monthly spend chart to dashboard"

Good commit messages are short, present-tense, and describe *what* changed (e.g., `fix: correct ISO week numbering in Adverity script`, `feat: add filter for service line`).

**5. Push your branch**

"Pushing" uploads your branch (and its commits) to GitHub so others can see it and you can open a pull request.

> "Push this branch to GitHub"

---

## 5. Pull Requests (PRs) — Proposing Your Changes

A **pull request** is how you propose merging your branch into `main`. It's also where review and discussion happens before anything becomes official.

**To open one:**
> "Open a pull request for this branch into main"

Or do it on GitHub.com: go to the repo → **Pull requests** → **New pull request** → select your branch → fill out the template.

**What to include (our PR template will prompt for this):**
- What changed and why
- How you tested it / how to verify it
- Any related issue (e.g., `Closes #14`)
- A screenshot if it's a visual change (dashboard, chart, UI)

### Who approves?

At least **one other team member** needs to review and approve before a PR can be merged. This isn't about hierarchy — it's a second pair of eyes to catch mistakes, share context, and keep everyone in the loop on what's changing. For now, any team member can review; for larger or sensitive changes (e.g., anything touching data pipelines or PHI-adjacent fields), loop in [Albert/Matas — whoever owns that area].

### After approval

Once approved, the PR gets merged using **"Squash and merge"** — this keeps the `main` branch history clean (one tidy entry per feature, instead of dozens of small "fix typo" commits). After merging, delete the branch — your AI assistant or GitHub will offer a button for this. Branches are disposable; the history lives on in `main`.

---

## 6. Issues — Tracking Tasks, Bugs, and Requests

**Issues** are how we track "things that need to happen" — bugs, feature requests, questions, or tasks — separate from the actual code changes.

**When to open an issue:**
- You found a bug
- You (or someone else, like your manager) want a new feature or change
- You're planning work and want to break it into trackable pieces

**How:**
Go to the repo → **Issues** → **New issue**. Give it a clear title (e.g., "Add YoY comparison to spend dashboard") and describe what's needed and why. Add labels if relevant (`bug`, `enhancement`, `question`).

**The lifecycle:**
1. Issue is opened, describing the ask
2. Someone picks it up, creates a branch referencing it (e.g., `feature/14-yoy-comparison`)
3. They open a PR and write `Closes #14` in the description
4. When that PR is merged, GitHub **automatically closes the issue**

This means anyone can look at the Issues tab and see exactly what's pending, in progress, or done — no separate task tracker needed.

---

## 7. Best Practices — Quick Do's and Don'ts

**Do:**
- Pull the latest `main` before starting new work
- Keep branches focused on one task — small PRs are easier to review than huge ones
- Write descriptive commit messages and PR descriptions (your AI assistant can help draft these)
- Resolve PR review comments before merging (or discuss if you disagree)
- Delete branches after merging

**Don't:**
- Push directly to `main` (branch protection should prevent this anyway, but the habit matters)
- Fork repos — work on branches within the same repo instead
- Commit secrets, API keys, or credentials — if you accidentally do, flag it immediately so it can be removed from history, not just deleted in a new commit
- Let PRs sit open for weeks — if it's blocked, say so in the PR or ask for help

---

## 8. Getting Help

If you're stuck on a git/GitHub issue (merge conflicts, authentication errors, "what do I do now"), your AI assistant can usually walk you through it — just describe what's on your screen. For org-level questions (access, new repos, permissions), reach out to **Katherine**.

---

## Quick Reference Cheat Sheet

| You want to... | Say to your AI assistant |
|---|---|
| Get the latest code | "Pull the latest changes from main" |
| Start new work | "Create and switch to a branch called feature/..." |
| Save your progress | "Commit these changes with message: ..." |
| Share your work | "Push this branch to GitHub" |
| Propose merging | "Open a pull request for this branch into main" |
| Clean up after merge | "Delete this branch, it's already merged" |

Welcome to the team — looking forward to building with you! 🚀
