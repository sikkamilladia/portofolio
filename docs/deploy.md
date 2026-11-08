# Deploy to GitHub Pages
1. Create a public repo, e.g. `portfolio`, on GitHub.
2. In this folder: `git init && git add . && git commit -m "Initial portfolio"`
3. `git branch -M main && git remote add origin https://github.com/<user>/portfolio.git && git push -u origin main`
4. GitHub → Settings → Pages → Source: **Deploy from a branch**, branch `main`, folder `/ (root)` → Save.
5. After ~1 minute the site is at `https://<user>.github.io/portfolio/`.
