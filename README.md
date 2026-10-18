# Anna Zajacova's academic website

A four-page Quarto website. The homepage follows the supplied screenshot of
annazajacova.com: a grey background, deep red panel with restrained rounded
corners, prominent script name, and a large portrait on the right. On smaller
screens the panel and portrait stack, and navigation uses two columns.
Substantive text is explicitly marked as a placeholder.

## Source files

| File | Purpose |
| --- | --- |
| `_quarto.yml` | Website configuration, page list, and local font resources. |
| `index.qmd` | Homepage composition, About placeholders, and CV availability. |
| `_navigation.qmd` | Shared About, Research, Publications, and Teaching links. |
| `research.qmd`, `publications.qmd`, `teaching.qmd` | Existing content pages. |
| `styles.css` | Shared reading styles and responsive homepage layout. |
| `AZ Photo 1.jpg` | Original portrait, displayed without cropping or filters. |
| `assets/fonts/` | Local Allura font and its SIL Open Font License. |
| `.github/workflows/publish.yml` | Existing Quarto build and GitHub Pages deployment. |

The layout uses Quarto Markdown divs, ordinary links, and CSS grid. No custom
JavaScript, animation, social icons, or external font services are used.
The original JPEG is unchanged. Its photographic background is retained;
the page uses a light grey to complement it. The handwritten name is an
approximation using Allura, rather than an image of the original signature.

## Edit content

- Replace the clearly marked placeholder paragraphs in the `.qmd` files.
- About links to the homepage's `#about` section; the other links open their
  existing pages. Keep that section ID when changing its heading.
- The discreet CV link currently opens the `#cv` availability note, so there
  is no broken PDF link. When ready, add `cv.pdf`, change the homepage link to
  `[CV](cv.pdf)`, update its accessible label, and remove the forthcoming note.
- Keep the original portrait filename, including its spaces, unless you also
  update the image reference in `index.qmd`.
- The generated title block is hidden on the homepage, where the script name
  is the visible main heading. Other pages retain their normal title blocks
  and a comfortable reading width.

## Preview and build

Install the [Quarto CLI](https://quarto.org/docs/get-started/), then open this
repository's folder and run `quarto preview`. Alternatively, `quarto render`
builds all four pages into `_site/`. Generated files stay ignored by Git.
No R, Python, Node.js, or package installation is required for this website.

## Review checks

The homepage redesign was rendered using Quarto 1.10.19 and tested in Chromium:

- All four pages render; all 16 navigation combinations work under the
  `/academic-website/` project path.
- All pages fit viewport widths of 320, 390, 768, 800, 801, 1024, and 1440px.
- The homepage switches from columns to a stacked layout at 800px.
- About and CV anchors work, keyboard focus is visible, and the local font loads.
- The portrait loads at its original aspect ratio; the rendered image file
  matches the original JPEG byte for byte.
- Rendered pages contain no scripts and make no external asset requests.
- Desktop and mobile screenshots were inspected.

## Publishing

The existing workflow deploys pushes to `main` to:
https://annazajacova1.github.io/academic-website/

An unmerged pull request does not trigger this deployment. Review the pull
request before merging. Keep the Pages custom-domain field empty and do not
add a `CNAME` file. This project does not change annazajacova.com, DNS,
Hostinger, or the original WordPress website.
