## Concept Overview

### Git vs GitHub

* **Git**

  * A version control tool
  * Tracks history **on your computer**
  * Works fully offline

* **GitHub**

  * A hosting platform for Git repositories
  * Stores code **on the internet**
  * Enables collaboration, backups, and deployment

> You can use **Git without GitHub**.
> You cannot use **GitHub without Git**.

---

## Step 1: Authentication Safety Check

Before connecting to GitHub, verify how Git authenticates on your system.

### Run:

```bash
git config --global credential.helper
```

### Expected Result

* **Windows:** `manager`
* **macOS:** `osxkeychain`

### Why This Matters

* GitHub **does not accept passwords** in the terminal anymore
* Authentication must happen via **browser popup**
* If Git asks for a password in the terminal → **STOP** and ask for help

This check prevents most authentication failures before they happen.

---

## Step 2: Create an Empty Repository on GitHub

1. Go to **github.com**
2. Click **New Repository**
3. Repository name: `portfolio-site`
4. Visibility: **Public**
5. **IMPORTANT:**

   * Do NOT add README
   * Do NOT add `.gitignore`
   * Do NOT choose a license

> The repository must be completely empty.

---

## Step 3: Connect Local Repo to GitHub (Remote)

### Add the Remote

Copy the command provided by GitHub, similar to:

```bash
git remote add origin https://github.com/YOUR_USERNAME/portfolio-site.git
```

### Rename Branch (If Required)

```bash
git branch -M main
```

### What This Does

* `origin` becomes a **nickname** for the GitHub URL
* Git now knows **where to push your code**

---

## Step 4: Push Code to GitHub (First Upload)

### Run:

```bash
git push -u origin main
```

### What to Watch For

* A **browser popup** asking you to sign in
* Click **“Sign in with browser”**
* Approve the request

**If the terminal asks for a password:**
Do not type anything. Pause and ask for help.

### Verify

* Refresh your GitHub repository page
* Your files should now be visible online

---

## Step 5: The “Two Laptops” Scenario (Cloning)

### Concept

* `git init` → start a brand-new project
* `git clone` → copy an existing project from the cloud

### Simulate a Second Laptop

```bash
cd ..
git clone https://github.com/YOUR_USERNAME/portfolio-site.git portfolio-laptop-2
```

You now have:

* `portfolio-site` → Laptop 1
* `portfolio-laptop-2` → Laptop 2

---

## Step 6: Create a Conflict

### Laptop 2 Makes a Change

```bash
cd portfolio-laptop-2
```

Edit `index.html`:

```html
<h1>Laptop 2 Rules</h1>
```

Commit and push:

```bash
git commit -am "feat: laptop 2 change"
git push
```

---

### Laptop 1 Makes a Different Change

```bash
cd ../portfolio-site
```

Edit `index.html`:

```html
<h1>Laptop 1 is Better</h1>
```

Commit:

```bash
git commit -am "feat: laptop 1 change"
```

Attempt to push:

```bash
git push
```

### Result

**Push is rejected**
Git refuses because the remote has changes you do not have.

---

## Step 7: Pull and Face the Conflict

### Pull the Latest Changes

```bash
git pull
```

Git reports a **merge conflict**.

This means:

* Two people changed the **same line**
* Git cannot decide which version to keep

---

## Step 8: Resolve the Conflict Manually

Open `index.html`. You will see something like:

```html
<<<<<<< HEAD
<h1>Laptop 1 is Better</h1>
=======
<h1>Laptop 2 Rules</h1>
>>>>>>> origin/main
```

### Rules for Resolving

* `HEAD` → Your local version
* Incoming → Remote version
* Delete **all conflict markers**
* Choose one version or combine them

### Example Resolution

```html
<h1>Laptop 1 and Laptop 2 are Friends</h1>
```

Save the file.

---

## Step 9: Finish the Merge

```bash
git add .
git commit -m "fix: resolve merge conflict"
git push
```

### Outcome

* Conflict resolved
* Remote updated
* Both timelines are now aligned

---

## Things to remember

* Git works locally; GitHub is the shared cloud
* Authentication should happen via browser, not terminal
* `push` sends code up, `clone` pulls everything down
* Conflicts are normal and **not errors**
* Humans resolve conflicts, Git only reports them

---