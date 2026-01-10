## Step 1: The Mechanic vs The Driver

### Concept

* **Terminal = Mechanic**

  * Understand the engine
  * Fix the low-level mechanics
* **VS Code GUI = Driver**

  * Operate quickly
  * Focus on coding and workflow

> Terminal is for setup and emergencies. GUI is for fast development.

---

## Step 2: Installing GitLens (The HUD)

1. Open **VS Code → Extensions**
2. Search **GitLens**
3. Install the free version (ignore any trial prompts)
4. Reload VS Code

---

### GitLens “Ghost Text”

* Click on a line in **index.html**
* See inline Git blame:

  ```
  You, 2 days ago • feat: initial commit
  ```
* Instantly know **who changed what and when**

---

## Step 3: GUI Workflow Basics

| VS Code Button  | Git Equivalent         | Action                |
| --------------- | ---------------------- | --------------------- |
| + (Stage)       | `git add`              | Stage file            |
| - (Unstage)     | `git restore --staged` | Unstage file          |
| Arrow (Discard) | `git restore`          | Discard changes       |
| ✔ (Commit)      | `git commit`           | Commit staged changes |

---

## Step 4: The Sync Button

* Icon: circular arrows 🔄
* Displays: `1↑ 2↓`
* Click → runs **git pull + git push** automatically
* Ensure **origin/upstream** are set up correctly
* **One click to sync with GitHub**

---

## Step 5: X-Ray Vision (File History)

* Open **GitLens sidebar → File History**
* Split view:

  * **Left:** Old version
  * **Right:** Current version
* Benefit: See evolution of a file visually
* Use it to review code or debug changes **before blaming a teammate**

---

## Step 6: Visual Conflict Resolution

### Scenario: The Grand Finale

1. Create conflict (setup only in terminal):

```bash
git switch -c feat/red-title
# Change Title color to RED
git commit -am "feat: red title"

git switch main
# Change Title color to BLUE
git commit -am "feat: blue title"
```

2. Merge branches:

```bash
git merge feat/red-title
```

* Git reports **CONFLICT!**

---

### Resolving Conflicts in VS Code

1. Open **index.html**
2. Look at **Merge Editor** (bottom-right button → Resolve in Merge Editor)
3. Layout:

   * **Incoming (Top Left):** Feature branch (Red)
   * **Current (Top Right):** Main branch (Blue)
   * **Result (Bottom):** Final merged version
4. Choose a side:

   * Tick left (Red)
   * Tick right (Blue)
   * Or type custom (e.g., Purple) in **Result**
5. Click **Complete Merge → Commit**

> No manual deletion of `<<<<<<<`, `=======`, `>>>>>>>` markers needed

---

## Step 7: Quick Live Example

* Update footer year via GUI:

  * Stage with `+`
  * Commit with `✔`: `"chore: update year via gui"`
  * Sync using **Sync button**
* Observe GitHub for automatic update
* Review changes visually using GitLens

---

## Step 8: When to Use Terminal vs GUI

| Tool            | Use Case                                                                                |
| --------------- | --------------------------------------------------------------------------------------- |
| **Terminal**    | Setup (SSH, remotes), emergency fix (reset, reflog), cherry-pick, squash                |
| **VS Code GUI** | Regular development, commits, staging, pushing/pulling, merge conflicts, history review |

> Rule of thumb: **Terminal for power, GUI for speed**

---

## Things to Remember

* **VS Code + GitLens = Cockpit HUD**
* Visual workflow reduces human error
* Inline blame helps accountability
* GUI merge editor avoids messy conflict markers
* Sync button simplifies push/pull operations
* Terminal knowledge is still essential for advanced operations

---
