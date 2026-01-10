## Project Initialization

### Step 1: Navigate to a Working Directory

Exit any existing project directories and move to a general workspace such as **Desktop** or **Documents**:

```bash
cd Desktop
# or
cd Documents
```

---

### Step 2: Create the Project Directory

Create a new folder for the portfolio project and enter it:

```bash
mkdir my-portfolio
cd my-portfolio
```

---

### Step 3: Initialize Git Version Control

Initialize a new Git repository:

```bash
git init
```

> **Note:**
> Git creates a hidden directory named `.git`.
> This directory contains the entire history, configuration, and metadata of the project.
>
> - It is the “brain” of the repository
> - Deleting it permanently destroys the project’s history
> - Never modify or delete the `.git` directory manually

---

### Step 4: Create the Homepage File

Create a file named `index.html` and add the following content:

```html
<!DOCTYPE html>
<html>
  <head>
    <title>My Portfolio</title>
  </head>
  <body>
    <h1>Welcome to My Portfolio</h1>
  </body>
</html>
```

Save the file (`Ctrl + S`).

---

### Step 5: Check Repository Status

Ask Git to show the current state of the repository:

```bash
git status
```

At this stage, Git will indicate that `index.html` is **untracked**.
This means the file exists in the working directory but is not yet being tracked by Git.

---

### Step 6: Stage the File

Add the file to the staging area:

```bash
git add index.html
```

Verify the status again:

```bash
git status
```

The file will now appear in **green**, indicating it is staged and ready to be committed.

---

### Step 7: Commit Using Conventional Commits

Avoid vague or meaningless commit messages such as:

- `first commit`
- `update`
- `changes made`

Instead, we use **Conventional Commits**, a widely adopted standard that improves readability, automation, and collaboration.

This change introduces a new feature (the homepage), so we use the `feat` type:

```bash
git commit -m "feat: initialize portfolio homepage"
```

---

## Conventional Commit Standard

### Commit Message Structure

```
<type>: <short, descriptive summary>
```

### Common Commit Types and When to Use Them

- **feat**
  Used when adding a new feature or user-visible functionality
  Examples:

  - Adding a new page
  - Introducing a new section
  - Implementing a new capability

- **fix**
  Used when correcting a bug or unintended behavior
  Examples:

  - Fixing broken layout
  - Correcting incorrect text
  - Resolving logic errors

- **chore**
  Used for maintenance tasks that do not affect application behavior
  Examples:

  - Updating dependencies
  - Cleaning up files
  - Adjusting configuration

- **refactor**
  Used when improving internal code structure without changing behavior
  Examples:

  - Renaming variables
  - Reorganizing code
  - Simplifying logic

- **docs**
  Used for documentation-only changes
  Examples:

  - Updating README files
  - Adding comments or guides

- **style**
  Used for formatting changes that do not affect logic
  Examples:

  - Whitespace
  - Indentation
  - Code formatting

### Why Conventional Commits Matter

- Create a readable and professional project history
- Enable automated changelogs and releases
- Improve team communication
- Reflect industry-standard engineering practices

---

## Development Cycle 2: Modification and Code Review

### Step 8: Add a Bio Section

Edit `index.html` and add a paragraph below the heading:

```html
<p>I build things with code.</p>
```

Save the file.

---

### Step 9: Review Changes with `git diff`

Before staging, inspect the changes:

```bash
git diff
```

**Understanding the output:**

- Lines prefixed with `-` show removed content
- Lines prefixed with `+` show newly added content

This command allows developers to **review and verify changes** before committing them.

---

### Step 10: Stage and Commit the Feature

Stage all changes:

```bash
git add .
git status
```

This update introduces new content, so it qualifies as a feature:

```bash
git commit -m "feat: add bio section"
```

---

## Development Cycle 3: Bug Fix Simulation

### Step 11: Modify Existing Content

Simulate a correction by updating the main heading:

```html
<h1>Welcome to my World</h1>
```

Save the file.

---

### Step 12: Commit the Fix

This change corrects existing content rather than introducing new functionality, so we use `fix`:

```bash
git add .
git commit -m "fix: update main title text"
```

---

## Viewing Project History

### Step 13: Inspect Commit History

Display the project’s full commit history:

```bash
git log
```

Each commit includes:

- A **unique hash** (snapshot identifier)
- The **author**
- A **clear, structured commit message**

Example output:

```
fix: update main title text
feat: add bio section
feat: initialize portfolio homepage
```

---

## Things To Remember

- Git tracks work in **small, meaningful units**
- Clear commit messages communicate intent
- Conventional Commits reflect professional engineering standards
- A clean commit history demonstrates discipline and experience
