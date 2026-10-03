# Dr. Rohan Doshi — portfolio site

Single-page portfolio. One HTML file, no build step, no CDN dependencies.
Open `index.html` in a browser, or upload the whole folder to any host.

```
Dr Portfolio/
├─ index.html                        the entire page (HTML + CSS + JS inline)
├─ assets/
│  ├─ dr-rohan-doshi.webp            hero portrait, 900×1125
│  ├─ dr-rohan-doshi-square.webp     round headshot on the booking card
│  ├─ dr-rohan-doshi-og.jpg          1200×630 card shown when the link is shared
│  ├─ placeholder.svg                stand-in for the before/after photos
│  ├─ favicon.svg
│  └─ fonts/                         self-hosted Poppins + Playfair Display
└─ README.md
```

## Before it goes live

Every item below is marked in `index.html` with a `TODO(...)` comment, so you can
search the file for `TODO` and work top to bottom.

**`TODO(contact)` — phone, WhatsApp, address.** The placeholder `+91 98765 43210`
appears in six places: the hero button, the booking sidebar (phone + WhatsApp),
the sticky mobile bar (call + WhatsApp), and the JSON-LD block. The WhatsApp
number is also set once in the script at the bottom:

```js
var WHATSAPP_NUMBER = '919876543210';   // country code, digits only, no +
```

Also fill the clinic name and address in the booking sidebar, the medical council
registration number in the footer, and the three social profile URLs.

**`TODO(domain)` — the live URL.** Replace `example.com` in the canonical tag,
the three Open Graph tags and the JSON-LD block.

**`TODO(image)` — the before/after photos.** Both comparison sliders currently
point at `placeholder.svg`. Drop in real consented pairs and update the four
`src` attributes. Shoot each pair at the same distance, angle and lighting,
otherwise the slider exaggerates the result.

**`TODO(content)` — the testimonials.** The three quotes are written placeholders,
labelled `PLACEHOLDER — add real review` so they can't go live by accident.
Replace them with real feedback (the Google Business profile is the easiest
source), using first names or initials only, with the patient's consent.

**`TODO(pages)` — privacy policy and terms.** The consent checkbox and the footer
link to `privacy-policy.html` and `terms.html`, which don't exist yet.

## Where the form goes

Right now the booking form has no backend. On submit it validates, then opens
WhatsApp with the enquiry pre-filled so no lead is lost. To store leads instead,
publish a Google Apps Script as a web app and paste its `/exec` URL here:

```js
var LEAD_ENDPOINT = '';   // paste the Apps Script /exec URL
```

With an endpoint set, the form POSTs the lead and falls back to WhatsApp if the
request fails. The honeypot field and the consent checkbox work either way.

## Editing notes

- **Colours** are CSS custom properties at the top of the `<style>` block
  (`--teal`, `--ink`, `--gold`, …). Change them there and the whole page follows.
- **Icons** are an inline SVG sprite near the top of `<body>`. To add one, append
  a `<symbol id="i-yourname">` and reference it with
  `<svg><use href="#i-yourname"/></svg>`.
- **Fonts** are self-hosted in `assets/fonts/`. If you move the page somewhere
  without that folder, it falls back to system fonts and still looks reasonable.
- **The before/after slider** is a styled `<input type="range">` laid over the two
  images. That is deliberate — it gives pointer drag, touch drag, arrow keys and
  screen-reader support for free, which a custom drag handle does not.
