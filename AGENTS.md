# AGENTS.md

This is a Hugo static site (theme: `hugo-apero`) for jasdeep-singh.com.

## Build

- `hugo server` — run the local dev server.
- `hugo` — build the site into `public/`.

## Structure

- `content/note/` — blog posts ("Digital Garden" notes), imported from an old WordPress export. Each post is a Hugo leaf bundle: `content/note/<slug>/index.md` plus any of its own images alongside it. `content/note/_index.md` is the section list page and stays at the top level (not a bundle).
- `static/img/` — site-wide images not tied to a specific post (theme assets, avatars, etc.). Post-specific images live in the post's own bundle folder instead.
- `themes/hugo-apero/` — the Hugo theme.

## Conventions for `content/note` posts

- Front matter keys: `title`, `author`, `date`, `slug`, `draft`, `excerpt`, `categories`. Use `categories`, not `tags`.
- `author` is the actual poet/writer/creator of the piece when identifiable (even if Jasdeep only translated or crossposted it); otherwise `Jasdeep Singh`.
- A post's own images sit next to its `index.md` in the same bundle folder, named `<original-name>-featured.webp`, and are referenced from the body with a relative path (no leading slash).
- Images should be WebP; convert with ImageMagick (`magick input output.webp`) rather than adding new binary formats to the repo.

See `CHANGES.md` for a log of past changes made to this content.
