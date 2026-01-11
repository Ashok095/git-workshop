# Git Configuration

Before we start coding, we need to introduce ourselves to Git and configure our environment. These are one-time settings that will apply globally to your computer.

## 1. Verify Installation

First, let's ensure Git is actually installed on your machine.

```bash
git --version
```

---

## 2. Set Your Identity

Git attaches a name and email to every change you make. This acts like a signature for your code history.

Git needs to know whom to blame if anything goes wrong.

```bash
git config --global user.name "Your Name"
git config --global user.email "your@email.com"
```

> **Note:** This email does not need to be the same as your GitHub account, but it is recommended to match them so GitHub can attribute your commits to your profile.

---

## 3. Handle Line Endings

Different Operating Systems handle "new lines" (when you press Enter) differently.

- **Windows** uses Carriage Return + Line Feed (`CRLF`).
- **Mac/Linux** uses just Line Feed (`LF`).

We need to tell Git how to handle this so that code looks the same on everyone's computer.

**For Windows Users:**

```bash
git config --global core.autocrlf true
```

- **What it does:** When you save files (commit), Git converts them to `LF`. When you download files (checkout), Git converts them back to `CRLF` for Windows to understand.

**For Mac / Linux Users:**

```bash
git config --global core.autocrlf input
```

- **What it does:** When you save files, Git converts them to `LF`. When you download files, it leaves them as `LF` (since Mac/Linux already understands that).

---

## 4. Set Default Branch Name

Historically, the default branch in Git was called `master`. The modern standard is `main`.

```bash
git config --global init.defaultBranch main
```

---

## 5. Verify Configuration

Finally, let's check that all your settings were saved correctly.

```bash
git config --list
```
