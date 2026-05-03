# Alexi Gugushvili — Personal Academic Website

This is a Hugo-based personal academic website, configured for automatic deployment to GitHub Pages.

---

## SETUP GUIDE (Step by Step)

### Step 1: Install Git

**Windows:**
1. Download Git from https://git-scm.com/download/win
2. Run the installer — accept all default settings
3. After installation, open **Git Bash** (search for it in the Start menu)

To verify it worked, type in Git Bash:
```
git --version
```
You should see something like `git version 2.xx.x`.

---

### Step 2: Install Hugo

**Windows:**
1. Download Hugo **extended** from https://github.com/gohugoio/hugo/releases
   - Look for `hugo_extended_0.139.0_windows-amd64.zip` (or a newer version)
2. Extract the zip file to a folder, e.g. `C:\Hugo\bin\`
3. Add that folder to your system PATH:
   - Search "Environment Variables" in Windows
   - Under "System variables", find `Path`, click Edit
   - Click New, add `C:\Hugo\bin\`
   - Click OK everywhere
4. Open a new terminal and verify:
```
hugo version
```

---

### Step 3: Preview your site locally

1. Open Git Bash (or a terminal)
2. Navigate to this folder:
```
cd "C:\Users\alexig\OneDrive - Universitetet i Oslo\Documents\WEBPAGE\Personal"
```
3. Run the Hugo development server:
```
hugo server
```
4. Open your browser and go to: http://localhost:1313
5. You should see your website! Press `Ctrl+C` to stop the server.

---

### Step 4: Create a GitHub account and repository

1. Go to https://github.com and create a free account
   - Use the username `alexigugushvili` if available (this determines your URL)
2. Click the **+** icon (top right) → **New repository**
3. Name it: `alexigugushvili.github.io`
   - This special name tells GitHub to serve it as a website
4. Keep it **Public**
5. Do NOT check "Add a README" (we already have one)
6. Click **Create repository**

---

### Step 5: Push your site to GitHub

In Git Bash, navigate to your site folder and run these commands one by one:

```bash
cd "C:\Users\alexig\OneDrive - Universitetet i Oslo\Documents\WEBPAGE\Personal"

git init
git add .
git commit -m "Initial commit: personal academic website"
git branch -M main
git remote add origin https://github.com/alexigugushvili/alexigugushvili.github.io.git
git push -u origin main
```

GitHub will ask for your credentials the first time. If prompted for a password, you may need to create a **Personal Access Token** instead:
1. Go to https://github.com/settings/tokens
2. Click "Generate new token (classic)"
3. Give it a name, select "repo" scope
4. Copy the token and use it as your password

---

### Step 6: Enable GitHub Pages

1. Go to your repository on GitHub: `https://github.com/alexigugushvili/alexigugushvili.github.io`
2. Click **Settings** (top menu)
3. Click **Pages** (left sidebar)
4. Under "Build and deployment":
   - Source: **GitHub Actions**
5. That's it! The workflow we set up will build and deploy automatically.
6. Wait 1-2 minutes, then visit: **https://alexigugushvili.github.io**

---

### Step 7 (Optional): Connect a custom domain

If you purchase a domain like `alexigugushvili.com`:

1. At your domain registrar, add these DNS records:
   - Type `A`, Name `@`, Value: `185.199.108.153`
   - Type `A`, Name `@`, Value: `185.199.109.153`
   - Type `A`, Name `@`, Value: `185.199.110.153`
   - Type `A`, Name `@`, Value: `185.199.111.153`
   - Type `CNAME`, Name `www`, Value: `alexigugushvili.github.io`

2. In your GitHub repo Settings → Pages → Custom domain:
   - Enter `alexigugushvili.com`
   - Check "Enforce HTTPS"

3. Update `baseURL` in `hugo.toml` to `https://alexigugushvili.com/`

---

## HOW TO EDIT YOUR SITE

### Adding your photo
1. Save your profile photo as `profile.jpg`
2. Place it in the `static/images/` folder
3. It will automatically appear on the homepage and About page

### Editing content
All content is in the `content/` folder as Markdown files:
- `about.md` — your biography
- `research.md` — research areas
- `publications.md` — publication list
- `teaching.md` — courses and supervision
- `cv.md` — curriculum vitae
- `contact.md` — contact information

Edit these files in any text editor (Notepad, VS Code, etc.).

### Adding a CV PDF
1. Create a `static/files/` folder
2. Save your CV as `Gugushvili_CV.pdf` inside it
3. In `cv.md`, uncomment the download link

### Publishing changes
After editing, push changes to GitHub:
```bash
cd "C:\Users\alexig\OneDrive - Universitetet i Oslo\Documents\WEBPAGE\Personal"
git add .
git commit -m "Update website content"
git push
```
The site will automatically rebuild in 1-2 minutes.

---

## FOLDER STRUCTURE

```
Personal/
├── hugo.toml              ← Site configuration
├── content/               ← Your content (edit these!)
│   ├── _index.md
│   ├── about.md
│   ├��─ research.md
│   ├── publications.md
│   ├─��� teaching.md
│   ├── cv.md
│   └── contact.md
├── layouts/               ← HTML templates
│   ├── _default/
│   ├── partials/
│   └── index.html
├── static/
│   ├── css/style.css      ← Styling
│   └── images/            ← Put profile.jpg here
├── .github/workflows/     ← Auto-deployment config
└── README.md              ← This file
```
