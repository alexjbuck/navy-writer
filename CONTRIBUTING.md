# Contributing to Navy Writer

Thanks for your interest in Navy Writer. This is a small, independently maintained project, and an unofficial tool: it isn't endorsed by the Department of the Navy. Contributions are welcome, but what gets merged is up to the maintainer. Please read this guide before you put time into a change.

## Before you start

- **Small fixes** (typos, an obvious formatting bug, a broken button): just open a pull request.
- **Anything larger** (a new document type, a change to how documents are laid out, a new dependency, a restructure of the file): open an issue first and describe what you want to do. That way nobody spends a weekend on something that won't be merged.
- **Formatting questions**: if you think the tool gets something wrong compared to SECNAV M-5216.5, open an issue that cites the chapter, paragraph or figure.

## Never post sensitive information

Issues, pull requests, screenshots and sample files in this repository are public. Do **not** include classified information, CUI, PII, or real correspondence. If you need to show a bug, recreate it with made-up names, units and content.

## How the project is laid out

| File | What it is |
|---|---|
| `Navy_Writer_1.0.html` | The tool itself: one self-contained HTML file that users download and open in their browser. |
| `index.html` | The landing page served at navywriter.org (GitHub Pages). |
| `navy-writer-demo.mp4` | The demo video shown on the landing page. |
| `CNAME` | The custom domain setting for GitHub Pages. Don't change it. |

There is no build step. The HTML file you edit is the file people download.

## Ground rules for `Navy_Writer_1.0.html`

Many people run this tool on locked-down government computers, sometimes with no internet access. These rules exist to keep it working there.

1. **It stays a single file.** No separate JS, CSS, font or image files that the tool needs at runtime.
2. **It works fully offline.** No requests to CDNs, web fonts, analytics, or any other network service. Opening the file from disk (`file://`) has to work exactly like opening it from a web server.
3. **User data stays in the browser.** Drafts are kept in the browser's local storage. Don't add anything that sends document content anywhere.
4. **Third-party code is bundled inline, with its license.** If you add or update a library, include its license text in the file, the same way the bundled `docx` library's license is included now. Explain why it's needed in the PR, since every library adds size.
5. **Mind the file size.** People download this file, sometimes over slow connections.
   - Images used only in the interface (backgrounds, banners) should be WebP.
   - Images that end up inside exported documents (seals, flag art) should stay PNG or JPEG so Word and other readers handle them correctly.
   - Don't add large embedded assets without discussing it first.
6. **Don't reformat or minify the whole file.** It's very large, and the embedded base64 images already make diffs hard to read. Change only what your fix needs, so the diff stays reviewable.

## Making a change

1. Fork the repository and create a branch from `main`.
2. Keep each pull request to one change. Two unrelated fixes means two PRs.
3. Before opening the PR, make sure your branch is up to date with `main`. There is no build tooling to catch a branch that quietly undoes someone else's change.
4. Write commit messages that say what changed and why, for example: "Fix flag letter signature alignment for 5x7 stationery (fig 12-8)".

## Testing your change

There are no automated tests yet, so please check your change by hand before opening a PR:

- [ ] Open the file directly from disk (double-click it, don't serve it) in at least one Chromium browser (Edge or Chrome). Firefox too, if you can.
- [ ] Open the developer tools: there should be no console errors, and the Network tab should show no outgoing requests.
- [ ] Try the document types your change affects, and export them. Open the exported files (in Word, for `.docx`) and check them against the relevant SECNAV M-5216.5 figure.
- [ ] Reload the page and confirm your drafts are still there.
- [ ] If you changed embedded assets, note the file size before and after.

## What to put in a pull request

- What the change does and why.
- For formatting changes: the SECNAV M-5216.5 reference (chapter, paragraph or figure) that backs it up.
- How you tested it: browsers, document types, export formats.
- Before and after screenshots for visual changes, with made-up content only.
- The file size change, if any.

## Reporting bugs

Open an issue that includes:

- What you did, what you expected, and what happened.
- Your browser and its version, and whether you opened the file from disk or from navywriter.org.
- The document type involved and, for formatting bugs, the SECNAV M-5216.5 reference.
- A screenshot or exported file made with **made-up content only**.

## License

This repository doesn't have a license file yet. Until the maintainer adds one, please don't assume your contribution can be reused under any particular license. Once a license is added, contributions will be accepted under it.
