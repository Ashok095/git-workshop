## The Safety Net: `git reflog`

### The Black Box Recorder

- `git log` shows **official history**
- `git reflog` records **every move you make**
- Branch switches, resets, mistakes — all recorded

**Rule of Survival:**

> If you panic, type `git reflog`

---

## Viewing the Reflog

Run:

```bash
git reflog
```

You will see entries like:

```bash
HEAD@{0}
HEAD@{1}
HEAD@{2}
```

Each entry represents:

- A previous state of your project
- A place you can return to

---

## The Soft Undo

### Resetting a Commit Without Losing Code

Command:

```bash
git reset --soft HEAD~1
```

**Effect:**

- Removes the last commit
- Keeps all code changes
- Changes remain staged

---

## When to Use Soft Reset

Use `--soft` when:

- Commit message is wrong
- You forgot to include a file
- You want to fix something _before anyone sees it_

This preserves your work while cleaning history.

---

## Soft Reset: Example

1. Add a copyright line:

```html
<p>Copyright 2023</p>
```

2. Commit:

```bash
git commit -am "feat: add copyright"
```

3. Realize the year is wrong

4. Undo the commit:

```bash
git reset --soft HEAD~1
```

5. Fix the year and recommit:

```bash
git commit -m "feat: add copyright 2026"
```

Result: Clean history. No evidence of the mistake.

---

## The Hard Reset

### Complete Memory Wipe

Command:

```bash
git reset --hard HEAD~1
```

**Effect:**

- Deletes the commit
- Deletes the code
- Working directory is reset completely

---

## When to Use Hard Reset

Use `--hard` when:

- Code is pure garbage
- You want to erase it completely
- You are certain you want it gone

**This is destructive.**

---

## Hard Reset: Example

1. Add garbage text to `index.html`
2. Commit:

```bash
git commit -am "chore: broken code"
```

3. Erase it:

```bash
git reset --hard HEAD~1
```

The commit and code are gone.

---

## The Resurrection

### Bringing Back the Dead

If something is gone:

- `git log` cannot see it
- `git reflog` can

---

## Resurrecting a Lost Commit

1. View the reflog:

```bash
git reflog
```

2. Find the commit labeled:

```
chore: broken code
```

3. Copy its hash

4. Restore it:

```bash
git reset --hard <commit-hash>
```

You have recovered deleted history.

---

## The Sniper: `git cherry-pick`

### Saving One Good Commit

Scenario:

- A branch has many bad commits
- One commit is valuable
- You want only that commit

---

### Cherry-Pick Command

```bash
git cherry-pick <commit-hash>
```

**Effect:**

- Copies a single commit
- Applies it to the current branch
- Leaves the rest behind

---

### Cherry-Pick: Workflow

1. Create an experimental branch

2. Make multiple commits:

   - Bad change
   - Good feature
   - Worse change

3. Switch back to `main`

4. Cherry-pick only the good commit

---

#### Cherry-Pick Full Example:

##### Step 1: Create an Experimental Branch

```bash
git switch -c feat/experiment
```

##### Step 2: Make Multiple Commits

###### Bad commit

```html
<h1>Temporary Test</h1>
```

```bash
git commit -am "wip: temporary test heading"
```

---

###### Good commit

```html
<section>
  <h2>About Us</h2>
  <p>We build reliable software.</p>
</section>
```

```bash
git commit -am "feat: add about us section"
```

---

###### Worse commit

```html
<div>WELCOME</div>
```

```bash
git commit -am "chore: experimenting with styles"
```

`experiment` branch now looks like:

```
wip: temporary test heading
feat: add about us section
chore: experimenting with styles
```

---

##### Step 3: Return to `main`

```bash
git switch main
```

At this point, **main does not have any of those commits**.

---

##### Step 4: Find the Good Commit Hash

```bash
git log experiment --oneline
```

Example output:

```
c3a9f21 feat: add about us section
b91d0aa wip: temporary test heading
e44c991 chore: experimenting with styles
```

Copy the hash of the good commit:

```
c3a9f21
```

---

##### Step 5: Cherry-Pick the Commit

```bash
git cherry-pick c3a9f21
```

