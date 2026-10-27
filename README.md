# Makerspace Wiki

Source for our makerspace's tool & equipment wiki, built with [MkDocs](https://www.mkdocs.org/) + the [Material theme](https://squidfunk.github.io/mkdocs-material/), version-controlled in this repo, and published with GitHub Pages.

## Structure

```
docs/
  index.md              Home page / navigation hub
  cnc.md                CNC machines, software, materials, tool settings, safety, FAQ
  lasercutters.md        Laser cutters, software, materials, tool settings, safety, FAQ
  3d-printers.md          3D printers, software, safety, FAQ
  woodworking.md          Woodworking/carpentry tools, safety, FAQ
  sewing.md               Sewing machines, safety, FAQ
  electronics.md          Electronics bench equipment, safety, FAQ
  img/                    (create as needed) images referenced from pages
mkdocs.yml               Site config and navigation
```

## How changes get made

Nobody pushes straight to `main`. Every change goes through a **Pull Request (PR)**, gets an automatic build check, and is merged by a maintainer. Merging to `main` publishes the site automatically.

### Members (no setup needed)

1. Open the page on the wiki and click the pencil icon or **Edit this page on GitHub** (free GitHub account required).
2. Make the change in GitHub's editor and click **Propose changes**. GitHub copies the repo to your account (a "fork") and opens a PR for you.
3. A maintainer reviews it. If it's good, it goes live within a few minutes of being merged.

No GitHub account? Use **Suggest an update on Discord** at the bottom of any page.

### Maintainers (bigger edits, images, new pages)

1. Clone the repo once: `git clone https://github.com/ApocPro/AltMakersWiki.git`
2. Install MkDocs Material once: `pip install mkdocs-material`
3. Before each piece of work, update and branch off `main`:
   ```bash
   git switch main && git pull
   git switch -c laser-quickstart-update     # short name describing the change
   ```
4. Edit the relevant `.md` file under `docs/`. Each page uses `##` for subcategories (Machines, Software, Materials, Tool Settings, Safety, FAQ) and `###` for each individual machine/software entry. Keep that pattern so the table of contents stays consistent.
5. To add images: put the file in `docs/img/` and reference it with `![alt text](img/filename.jpg)`.
6. Preview locally: `mkdocs serve`, then open `http://127.0.0.1:8000`.
7. Commit, push the branch and open a PR:
   ```bash
   git add -A && git commit -m "Describe the change"
   git push -u origin laser-quickstart-update
   ```
   GitHub then shows a **Compare & pull request** button.
8. Once the **build** check is green, merge the PR and delete the branch.

### Reviewing a PR

- Check the **Files changed** tab. Be strict with the safety pages.
- The **build** check must pass (it runs `mkdocs build --strict`, which catches broken links and missing pages).
- Use **Squash and merge** to keep the history tidy.

## First-time setup checklist

- [ ] Create a new GitHub repo and push this folder to it.
- [ ] In the repo, go to **Settings → Pages** and set the source to **GitHub Actions**.
- [ ] Update `site_url` in `mkdocs.yml` once you know the Pages URL (or your custom domain).
- [ ] Replace the placeholder text (in `[brackets]` and under `_italic prompts_`) in each page with real info — specs, locations, training requirements, actual FAQ content.
- [ ] If you want a custom domain (e.g. `wiki.yourmakerspace.org`), add a `docs/CNAME` file containing that domain and configure DNS per [GitHub's docs](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site).

## Access model

- **Read access:** anyone (repo and site are public).
- **Suggesting changes:** open to all members (crowdsourced).
  - With a GitHub account: use the pencil / "Edit this page on GitHub" button on any wiki page. GitHub forks the repo and opens a Pull Request.
  - Without a GitHub account: use the "Suggest an update on Discord" button, which opens the #wiki-updates channel.
- **Merging and pushing to `main`:** repo owner only for now. Every Pull Request is reviewed before it goes live, which matters most for the safety pages.
- Once it's clear which members contribute regularly, add them as **Collaborators** under **Settings → Collaborators** so they can review and merge too.
