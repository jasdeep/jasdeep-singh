# Changes

## 2026-09-11 — Migrating `content/note` from the WordPress export

Imported and cleaned up the old blog posts (from `sites/jasdeep-data-from-blogs/notes`) into this site's `content/note` section, and converted the section to Hugo page bundles.

1. **Copied posts into `content/note`.** Copied 178 markdown files from `sites/jasdeep-data-from-blogs/notes`; 5 files already present (`_index.md`, `2007-05-17_hello-world.md`, `2020-05-22_how-to-fight-traffic-chaos.md`, `2020-05-22_the-stress-market.md`, `2021-09-28_bhagat-singh-shirt.md`) were left untouched.

2. **Added `excerpt:` to every post's front matter** — a one-line English summary of the post's content (poem theme/subject for poetry, topic summary for technical/personal posts).

3. **Downloaded externally-hosted post images.** Every `![alt](https://...)` markdown image pointing at a remote host (mostly old `wordpress.com`/`blogger.com` URLs) was downloaded into `static/img`, named `<first 25 chars of the source .md filename>_<original image filename>`, and the in-post reference rewritten to the local path. One broken reference (`http://barcamp4`, not a real image URL) was left as-is.

4. **Renamed the `tags:` front matter key to `categories:`** across all posts (values unchanged).

5. **Added `author:` to every post's front matter.** Where a post is clearly a poem/song/essay by a named poet or writer (e.g. Shah Hussain, Paash, Amrita Pritam, Shiv Kumar Batalvi, Surjeet Patar, Amarjit Chandan, Bulle Shah, Bhagat Singh, and others), that person's name was used, even when Jasdeep only translated or crossposted it. Personal/technical/opinion posts with no other named author default to `Jasdeep Singh`. A few explicitly-anonymous/folk pieces use `Anonymous`.

6. **Fixed spacing before the comments-section rule.** Where the `_Crossposted from [...]_ ` line was immediately followed (no blank line) by the `---` rule that precedes the `### Comments:` section, a blank line was inserted between them (108 files).

7. **Converted every post-related image to WebP** using ImageMagick (`magick`).

8. **Converted every post into a Hugo leaf bundle.** Each `content/note/<slug>.md` became `content/note/<slug>/index.md`. (`_index.md`, the section's own list page, was left at the top level.)

9. **Moved each post's image(s) into its own bundle folder**, appending `-featured` to the filename before the `.webp` extension (e.g. `logo.jpg` → `logo-featured.webp`), and updated the in-post image reference to the new relative filename. This also covered the three pre-existing loose images sitting directly in `content/note` (`ubuntulogo.png`, `screenshot.webp`, `bhagat-singhs-shirt-ludhiana-nov-09-pic-amarjit-chandan.webp`), which were converted/moved into their respective post's bundle the same way.

Net result: 182 posts under `content/note`, each its own page bundle with an `index.md` and any images alongside it as `<name>-featured.webp`; `static/img` no longer holds any post-specific images.