**Result:**

- Only the good change is applied
- A new commit is created on `main`
- The bad commits stay behind

---

### Cherry-Pick Conflicts

If Git cannot apply the commit cleanly:

- It will **pause**
- Show conflict markers
- Ask you to resolve them

After fixing conflicts:

```bash
git add .
git cherry-pick --continue
```

To cancel completely:

```bash
git cherry-pick --abort
```

Result: Feature saved. Garbage ignored.

### Warning: Cherry-Picking Public Commits

Cherry-picking creates a **new commit hash**.

If the original commit was already pushed:

- History diverges
- Duplicate commits can appear
- Confusion increases

### Use cherry-pick **deliberately**, not casually.

## Cleaning History: Squashing

### Turning Chaos into One Commit

During development, commits often look like this:

```
wip
fix typo
still broken
ok now it works
```

This is normal **while working**.

But before sharing your work, history should tell a **clear story**.

---

### The Tool Behind Squashing: Interactive Rebase

Command:

```bash
git rebase -i
```

This allows you to:

- Reorder commits
- Combine commits
- Edit commit messages
- Delete commits

---

### Interactive Rebase: Targeting Commits

Rebase the last 3 commits:

```bash
git rebase -i HEAD~3
```

Git opens an editor like:

```
pick a1b2c3 wip
pick d4e5f6 fix typo
pick g7h8i9 final implementation
```

Each line is a commit, from **oldest → newest**.

---

### Squashing Commits

#### Step 1: Decide the Final Story

We want:

```
feat: complete about page
```

Instead of three messy commits.

---

#### Step 2: Edit the Rebase Instructions

Change the file to:

```
pick a1b2c3 wip
s d4e5f6 fix typo
s g7h8i9 final implementation
```

**Rules:**

- Keep the first commit as `pick`
- Change later commits to `s` (squash)
- Order matters

---

#### Step 3: Save and Continue

- **Vim:** `:wq` + Enter
- **Nano:** `Ctrl + X`, `Y`, Enter
- **VS Code:** Close the tab

Git will now ask for a new commit message.

Replace everything with:

```
feat: complete about page
```

Save and exit.

---

#### Squash Result

Check history:

```bash
git log --oneline
```

Output:

```
k9l8m7 feat: complete about page
```

Three commits → one clean commit.

---

### Squash Example: Full Walkthrough

#### Step 1: Make Messy Commits

```bash
git commit -am "wip: about page layout"
git commit -am "fix: spacing issue"
git commit -am "feat: about page content"
```

---

#### Step 2: Squash Them

```bash
git rebase -i HEAD~3
```

Edit:

```
pick 111aaa wip: about page layout
s 222bbb fix: spacing issue
s 333ccc feat: about page content
```

---

#### Step 3: Final Message

```
feat: complete about page
```

---

### Editing Commit Messages Without Squashing

To change only the **last commit message**:

```bash
git commit --amend
```

To edit an older commit message:

```bash
git rebase -i HEAD~3
```

Change:

```
pick a1b2c3 wrong message
```

To:

```
r a1b2c3 correct message
```

(`r` = reword)

---

### Rebase Conflicts

If a conflict occurs during rebase:

1. Git pauses
2. Fix conflicts manually
3. Stage changes:

```bash
git add .
```

4. Continue rebase:

```bash
git rebase --continue
```

To cancel everything:

```bash
git rebase --abort
```

---

## Rebase vs Merge

| Tool     | Result             |
| -------- | ------------------ |
| `merge`  | Preserves history  |
| `rebase` | Rewrites history   |
| `squash` | Simplifies history |

---

## The Golden Rule

### Never Rewrite Public History

Once commits are pushed:

Do NOT:

- `git rebase`
- `git reset`
- `git commit --amend`
- `git push --force`

---

### Why This Rule Exists

- Others depend on your history
- Rewriting breaks their timelines
- Causes conflicts and data loss

These powers are **local-only tools**.

---

## Things to Remember:

- `reflog` is your safety net
- `reset --soft` fixes commits safely
- `reset --hard` erases history
- `cherry-pick` rescues good work
- `rebase -i` cleans history
- Public history must remain untouched

---
