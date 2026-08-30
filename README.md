# Asterhue support site

The pages the App Store and Japanese law require: a support URL and a privacy policy URL
(§0.5.4), the 特定商取引法 disclosure, and a small front page. Support and privacy carry both
languages on one page, Japanese first, so nothing depends on a script running or on
guessing the reader's locale. The 特商法 page is Japanese only — it exists to satisfy a
Japanese statute.

Static HTML and one stylesheet. No build step, no framework, no external requests:
these pages have to load for a reviewer on a bad connection.

## Before publishing

Nothing to fill in — the contact address and the seller details are set.

## Publishing

GitHub Pages, the same way `exposir-support` is published. Create a public repository
`asterhue-support` under `kuserin`, push the contents of this folder to its root, and turn
on Pages for the default branch. It is served at

    https://kuserin.github.io/asterhue-support/

which is the URL `LegalLinks.swift` points at and the one to enter in App Store Connect.

If a domain is bought later, add a `CNAME` file and point the DNS at Pages, exactly as
`exposir.app` is set up, then change the single `base` constant in `LegalLinks.swift`. The
paths do not move.

## Keeping it honest

The privacy policy describes what the app actually does, and it is specific enough that
it can go out of date. Re-read it whenever the answer to any of these changes:

- the app makes a network request of its own (today it makes none)
- an analytics or crash-reporting SDK is added (today there are none)
- palettes leave the device — iCloud sync is on the v2 list
- the photo library is accessed as anything other than add-only
- the eyedropper's source image is written to disk (today it is memory-only)
- advertising returns (removed entirely — see `docs/decisions.md`)

And re-read `tokushoho.html` if the price changes, the seller identity changes, or the app
is ever sold through anything other than the App Store.
