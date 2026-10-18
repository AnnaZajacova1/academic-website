# Anna Zajacova's academic website

A simple Quarto website with four pages. Substantive content is clearly marked
as a placeholder. GitHub Actions builds and deploys the site to GitHub Pages
after changes are merged into `main`.

## Files

| File | Purpose |
| --- | --- |
| `_quarto.yml` | Website configuration, list of pages, and shared HTML options. |
| `index.qmd` | Home page, introduction placeholders, and forthcoming CV link. |
| `research.qmd` | Research placeholders. |
| `publications.qmd` | Publication-list placeholder. |
| `teaching.qmd` | Teaching placeholders. |
| `_navigation.qmd` | Shared Markdown navigation included in each page. |
| `styles.css` | Minimal typography, spacing, and link styling. |
| `.gitignore` | Excludes generated output and local state from Git. |
| `.github/workflows/publish.yml` | Builds Quarto and deploys `_site/` to GitHub Pages on pushes to `main`. |
| `README.md` | These instructions. |

## How Quarto works

Quarto reads `_quarto.yml` and converts each `.qmd` Markdown file to HTML.
The YAML block between `---` lines sets each page's title. The include shortcode
inserts shared navigation, and Quarto resolves page links to their HTML targets.
CSS controls appearance. `quarto render` writes the website to `_site/`.
Edit the source files: rendering replaces generated HTML.

The explicit page list prevents this README and the shared navigation from
becoming extra pages. Quarto's built-in website project uses `theme: none` and
`minimal: true` to produce simple HTML without JavaScript. Ordinary Markdown
links provide navigation without an interactive menu. Search, a table of
contents, and heading link helpers are disabled. No external fonts or custom
scripts are needed. The preview tool may inject a development-only live-reload
script; that is separate from the rendered website.

## Preview locally

1. Install the [Quarto CLI](https://quarto.org/docs/get-started/).
   These text-only pages do not require R, Python, or Node.js.
2. Open a terminal in this repository's folder (`academic-website`).
3. Run:

   ```sh
   quarto --version
   quarto preview
   ```

4. Open the local address printed in the terminal if a browser does not open
   automatically. Save source changes to refresh the preview.
5. Press `Ctrl+C` in the terminal to stop.

To build without a preview server:

```sh
quarto render
```

Neither command publishes the site.

## Make changes

- Replace **Placeholder:** paragraphs in the `.qmd` files with your own text.
  Markdown uses blank lines between paragraphs, `##` for section headings,
  and `[link text](destination)` for links.
- Keep each page's title block and `{{< include _navigation.qmd >}}` line.
- Edit `_navigation.qmd` to update navigation on all four pages at once.
- Add your real CV as `cv.pdf` in the repository root. The home-page link already
  points there. Remove “forthcoming” from the link and delete the sentence
  saying the PDF has not been added. Quarto copies linked PDF resources to the
  output. Until then, this clearly marked link intentionally has no target.
- Adjust `styles.css` for small visual changes and preview again.

Git records versions of your source files; GitHub stores the repository online.
After reviewing changes, make a Git commit to save a version. Generated files in
`_site/` stay ignored. The GitHub Pages workflow publishes `main`; a pull request
does not publish until you merge it. Generated HTML is uploaded as a workflow artifact rather
than committed to Git.

## Review before accepting

- Preview every page on wide and narrow screens.
- Check typography, spacing, contrast, and keyboard navigation.
- Click the four navigation links on each page.
- Confirm that all substantive content is visibly marked as a placeholder.
- Expect the CV link to be unavailable until you supply the real PDF.
- Run `quarto render` and review errors or warnings.

## Verification and Windows review

Rendered successfully using Quarto 1.10.19 from the official Linux tarball:
https://github.com/quarto-dev/quarto-cli/releases/download/v1.10.19/quarto-1.10.19-linux-amd64.tar.gz

All four pages rendered without warnings or errors. Chromium loaded each page
and its stylesheet, and all 16 navigation combinations were clicked successfully
through a loopback-only test server. All four pages fit a 390px-wide viewport
without horizontal scrolling. Generated pages contain no JavaScript. Desktop
screenshots of all pages and a mobile homepage screenshot were captured.
The forthcoming `cv.pdf` remains the only expected missing link target.

To preview on Windows without installing software on your computer, use a
GitHub Codespace for the branch you want to review:

1. Select that branch on GitHub, then **Code → Codespaces → Create codespace**.
2. In the Codespace terminal, install Quarto in the cloud:

   ```sh
   curl -fL https://github.com/quarto-dev/quarto-cli/releases/download/v1.10.19/quarto-1.10.19-linux-amd64.deb -o /tmp/quarto.deb
   sudo dpkg -i /tmp/quarto.deb
   ```

3. From the folder containing `_quarto.yml`, run:

   ```sh
   quarto preview --host 0.0.0.0 --port 4200 --no-browser
   ```

4. In the **Ports** tab, keep port **4200** set to **Private**, then choose
   **Open in Browser**. Stop the Codespace when finished.

This does not enable GitHub Pages or publish the website. Codespaces usage is
subject to your GitHub account's allowance. Rendered files and screenshots are
not included in this repository.

The existing website's text structure was inspected as a reference; its visual
appearance was not verified in a browser. No outdated substantive content was
reused. WordPress, Hostinger, DNS, and custom-domain settings are not changed
by this workflow.

## Enable the GitHub Pages preview

The preview address will be:
https://annazajacova1.github.io/academic-website/

1. On GitHub, open **AnnaZajacova1/academic-website → Settings → Pages**.
2. Under **Build and deployment**, select **GitHub Actions** as the **Source**.
   Do not add a custom domain. If a starter-workflow suggestion appears, you
   can ignore it: this repository already contains the workflow.
3. Review and merge the GitHub Pages setup pull request. Merging into `main`
   starts the build automatically.
4. Open the repository's **Actions** tab and select **Build and deploy Quarto
   to GitHub Pages**. Wait for both `build` and `deploy` to show green checks.
5. Open the preview address above (or **Settings → Pages → Visit site**).
   The first deployment may take a few minutes to appear.

If you merge before choosing the Pages source and the workflow fails, choose
**GitHub Actions** as described above, then open **Actions → Build and deploy
Quarto to GitHub Pages → Run workflow**, select `main`, and click **Run workflow**.
If repository Actions are disabled, enable them in **Settings → Actions → General**.
If your account or organization does not offer Pages for this repository's
visibility, GitHub will explain that under **Settings → Pages**; do not change
repository visibility without considering what source content would become public.

The Pages website is a publicly accessible preview. It does not replace
annazajacova.com. Leave **Custom domain** empty and do not change DNS or Hostinger.
No `CNAME` file is included. Navigation and CSS use relative URLs so they work
under `/academic-website/`. Future merges into `main` automatically update the
preview. No personal access token or publishing branch is needed.

The workflow pins Quarto to the version used for the local build check.
GitHub's actual build and deployment can be verified after you enable Pages
and merge the pull request; they cannot run from this unmerged setup branch.

The Pages setup was also tested locally under the `/academic-website/` path.
All four pages and their CSS returned HTTP 200, and all 16 navigation
combinations worked in Chromium. The local render completed without errors or
warnings. Workflow YAML and deployment permissions were checked.
