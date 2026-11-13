# OKB Waterway Registration Portal

**Live page:** https://oplankontrabaha.github.io/registration/

The Oplan Kontra Baha (OKB) portal that DPWH regions use to register waterways and drainages, map existing registry entries, and extend waterways already on the map.

## How it works

- This repository holds only the page (`index.html`). It is served by GitHub Pages.
- Everything else stays in the Apps Script project: region sign-in, the SSOT lookups, writing to the staging sheet, the approval emails, and the SSOT bridge.
- The page talks to the Apps Script web app through its `/exec` URL (`OKB_API_URL` near the top of the script in `index.html`). Calls are `POST` requests with a `text/plain` JSON body of the form `{ fn, args }`, answered by `doPost()` in `Code.gs`.

## Apps Script deployment settings

The web app must be deployed with:

- **Execute as:** Me
- **Who has access:** Anyone

After changing `Code.gs`, use **Deploy → Manage deployments → Edit → New version** so the `/exec` URL stays the same.

## Trying the page without the server

Open the page with `?preview=1` added to the address. It signs in with any password and uses sample data, and nothing is written.

## Related

- Approval queue: https://oplankontrabaha.github.io/registrationapprovals/
