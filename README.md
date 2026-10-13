# Scripture Practice — Mobile Web App

A free static Progressive Web App (PWA) for private Scripture memorization. Uses the same `verses.json` format as your Python `Main.py` file. No server, API key, paid hosting, or domain required.

## Open locally

Open `index.html` in a desktop browser to try the sample Psalm 23 (KJV) verses. For full PWA/offline support, use an HTTPS host, such as GitHub Pages.

## Publish using GitHub Pages

1. Sign in at https://github.com/ and create a **public** repository named `scripture-practice` (or another name).
2. Choose **Add file → Upload files**. Upload the **contents** of this folder: `index.html`, `style.css`, `app.js`, `manifest.webmanifest`, `sw.js`, `icon-192.png`, `icon-512.png`. The README is optional. Do **not** upload your `verses.json`, any NIV text, or your Python practice history.
3. Commit changes.
4. In the repository, choose **Settings → Pages → Build and deployment → Deploy from a branch → main → / (root) → Save**.
5. The site will be accessible at `https://YOUR-GITHUB-USERNAME.github.io/scripture-practice/` once deployment is complete. The address varies with the repository name.
6. On your phone, visit the site. On iPhone use Safari → Share → Add to Home Screen. On Android use Chrome's menu → Install app or Add to Home screen (wording varies).
7. Open **Library → Choose a JSON file** and import the *existing* `verses.json` from your OneDrive/Python project. A complete bank will replace the sample demo verses.

## Data privacy & backups

- Only KJV demo text (US public-domain sample) is included in the published source. Your own NIV text is imported **locally into your browser's storage** and is never uploaded to GitHub or to this app's server. The site has no backend.
- **Do not upload `verses.json` to a public GitHub repository.** This is important for Bible translation copyright as well as personal privacy.
- Data currently does **not** automatically sync between desktop and phone or with OneDrive. Export a full backup from Library periodically. Browser storage can be erased when site data is cleared or when using private browsing.
- `Export verses.json` writes a Python-compatible object of reference-text pairs.
- `Export history.jsonl` writes Python-compatible line-delimited history records.
- PWA offline use should work after the deployed site has been opened online at least once; internet may be needed for web fonts, which have system fallbacks.

## Scoring and practice mechanics

- Random passage chooses a random chapter within the selected scope, then chooses a random contiguous saved run. If the chapter is shorter than the requested count, its maximum run is used.
- Exact passage accepts `5`, `5-14`, or `all`, and checks all verses are present.
- First letters are compared case/punctuation/space-insensitively using Levenshtein edit distance. Weighted session accuracy is calculated using expected initial counts, matching the Python approach.
- Previous-verse context and first-words hints are optional; assisted attempts are marked in history. Skips receive 0%.

## Later: OneDrive sync

We can add authenticated OneDrive integration through Microsoft Graph/MSAL after the site has a fixed HTTPS address. A registered Microsoft app, delegated permissions, and testing against your personal OneDrive account would be required. No client secret or Bible API key should be included in static client-side code.
