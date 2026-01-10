## Branching · Merging · Emergency Handling

## The Sacred Timeline

### MAIN Branch

- Represents **production**
- What users see
- What must always work

**Rule:** Never experiment directly on `main`

---

## Why Branches Exist

Branches allow you to:

- Create a parallel timeline
- Experiment safely
- Break things without fear
- Merge only when ready

If a branch fails → `main` is untouched  
If a branch succeeds → merge it back

---

## Creating a New Branch

Command to create and switch to a branch:

```bash
git switch -c <branch-name>
```

This:

- Creates a new branch
- Moves you into it immediately

---

## Branch Naming Convention

Use descriptive, professional names:

### Features

```
feat/contact-section
feat/dark-mode
```

### Bug Fixes

```
fix/login-bug
fix/header-typo
```

### Documentation

```
docs/update-readme
```

Clear naming helps teams collaborate safely.

---

## create new Feature Branch

We will add a **Contact section** Not on `main`

Create a new branch:

```bash
git switch -c feat/contact-section
```

Verify:

```bash
git status
```

---

## Coding in a Branch

Edit `index.html`

Add at the bottom:

```html
<footer>Contact: me@example.com</footer>
```

Commit the change:

```bash
git commit -am "feat: add contact footer"
```

---

## The Magic of Switching Branches

Switch back to `main`:

```bash
git switch main
```

The footer is gone

Switch back to the feature branch:

```bash
git switch feat/contact-section
```

The footer reappears

You are watching timelines change instantly.

---

## Merging: Bringing Work Home

To merge code into `main`:

1. Switch to `main`
2. Merge the branch

```bash
git switch main
git merge feat/contact-section
```

---

## Fast-Forward Merge

Git may say: `Fast-forward`

This means:

- `main` did not change
- Git simply moved the pointer forward
- No conflict, no merge commit

This is the simplest merge.

---

## The Real World Scenario

You are building **Dark Mode**
Work is incomplete;  You must not commit yet

Suddenly, critical issue on `main` You must switch immediately.

---

## The Problem

Git does not like:

- Half-finished files
- Messy working directories

Switching branches may:

- Fail
- Carry unfinished files into `main`

This is dangerous.

---

## The Solution: Stashing

Stashing temporarily hides your work.

Command:

```bash
git stash
```

Think of it as:

- Sweeping work into a drawer
- Making your workspace clean instantly

---

## Dark Mode Setup (Before Stash)

Create a new branch:

```bash
git switch -c feat/dark-mode
```

Create `style.css`:

```css
body {
  background: black;
}
```

Do not commit

---

## Stash the Work

Run:

```bash
git stash
```

Result:

- `style.css` disappears
- Working directory is clean
- Work is safe

---

## Emergency Fix on Main

Switch to `main`:

```bash
git switch main
```

Fix the title in `index.html`
Change:

```
Developer → Expert Engineer
```

Commit the fix:

```bash
git commit -am "fix: update title"
```

---

## Returning to Your Feature

Go back to Dark Mode:

```bash
git switch feat/dark-mode
```

Restore stashed work:

```bash
git stash pop
```

Your files return exactly as before.

---

## Finish the Feature

Complete Dark Mode and commit:

```bash
git add .
git commit -m "feat: add dark mode css"
```

Your branch is now ready.

---

## True Merge (Diverged History)

Now:

- `main` has the hotfix
- `feat/dark-mode` has new CSS

Timelines have diverged.

Git must create a **merge commit**.

---

## Performing the Merge

Switch to `main`:

```bash
git switch main
git merge feat/dark-mode
```

Git opens an editor asking for a merge message.

---

## Completing the Merge Commit

Depending on editor:

- **Vim:** `:wq` + Enter
- **Nano:** `Ctrl + X`, `Y`, Enter
- **VS Code:** Close the tab

You have completed a **3-way merge**.

---

## Visualizing the Multiverse

Use Git’s graph view:

```bash
git log --all --decorate --oneline --graph
```

This shows:

- Where branches split
- Where they merged
- The full timeline

---

## Make It Easier (Alias)

Create a shortcut:

```bash
git config --global alias.graph "log --all --decorate --oneline --graph"
```

Now simply run:

```bash
git graph
```

---

## Things to Remember

- `main` is sacred
- Branches are safe playgrounds
- Merging brings success home
- Stashing saves unfinished work
- Git lets you visualize time

---