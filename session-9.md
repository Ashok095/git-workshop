## Step 1: From Warehouse to Storefront

* **Repo = Warehouse** (your code lives here)
* **GitHub Pages = Storefront** (the world can visit it)
* Goal: Transform `index.html` into a live site:

```
www.username.github.io
```

---

## Step 2: Deployment Steps

1. Open your **GitHub repository**
2. Click **Settings → Pages** (left sidebar)
3. Under **Build and deployment**, select:

   * Source: **Deploy from a branch**
   * Branch: **main → /(root)**
4. Click **Save**

> Your site is not instant, GitHub will build it next.

---

## Step 3: The Pipeline (Wait)

* Visual: Robots building your site
* Concept:

  * GitHub automatically builds your site
  * Takes **60–90 seconds**
* Look for:

  * Yellow spinning dot → building
  * Green check → live site
* Tip: Refresh the page and check the **link provided in Settings → Pages**

---

## Step 4: Professional Polish

* Go to your repository **main page**
* Sidebar “About” section:

  * **Description:** `My first portfolio built with Git & GitHub`
  * **Website:** Paste live URL (clickable)
  * **Topics:** `#html #css #portfolio`
* Pin your repo to your profile:

  * Profile → Customize Pins → select portfolio-site
* This ensures recruiters see your work first

---

## Step 5: Troubleshooting Common 404s

| Problem                | Cause                                          | Fix                                   |
| ---------------------- | ---------------------------------------------- | ------------------------------------- |
| Blank white page / 404 | File is not `index.html`                       | Rename file to `index.html`           |
| Broken images          | Absolute local path (C:/Users/Desktop/img.jpg) | Use relative path: `images/img.jpg`   |
| Wrong branch deployed  | Deployed from non-main branch                  | Deploy correct branch: main → /(root) |

* Fix in VS Code → **Commit → Push**
* Wait 60–90 seconds for GitHub Pages to rebuild

---

## Step 6: The Humble Brag (LinkedIn)

* Take a **screenshot** of your live site
* Post on LinkedIn:

  ```
  Just built and deployed my first site using Git & GitHub!
  Learned branching, pull requests, and CI/CD. Check it out: [LINK]
  ```
* Tags: `#webdev #git #portfolio`
* This is your **Proof of Work**, better than a resume

---
