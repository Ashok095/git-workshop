## Step 1: Deployment Steps

1. Open your **GitHub repository**
2. Click **Settings → Pages** (left sidebar)
3. Under **Build and deployment**, select:

   - Source: **Deploy from a branch**
   - Branch: **main → /(root)**

4. Click **Save**


---

## Troubleshooting Common 404s

| Problem                | Cause                         | Fix                                   |
| ---------------------- | ----------------------------- | ------------------------------------- |
| Blank white page / 404 | File is not `index.html`      | Rename file to `index.html`           |
| Wrong branch deployed  | Deployed from non-main branch | Deploy correct branch: main → /(root) |

- Fix in VS Code → **Commit → Push**
- Wait 60–90 seconds for GitHub Pages to rebuild

---
