## Collaboration Models (Two Ways to Work)

### 1. Collaborator Model (Private Teams / Companies)

* Maintainer **adds collaborators**
* Contributors can push directly
* Used in small trusted teams

### 2. Fork & Pull Request Model (Open Source)

* Contributors **cannot push directly**
* They fork, work independently, and request changes
* Used by Google, Meta, Linux, Django, etc.


---

## Step 1: SSH – The Professional Authentication Method

### Why SSH?

* HTTPS → username + token
* SSH → cryptographic identity
* No repeated logins
* Industry standard

---

### Generate SSH Key

```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```

* Press **Enter** for file location
* Press **Enter twice** for empty passphrase

---

### Copy Public Key

**Windows**

```bash
cat ~/.ssh/id_ed25519.pub | clip
```

**macOS**

```bash
pbcopy < ~/.ssh/id_ed25519.pub
```

---

### Add Key to GitHub

1. GitHub → Settings
2. SSH and GPG Keys
3. New SSH Key
4. Title: `Laptop`
5. Paste key → Add

---

### Test Connection

```bash
ssh -T git@github.com
```

Expected message:

```
Hi USERNAME! You've successfully authenticated.
```

---

## Step 2: Roles & Responsibilities (Buddy System)

### Student A – Maintainer

* Owns the repository
* Reviews Pull Requests
* Controls merging
* Manages Issues

### Student B – Contributor

* Does not push directly
* Forks the repository
* Works on feature branches
* Requests changes via PR

---

## Step 3: Project Management with Issues (Tickets)

### Rule

> **Never write code without a ticket.**

---

### Create an Issue (Contributor)

1. Go to **Maintainer’s repository**
2. Open **Issues → New Issue**
3. Title: `Feature: Add Testimonial Section`
4. Description: Brief explanation
5. Submit

Note the issue number (e.g. `#1`)

---

## Step 4: Fork vs Clone (Critical Difference)

### Fork

* Creates a **copy on GitHub**
* You own this copy
* Required for open-source contribution

### Clone

* Downloads code to your laptop

### Workflow

```
Maintainer Repo
      ↓
Contributor Fork
      ↓
Local Clone
```

---

## Step 5: Fork and Clone (Contributor)

### Fork the Repository

* Click **Fork** (top-right)
* You now have: `student-b/portfolio-site`

---

### Clone Using SSH

```bash
cd ..
git clone git@github.com:student-b/portfolio-site.git partner-portfolio
cd partner-portfolio
```

Always use **SSH URL**, not HTTPS.

---

## Step 6: The Triangle of Remotes

### The Three Locations

* **Local** → Your laptop
* **Origin** → Your fork (push here)
* **Upstream** → Original repo (pull from here)

---

### Add Upstream Remote

```bash
git remote add upstream git@github.com:student-a/portfolio-site.git
```

Verify:

```bash
git remote -v
```

You should see:

* `origin`
* `upstream`

---

## Step 7: Feature Branch Workflow

### Create Feature Branch

```bash
git switch -c feat/testimonial
```

### Make the Change

Edit `index.html`:

```html
<h2>Testimonials</h2>
```

---

### Commit with Issue Reference

```bash
git commit -am "feat: add testimonial section (fixes #1)"
```

### Why This Matters

* `fixes #1` links code to the Issue
* Merging the PR **automatically closes the ticket**
* This is real DevOps automation

---

### Push Feature Branch

```bash
git push -u origin feat/testimonial
```

---

## Step 8: Opening a Pull Request (PR)

### Create PR on GitHub

1. Go to **your fork**
2. Click **Compare & Pull Request**
3. Verify:

   * **Base:** Student A
   * **Head:** Student B
4. Create Pull Request

---

## Step 9: Code Review (Maintainer)

### Review Process

1. Maintainer opens **Pull Requests**
2. Click the open PR
3. Open **Files Changed**
4. Add comments:

   * Suggestions
   * Questions
   * Approval notes

### Discussion Rules

* Be constructive
* No direct edits to contributor’s branch
* Resolve discussions before merging

---

## Step 10: Merge the Pull Request

Maintainer clicks:

* **Merge Pull Request**
* **Confirm Merge**

---

## Step 11: Observe the Automation

Maintainer checks **Issues** tab:

* Issue `#1` is now **Closed**
* Closed automatically by commit message

This is how real teams track work.

---

## Things to Remember

* SSH is the professional authentication method
* Issues define **what** to build
* Forks protect the main codebase
* Feature branches isolate work
* Pull Requests enable review and discussion
* Code review is a **required professional skill**
* Commit messages can trigger automation

---