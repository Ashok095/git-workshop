## Global Rules

- **Terminal-first:** All Git commands must be run in the terminal
- **Editor usage:** Editors are allowed **only** for writing code or resolving conflicts
- **Branch rule:** No one commits directly to `main`

---

## Workshop Rule

Although this workshop uses the **Collaborator Model**,  
**all changes must go through feature branches and Pull Requests** to simulate professional review workflows.

---

## Activity 7: The Command Line Sprint

---

## Phase 1: Setup & the `main` Branch

### Instructions (Student A — Owner)

1. Go to GitHub and create a **private** repository named `<student-name>-resume`
2. Add Student B as a **Collaborator**  
   (`Settings → Collaborators`)
3. Clone the repository locally
4. Create a file named `index.html`
5. Paste the skeleton code below
6. Commit and push to `main`

---

### Code Asset: Skeleton (`index.html`)

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Professional Resume</title>
    <link
      href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css"
      rel="stylesheet"
    />
  </head>
  <body class="bg-light">
    <nav class="navbar navbar-dark bg-dark">
      <div class="container">
        <span class="navbar-brand mb-0 h1">DevProfile</span>
      </div>
    </nav>

    <div class="container mt-5">
      <!-- Hero Section Placeholder -->
      <!-- About Section Placeholder -->
      <!-- Experience Section Placeholder -->
    </div>
  </body>
</html>
```

---

### Instructions (Student B — Collaborator)

1. Accept the email invitation
2. Clone the repository to your laptop

---

## Phase 2: Feature Branch 1 — The Hero

### Instructions (Student A)

1. Create and switch to a branch named `feat/hero`
2. Replace `<!-- Hero Section Placeholder -->` with the code below
3. Commit and push the branch
4. Open a Pull Request and merge it

---

### Code Asset: Hero Section

```html
<div class="p-5 mb-4 bg-white rounded-3 shadow-sm">
  <div class="container-fluid py-5">
    <h1 class="display-5 fw-bold">John Doe</h1>
    <p class="col-md-8 fs-4">Full Stack Developer & Git Expert</p>
    <button class="btn btn-primary btn-lg" type="button">Contact Me</button>
  </div>
</div>
```

---

### Instructions (Student B)

Pull the latest `main` branch so you have Student A’s work.

---

## Phase 3: Issues & Feature Branch 2 — About Section

### Instructions (Student A)

Create a GitHub Issue:

- **Title:** Create About Me Section
- **Description:** We need a 2-column layout for the bio

---

### Instructions (Student B)

1. Create and switch to branch `feat/about`
2. Replace `<!-- About Section Placeholder -->` with the code below
3. Commit using a message that closes the issue (e.g. `closes #1`)
4. Push the branch
5. Open a Pull Request

---

### Code Asset: About Section

```html
<div class="row align-items-md-stretch mb-4">
  <div class="col-md-6">
    <div class="h-100 p-5 text-bg-dark rounded-3">
      <h2>About Me</h2>
      <p>
        I am passionate about writing clean code and solving complex problems.
      </p>
    </div>
  </div>
  <div class="col-md-6">
    <div class="h-100 p-5 bg-white border rounded-3">
      <h2>Skills</h2>
      <p>HTML, CSS, JavaScript, Git, GitHub.</p>
    </div>
  </div>
</div>
```

---

### Instructions (Student A)

1. Review Student B’s Pull Request
2. Merge the PR
3. Pull the updated `main` branch locally

---

## Phase 4: Feature Branch 3 — Experience

### Instructions (Student A)

1. Create branch `feat/experience`
2. Add the code below under `<!-- Experience Section Placeholder -->`
3. Commit, push, open PR, and merge

---

### Code Asset: Experience Section

```html
<div class="row">
  <div class="col-12">
    <div class="card">
      <div class="card-header">Work History</div>
      <div class="card-body">
        <h5 class="card-title">Senior Engineer @ Tech Corp</h5>
        <p class="card-text">Led a team of 5 developers to build a CRM.</p>
      </div>
    </div>
  </div>
</div>
```

---

## Phase 5: The Conflict — Theme War

### Instructions (Student A)

1. Switch to `main` and pull latest changes
2. Create branch `style/blue-theme`
3. Change the Hero button class from `btn-primary` to `btn-info`
4. Commit and push
5. Merge the PR immediately

---

### Instructions (Student B)

1. Switch to `main` and pull latest changes
2. Create branch `style/red-theme`
3. Change the **same button** to `btn-danger`
4. Commit and push
5. Attempt to open a PR — GitHub will report a conflict

---

### Instructions (Student B — Resolve the Conflict)

1. Pull the latest `main`
2. Open the conflicted file
3. Resolve the conflict by choosing `btn-success`
4. Remove conflict markers
5. Commit and push

---

# Solution — Activity 7

## Phase 1: Setup & `main` Branch

### Student A (Owner)

```bash
git clone <REPO_URL>
cd <student-name>-resume

# create index.html and paste skeleton code
git add index.html
git commit -m "chore: init project skeleton"
git push origin main
```

---

### Student B (Collaborator)

```bash
git clone <REPO_URL>
cd resume-alpha
```

---

## Phase 2: Feature Branch 1 — Hero

### Student A

```bash
git switch -c feat/hero

# edit index.html (add hero section)
git add index.html
git commit -m "feat: add hero section"
git push -u origin feat/hero
```

Open GitHub → Create PR → Merge into `main`

---

### Student B

```bash
git switch main
git pull origin main
```

---

## Phase 3: Issue & Feature Branch 2 — About

### Student A

- Create Issue **#1** on GitHub

---

### Student B

```bash
git switch -c feat/about

# edit index.html (add about section)
git add index.html
git commit -m "feat: add about section (closes #1)"
git push -u origin feat/about
```

Open GitHub → Create PR

---

### Student A (After Merge)

```bash
git switch main
git pull origin main
```

---

## Phase 4: Feature Branch 3 — Experience

### Student A

```bash
git switch -c feat/experience

# edit index.html (add experience section)
git add index.html
git commit -m "feat: add experience section"
git push -u origin feat/experience
```

Open GitHub → Create PR → Merge

---

## Phase 5: Conflict Branches — Theme War

---

### Student A (Blue Theme)

```bash
git switch main
git pull origin main
git switch -c style/blue-theme

# change btn-primary to btn-info
git add index.html
git commit -m "style: blue theme button"
git push -u origin style/blue-theme
```

Open GitHub → Create PR → Merge immediately

---

### Student B (Red Theme)

```bash
git switch main
git pull origin main
git switch -c style/red-theme

# change btn-primary to btn-danger
git add index.html
git commit -m "style: red theme button"
git push -u origin style/red-theme
```

GitHub will report **Merge Conflict**

---

### Student B (Conflict Resolution)

```bash
git pull origin main
```

- Open `index.html`
- Resolve conflict by using: `btn-success`
- Remove all conflict markers

```bash
git add index.html
git commit -m "fix: resolve button color conflict"
git push
```
