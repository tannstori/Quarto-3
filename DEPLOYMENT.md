# Deployment Guide

How to deploy Minerva to GitHub Pages.

---

## 📋 Prerequisites

1. A [GitHub](https://github.com) account
2. [Git](https://git-scm.com/) installed locally
3. [Quarto](https://quarto.org/docs/get-started/) v1.3+ installed
4. The site builds successfully with `quarto render`

---

## 🚀 Method: Manual Deploy (Recommended for Beginners)

This method renders locally and pushes to GitHub.

### Step 1: Create a New GitHub Repository

1. Go to [github.com/new](https://github.com/new)
2. Repository name: `minerva` (or your preferred name)
3. Description: "Faroese Mathematics Education"
4. Visibility: **Public** (required for free GitHub Pages)
5. **Do NOT** initialize with README, .gitignore, or license
6. Click **Create repository**

### Step 2: Initialize Local Git

Open terminal in your project folder:

```bash
# Initialize git repository
git init

# Add all files
git add .

# Create initial commit
git commit -m "Initial commit: Minerva Quarto site"
```

### Step 3: Connect to GitHub

Replace `YOUR_USERNAME` and `REPO_NAME` with your values:

```bash
# Add remote origin
git remote add origin https://github.com/YOUR_USERNAME/REPO_NAME.git

# Push to GitHub
git branch -M main
git push -u origin main
```

### Step 4: Enable GitHub Pages

1. Go to your repository on GitHub
2. Click **Settings** → **Pages** (left sidebar)
3. Under "Source", select:
   - **Branch:** `main`
   - **Folder:** `/docs`
4. Click **Save**
5. Wait 2-3 minutes for deployment

### Step 5: Access Your Site

Your site will be available at:

```
https://YOUR_USERNAME.github.io/REPO_NAME/
```

---

## 🔄 Updating the Site

After making changes:

```bash
# 1. Render the site
quarto render

# 2. Stage changes
git add .

# 3. Commit
git commit -m "Description of changes"

# 4. Push
git push
```

GitHub Pages will automatically update within a few minutes.

---

## ⚡ Method: GitHub Actions (Automatic)

This method builds automatically when you push.

### Step 1: Create Workflow File

The file `.github/workflows/quarto-publish.yml` should contain:

```yaml
name: Quarto Publish

on:
  push:
    branches: [main]

jobs:
  build-deploy:
    runs-on: ubuntu-latest
    permissions:
      contents: write
    steps:
      - uses: actions/checkout@v4
      
      - uses: quarto-dev/quarto-actions/setup@v2
      
      - name: Render Quarto Project
        run: quarto render
        
      - name: Deploy to GitHub Pages
        uses: peaceiris/actions-gh-pages@v3
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          publish_dir: ./docs
```

### Step 2: Enable Actions

1. Go to repository **Settings** → **Actions** → **General**
2. Under "Workflow permissions", select **Read and write permissions**
3. Click **Save**

### Step 3: Configure Pages

1. Go to **Settings** → **Pages**
2. Under "Source", select:
   - **Branch:** `gh-pages` (created by Actions)
   - **Folder:** `/ (root)`
3. Click **Save**

Now the site rebuilds automatically on every push!

---

## 🔍 Troubleshooting

### Site Shows 404

- Wait a few minutes for GitHub Pages to deploy
- Check that **Settings → Pages** shows correct branch/folder
- Verify `docs/` folder was pushed to GitHub
- Check `_quarto.yml` has `output-dir: docs`

### CSS/Styles Not Loading

- Ensure `site-url` in `_quarto.yml` matches your GitHub Pages URL
- Clear browser cache (Ctrl+Shift+R)
- Re-render with `quarto render`

### Build Fails in Actions

1. Check the **Actions** tab for error logs
2. Common issues:
   - Missing Quarto files
   - Syntax errors in `.qmd` files
   - Invalid YAML in `_quarto.yml`

### Pages Not Updating

- Force push: `git push --force`
- Check Actions tab for workflow status
- Verify files changed in `docs/` folder

---

## 📁 Important Files for Deployment

```
quarto_3/
├── _quarto.yml          # Must have output-dir: docs
├── docs/                # Built site (pushed to GitHub)
│   ├── index.html
│   ├── search.json
│   └── ...
└── .github/
    └── workflows/
        └── quarto-publish.yml  # (Optional) Auto-build
```

---

## 🔗 Useful Links

- [Quarto: Publishing to GitHub Pages](https://quarto.org/docs/publishing/github-pages.html)
- [GitHub Pages Documentation](https://docs.github.com/en/pages)
- [GitHub Actions for Quarto](https://github.com/quarto-dev/quarto-actions)

---

## ✅ Deployment Checklist

- [ ] Repository created on GitHub
- [ ] Local git initialized and connected
- [ ] Site rendered with `quarto render`
- [ ] All files committed and pushed
- [ ] GitHub Pages enabled in Settings
- [ ] Site loads at GitHub Pages URL
- [ ] Styles and math display correctly
