# Cloudinary image savings bookmarklet

A one-click browser bookmarklet for demoing image performance gains on George (Asda).

It scans the current page for images served from `asda.scene7.com`, re-fetches each one
through Cloudinary in fetch mode with `f_auto,q_auto:eco`, compares `content-length`, and
overlays the byte savings in bright green on top of every image — plus a summary panel
with the page total.

**Install page:** https://pglithro-cloudinary.github.io/george-cloudinary-bookmarklet/

## Usage

1. Open the install page and drag the green button to your bookmarks bar (Safari users: paste the code into a bookmark's address field).
2. Browse to a george.com page and scroll so lazy-loaded images are in the DOM.
3. Click the bookmark.
4. Per-image detail, including both URLs, is logged to the console.

## Notes

- Sizes come from `content-length` on a `HEAD` request; images served without that header are skipped from the totals.
- Delivery uses the `patrickg` Cloudinary cloud. Change `cloudinaryPrefix` in `index.html` to point at a different cloud.
- Savings are format + quality only — no resizing. Responsive sizing would increase them further.
- A site's CSP can block the Cloudinary fetches; check the console if everything comes back empty.

## Editing

The bookmarklet lives as a normal, readable function (`cloudinarySavings`) inside
`index.html`. The page stringifies it at load time to build the `javascript:` URL, so edit
the function and the bookmark code, the copy box, and the displayed source all update together.
