
# Dumas Lab Website — Publishing Workflow

This website uses **Quarto + Babelquarto** for bilingual rendering and **GitHub Pages (`gh-pages`)** for deployment.

## Branch structure

- `main`: Website source files (`.qmd`, `_quarto.yml`, CSS, images, etc.) and rendered output in `docs/`.
- `gh-pages`: Published website (rendered HTML files and assets at the branch root).
- GitHub Pages deploys from `gh-pages` → `/(root)`.

**Important:** Always develop on `main`. Never manually edit the `gh-pages` branch.

---

## 1. Render the bilingual website

After editing the website, open the R console and run:

```r
babelquarto::render_website()
```

This renders both English and French versions into `docs/`.

Check the preview to make sure both languages look correct.

## 2. Commit and push source changes

In the VS Code terminal, make sure you are on `main`:

```bash
git branch
```

The active branch should have an asterisk (`*`) beside `main`.

Then stage, commit, and push your changes:

```bash
git add .
git commit -m "Describe website updates"
git push origin main
```

Replace `"Describe website updates"` with a short description of your changes.

If there are no new changes to commit, skip the commit step.

## 3. Publish to GitHub Pages

Still on `main`, run:

```bash
quarto publish gh-pages --no-render
```

The `--no-render` flag is important because Babelquarto has already rendered both language versions. This prevents Quarto from performing a separate render before publishing.

If prompted, confirm the GitHub Pages publishing destination.

## 4. Check the live website

Visit:

https://micheladumas.github.io/

Allow a little time for GitHub Pages to deploy the changes. Refresh the page if necessary.

---

## Complete workflow — quick reference

**Every time you update the website:**

1. Edit source files on `main`.
2. Render both languages:

   ```r
   babelquarto::render_website()
   ```
3. Commit and push source files:

   ```bash
   git add .
   git commit -m "Update website"
   git push origin main
   ```
4. Publish the rendered website:

   ```bash
   quarto publish gh-pages --no-render
   ```
5. Check the live website:

   https://micheladumas.github.io/

---

## Useful Git commands

| Command                  | What it does                         |
| ------------------------ | ------------------------------------ |
| `git status`           | Check for uncommitted changes        |
| `git branch`           | See your branches and current branch |
| `git switch main`      | Switch to the source branch          |
| `git pull origin main` | Pull the latest source changes       |
| `git log --oneline -5` | View the five most recent commits    |
| `git remote -v`        | Check your GitHub remote             |

**Golden rule:** Work on `main`, render with Babelquarto, publish with Quarto. No manual copying, no subtree commands, and no need to switch branches to deploy!
