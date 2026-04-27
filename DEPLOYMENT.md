# Deployment Guide

## GitHub: clone and basic commands

## 1) Clone the repository

Use:

```bash
git clone https://github.com/efmcontrolling-solutions/efmcontrolling
cd efmcontrolling

```

## 2) Basic update commands (only if you update anything in index.html file)

```bash
git status
git add .
git commit -m "Update website content"
git push
```

## Important rule

The main file must be named exactly:

`index.html`

If the file has a different name, deployment will not work as expected for this static page setup.

## Deploy on Vercel

## 1) Import your GitHub repository

- Open Vercel dashboard
- Click **Add New Project**
- Import your GitHub repo

## 2) Select the project

- Choose the correct repository
- Confirm project details

## 3) Build settings

No build settings are required for this project.

Reason:

- It is a static HTML/CSS/JS project
- No framework build step is needed

## 4) Deploy

- Click **Deploy**
- Wait for Vercel to publish your site

## After first deployment

- Every new `git push` to the connected branch triggers auto deployment
- Vercel updates the live site automatically

## How this static project behaves on Vercel

- Vercel serves `index.html` directly
- CSS and JavaScript in the same file run in the browser
- No server runtime is required for this page
