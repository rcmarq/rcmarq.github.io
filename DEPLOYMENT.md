# Researcher Site – Deployment Guide

## File Structure

```
your-repo/
├── index.html        ← Main site (edit this to update content)
├── style.css         ← All styles
├── cv.pdf            ← Your CV (add this yourself)
├── photo.jpg         ← Your photo (add this yourself)
├── notebooks/        ← Your Jupyter notebooks (for Binder)
│   ├── gene_expression_explorer.ipynb
│   └── ...
└── .nojekyll         ← Tells GitHub Pages to serve files as-is
```

---

## 1. Deploy to GitHub Pages (5 minutes)

### Step 1 — Create a GitHub repo

1. Go to [github.com/new](https://github.com/new)
2. Name it `YOUR_USERNAME.github.io` (replace with your actual GitHub username)
   - This gives you a free URL like `https://YOUR_USERNAME.github.io`
   - Alternatively, name it anything (e.g. `research-site`) for a URL like `https://YOUR_USERNAME.github.io/research-site`
3. Set it to **Public**
4. Click **Create repository**

### Step 2 — Push the files

```bash
cd /path/to/this/folder
git init
git add .
git commit -m "Initial site"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPO.git
git push -u origin main
```

### Step 3 — Enable GitHub Pages

1. In your repo on GitHub, go to **Settings → Pages**
2. Under **Source**, choose **Deploy from a branch**
3. Select branch: `main`, folder: `/ (root)`
4. Click **Save**

Your site will be live at `https://YOUR_USERNAME.github.io` (or `/YOUR_REPO`) within ~60 seconds.

---

## 2. Updating the Site

Edit any file, commit, and push — GitHub Pages automatically redeploys.

```bash
# After editing index.html or style.css:
git add .
git commit -m "Update publications"
git push
```

Changes are live within ~30 seconds.

---

## 3. Custom Domain (Optional)

If you have a domain (e.g. `janesmith.com`):

1. Add a file named `CNAME` to the repo root containing just your domain:
   ```
   janesmith.com
   ```
2. In your domain registrar's DNS settings, add a CNAME record:
   - Name: `www` → Value: `YOUR_USERNAME.github.io`
3. In GitHub Pages settings, enter your custom domain and enable **Enforce HTTPS**

---

## 4. Adding Your Content

### Photo
- Add `photo.jpg` to the repo root
- In `index.html`, find the comment `✏️ EDIT: Replace the placeholder` and follow the instructions (uncomment the `<img>` tag, delete the placeholder div)

### CV PDF
- Add `cv.pdf` to the repo root
- The download button in the CV section will work automatically

### Publications
- In `index.html`, find the `<!-- PUBLICATIONS -->` section
- Copy/paste a `<div class="pub-card">` block and fill in your details
- Set `data-type` to `journal`, `conference`, or `preprint` for filtering

### Jupyter Notebooks (Binder)
1. Add your `.ipynb` files to a `notebooks/` folder in the repo
2. Optionally add a `requirements.txt` or `environment.yml` to the repo root with your dependencies
3. Go to [mybinder.org](https://mybinder.org), enter your repo URL, and the path to each notebook
4. Copy the generated link and paste it into the `href` of the corresponding "Launch Notebook" button in `index.html`

### Contact Form (Formspree)
1. Go to [formspree.io](https://formspree.io) and create a free account
2. Create a new form — you'll get an endpoint like `https://formspree.io/f/abcd1234`
3. In `index.html`, find `action="https://formspree.io/f/YOUR_FORM_ID"` and replace `YOUR_FORM_ID` with your actual ID

---

## 5. Key Things to Edit in `index.html`

Search for `✏️ EDIT` comments throughout `index.html` — each one marks something to personalize:

- `<title>` and `<meta name="description">` — your name and bio summary
- `.nav-brand` — your name in the navbar
- About section — bio, tags, social links
- Publications — replace example papers with your own
- CV section — positions, education, funding, awards
- Tools section — Binder links for your notebooks
- Contact section — email, office address, office hours
- Footer — your GitHub repo URL
