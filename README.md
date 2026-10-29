# Simon Flitter

The holding page at simonflitter.com, replacing the 2013 site. Plain HTML and CSS: no build step, no frameworks, no external fonts or scripts.

## Structure

Everything served lives in `public/`:

- `index.html` is the holding page: "So you found me, now what?!", the glasses and a link to agavetequilana.com
- `404.html` is served for any address that doesn't exist
- `assets/styles.css` holds every style for both pages, including a dark mode
- `assets/glasses.svg` is the glasses, used as a CSS mask so they take the text colour
- `assets/agave.svg` is the agavetequilana.com favicon, used on the link card
- `favicon.svg` and `apple-touch-icon.png` are made from the glasses

The glasses combine the top-left frame from Adobe Stock 345560534 with the arms from the 2013 artwork, traced to a single SVG.

`wrangler.jsonc` configures the Cloudflare Worker that serves it.

## Run locally

Serve the folder so the root-relative links resolve like they will online:

```
python3 -m http.server -d public
```

## Deploy

Connect the repo to a Cloudflare Worker named `simonflitter-website` so every push to `main` deploys. The `routes` in `wrangler.jsonc` attach simonflitter.com and www.simonflitter.com as custom domains, and Cloudflare creates their DNS records and certificates automatically. The domain needs to be on the same Cloudflare account.
