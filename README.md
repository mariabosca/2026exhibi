# Summer Art Residency 2026 — Gallery

A single-page gallery website for hand-drawn works on paper. No build step, no
dependencies — one `index.html` plus the web-optimized images in `images/`.

## View locally

From this folder:

```sh
npx -y http-server -p 8642 -c-1
```

then open <http://localhost:8642>. (Any static file server works.)

## Manage the collection (easiest way)

Open **`admin.html`** on the live site (or locally) — the ✎ link in the site
footer takes you there. Unlock it with a GitHub fine-grained personal access
token (instructions are on the page itself). From there you can:

- upload a new artwork with a caption (the image is resized and flattened onto
  a white background automatically, right in the browser),
- rename captions, reorder works, or remove them.

Every action is a commit to this repository, and GitHub Pages republishes the
site automatically about a minute later.

## Edit the captions by hand

Captions live in `works.json` — one entry per artwork, in display order:

```json
{ "src": "images/subject-1.jpg", "title": "Subject 1" }
```

Edit, commit, push.

## Add artworks by hand

Originals live in `artimages/` (kept out of git — they are ~12 MB each). To
generate a web-sized copy:

```sh
sips -Z 1600 -s format jpeg -s formatOptions 82 "artimages/NAME.png" --out "images/name.jpg"
```

then add an entry for it to `works.json`.

## Publish on GitHub Pages

1. Create a repository on GitHub and push this folder to it.
2. In the repository: **Settings → Pages → Source: Deploy from a branch**,
   branch `main`, folder `/ (root)`.
3. The site appears at `https://<username>.github.io/<repo>/` after a minute.
