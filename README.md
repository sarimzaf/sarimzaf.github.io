# Personal Site

A personal academic website built with [Astro](https://astro.build).

---

## Local development

**Prerequisites:** Node.js 22 or later.

```bash
# Install dependencies
npm install

# Start the dev server (visit http://localhost:4321)
npm run dev

# Build for production
npm run build

# Preview the production build locally
npm run preview
```

---

## Updating content

| What to change | Where |
|---|---|
| Bio, education, contact links | `src/pages/index.astro` |
| Research papers | `src/pages/research.astro` — edit the `papers` array |
| Projects | `src/pages/projects.astro` — edit the `projects` array |
| Navigation | `src/layouts/Layout.astro` — edit the `navLinks` array |
| Styles | `src/styles/global.css` |

### Adding a profile photo

1. Place your photo in `public/` (e.g. `public/photo.jpg`).
2. In `src/pages/index.astro`, replace the `<div class="profile-photo-placeholder">` block with:

   ```astro
   <img src="/photo.jpg" alt="Sarim Zafar" class="profile-photo" />
   ```

---

## Deploying to GitHub Pages

### Step 1 — Create a GitHub repository

1. Go to [github.com](https://github.com) and sign in.
2. Click the **+** icon (top-right) → **New repository**.
3. Name it exactly **`<your-username>.github.io`** — for example `sarimzaf.github.io`.
   - This special name tells GitHub to serve it as your personal site at `https://<your-username>.github.io`.
4. Leave it **Public**, leave everything else at defaults, and click **Create repository**.

### Step 2 — Connect your local project to GitHub

Open a terminal in the project folder and run:

```bash
# 1. Initialise git (skip if the folder is already a git repo)
git init

# 2. Add all files to the first commit
git add .
git commit -m "Initial commit"

# 3. Point your local repo at the GitHub repo you just created
#    Replace <your-username> with your actual GitHub username
git remote add origin https://github.com/<your-username>/<your-username>.github.io.git

# 4. Push to GitHub
git branch -M main
git push -u origin main
```

If Git asks for credentials, use your GitHub username and a
[Personal Access Token](https://github.com/settings/tokens) (not your password).

### Step 3 — Enable GitHub Pages with GitHub Actions

1. On your repository page, click **Settings** → **Pages** (left sidebar).
2. Under **Source**, select **GitHub Actions**.
3. Save. GitHub will now use the workflow in `.github/workflows/deploy.yml` to build and deploy your site automatically every time you push to `main`.

### Step 4 — Visit your site

After the first push, wait ~1–2 minutes. The Actions tab on your repository will show the deployment running. Once it turns green, your site is live at:

```
https://<your-username>.github.io
```

### Making updates

Every time you push changes to the `main` branch, GitHub Actions rebuilds and redeploys the site automatically. You do not need to do anything else.

```bash
git add .
git commit -m "Update bio"
git push
```

---

## Project structure

```
.
├── public/               # Static assets (images, favicon, etc.)
├── src/
│   ├── layouts/
│   │   └── Layout.astro  # Shared page layout (nav, footer, head)
│   ├── pages/
│   │   ├── index.astro   # Home / About
│   │   ├── research.astro
│   │   └── projects.astro
│   └── styles/
│       └── global.css
├── .github/
│   └── workflows/
│       └── deploy.yml    # GitHub Actions deployment workflow
├── astro.config.mjs
└── package.json
```
