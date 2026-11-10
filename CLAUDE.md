# Lindell & Associates — Site Notes

## Overview

Plain HTML/CSS GitHub Pages site. No build step, no Jekyll, no frameworks.
Live at **mikelindell.info** (served from the `main` branch root).

- `index.html` — main one-page site
- `images/` — service card icons (400×400 PNG)
- `IMG_5489.png` — wide logo (used in About card)
- `IMG_5491.png` — square logo (used in nav and footer)
- `support/index.html` — remote support download page (unlisted)
- `downloads/rustdesk-setup.exe` — pre-configured RustDesk Windows installer

---

## Remote Support Page

**URL:** `/support/` — shared by direct link only; not in navigation.

The page has `<meta name="robots" content="noindex">` so search engines skip it.

### How the Windows download works

The download button uses the HTML `download` attribute to rename the file on save:

```html
<a href="/downloads/rustdesk-setup.exe"
   download="rustdesk-host=mikeremote.tplinkdns.com,key=IEMqlZ+k5LoHASWDtogcGKtTBDEW6KNe1VRWytm1WDs=.exe">
```

RustDesk for Windows reads its server and key from the **installer filename**. The long
`download="..."` value is what gets written to disk — the in-repo name stays `rustdesk-setup.exe`.

### Updating the installer

1. Download the new RustDesk Windows x64 `.exe` from https://github.com/rustdesk/rustdesk/releases
2. Rename it to `rustdesk-setup.exe`
3. Overwrite `downloads/rustdesk-setup.exe` with the new file
4. Update the HTML comment in `support/index.html` to record the new version

**Never** add versioned copies (e.g. `rustdesk-1.4.0.exe`). Always overwrite the same filename.

### Gotchas

- **No Git LFS.** GitHub Pages serves only the LFS pointer file, not the real binary. The `.exe` must be committed as a regular git object. The repo has no `.gitattributes` and no LFS configured — keep it that way.
- **Same-origin only.** The `download` attribute rename only works when the file is served from the same origin as the page (`mikelindell.info`). Do not move the installer to GitHub Releases, a CDN, or any other domain.
- **Keep the filename exact.** The `download="..."` value must match the RustDesk-expected format exactly: `rustdesk-host=<server>,key=<pubkey>.exe`. Do not shorten or reformat it.

### Server details

| Item | Value |
|---|---|
| ID / relay server | `mikeremote.tplinkdns.com` |
| Public key | `IEMqlZ+k5LoHASWDtogcGKtTBDEW6KNe1VRWytm1WDs=` |
| Configured filename | `rustdesk-host=mikeremote.tplinkdns.com,key=IEMqlZ+k5LoHASWDtogcGKtTBDEW6KNe1VRWytm1WDs=.exe` |

The key is a **public** key — safe to publish.
