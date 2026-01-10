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

* A previous state of your project
* A place you can return to

---

## The Soft Undo

### Resetting a Commit Without Losing Code

Command:

```bash
git reset --soft HEAD~1
```

**Effect:**

* Removes the last commit
* Keeps all code changes
* Changes remain staged

---

## When to Use Soft Reset

Use `--soft` when:

* Commit message is wrong
* You forgot to include a file
* You want to fix something *before anyone sees it*

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

* Deletes the commit
* Deletes the code
* Working directory is reset completely

---

## When to Use Hard Reset

Use `--hard` when:

* Code is pure garbage
* You want to erase it completely
* You are certain you want it gone

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

* `git log` cannot see it
* `git reflog` can

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

* A branch has many bad commits
* One commit is valuable
* You want only that commit

---

## Cherry-Pick Command

```bash
git cherry-pick <commit-hash>
```

**Effect:**

* Copies a single commit
* Applies it to the current branch
* Leaves the rest behind

---

## Cherry-Pick: Example

1. Create an experimental branch

2. Make multiple commits:

   * Bad change
   * Good feature
   * Worse change

3. Switch back to `main`

4. Cherry-pick only the good commit

Result: Feature saved. Garbage ignored.

---

## Cleaning History: Squashing

### Turning Chaos into One Commit

Messy history:

```
wip
typo
almost done
done
```

Professional history:

```
feat: complete feature
```

---

## Interactive Rebase

Command:

```bash
git rebase -i
```

Example:

```bash
git rebase -i HEAD~3
```

This opens an editor with commit instructions.

---

## Squashing Commits

In the editor:

* Keep the first commit as `pick`
* Change the rest to `s` (squash)

Save and continue.

Git will ask for a new commit message.

---

## Final Squash Result

Write a clean message:

```
feat: create complete about page
```

Check history:

```bash
git log
```

Multiple commits become one.

---

## The Golden Rule of History

**Never rewrite public history**

Do NOT:

* `rebase`
* `reset`
* `--force`

On commits that have been pushed and shared.

---

## Why This Rule Exists

* Others depend on your history
* Rewriting breaks their timelines
* Causes conflicts and data loss

These powers are **local-only tools**.

---

## Things to Remember:

* `reflog` is your safety net
* `reset --soft` fixes commits safely
* `reset --hard` erases history
* `cherry-pick` rescues good work
* `rebase -i` cleans history
* Public history must remain untouched

---
