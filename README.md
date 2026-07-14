# Summer Art Residency 2026 — Gallery

A single-page gallery website for hand-drawn works on paper. No build step, no
dependencies — one `index.html` plus the web-optimized images in `images/`.

## View locally

From this folder:

```sh
npx -y http-server -p 8642 -c-1
```

then open <http://localhost:8642>. (Any static file server works.)

## Edit the captions

Open `index.html` and find the `works` array near the bottom of the file:

```js
const works = [
  { src: 'images/subject-1.jpg', title: 'Subject 1' },
  ...
];
```

Change each `title` to the caption you want shown under the artwork. The order
of the array is the display order and the order of the lightbox navigation.

## Add or replace artworks

Originals live in `artimages/` (kept out of git — they are ~12 MB each). To
regenerate a web-sized copy:

```sh
sips -Z 1600 -s format jpeg -s formatOptions 82 "artimages/NAME.png" --out "images/name.jpg"
```

then add an entry for it to the `works` array.

## Publish on GitHub Pages

1. Create a repository on GitHub and push this folder to it.
2. In the repository: **Settings → Pages → Source: Deploy from a branch**,
   branch `main`, folder `/ (root)`.
3. The site appears at `https://<username>.github.io/<repo>/` after a minute.
