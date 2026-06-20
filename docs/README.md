# Boostoraa-style SMM Panel — Frontend (Static)

## Status
**Frontend only.** No backend, no real auth, no real payments, no real
order processing. All forms/buttons are visual only. Built as a static
HTML/CSS shell for backend developers to wire up.

## Folder Structure

```
/public          → Pages a visitor sees BEFORE logging in
                    index.html       ← homepage (also serves as sign-in)
                    signup.html      ← sign up
                    services.html    ← public pricing/services list
                    api.html         ← public API info/marketing page
                    terms.html       ← terms of service

/panel            → Pages a user sees AFTER logging in (the client panel)
                    new-order.html   ← landing page after login
                    services.html
                    orders.html
                    add-funds.html
                    api.html
                    affiliates.html
                    child-panel.html
                    mass-order.html
                    updates.html
                    account.html

/assets
  /css            → style.css — single shared stylesheet, all pages use this
  /js             → (empty for now — reserved for shared JS once
                     interactivity / backend wiring begins)
  /img            → (empty for now — reserved for logo, icons-as-files,
                     screenshots, etc.)

/docs             → project notes, this README, handoff notes
```

## Design Tokens (in `assets/css/style.css` under `:root`)

| Token | Value |
|---|---|
| Font | Cairo (Google Font) |
| Primary navy | `#13364d` |
| Accent gold | `#eaa349` |
| Primary blue (buttons/links) | `#1f6fd6` |

All colors/spacing are defined as CSS variables at the top of `style.css`.
**Change values there, not inline in individual pages** — every page pulls
from the same variables, so a single edit updates the whole site.

## How Pages Are Linked

Pages inside `/panel` link to each other using relative filenames
(e.g. `href="orders.html"`) since they all live in the same folder.
Pages reference the stylesheet via `../assets/css/style.css` since
`/panel` is one level below the project root.

## What's NOT Built Yet (out of scope for this phase)
- Any backend: authentication, database, payment gateway, order
  fulfillment / provider API integration, real wallet balance logic
- Any JS interactivity beyond the mobile sidebar toggle and basic form
  display (no real validation, no real submission)
- Linking public pages to panel pages on actual login (currently separate
  static folders — a real app would route `/public` → `/panel` post-auth)

## For the Next Developer
- Every page shares the same sidebar + topbar markup (copy-pasted at the
  top of each file, not yet componentized — if you introduce a framework
  like React/Vue/Next, this is the natural place to extract a `<Sidebar>`
  and `<Topbar>` component)
- Form inputs have no `name` attributes yet — add these when wiring to a
  real backend
- All sample data (order history rows, service lists, transaction history)
  is hardcoded placeholder content — replace with real data bindings
