# jesshester-site

Personal consulting site for jesshester.com. One static page, no build step, no JavaScript.

## Layout

- `public/index.html`: the whole site. Inline CSS, system fonts, no external requests. Dark color scheme only (`prefers-color-scheme` light mode removed).
- `wrangler.jsonc`: Cloudflare Workers config.
- `package.json`: pins `wrangler` as a dev dependency, with `dev` and `deploy` scripts.

## Hosting

Cloudflare Workers static assets. DNS and domain registration for jesshester.com and jesshester.me are at Cloudflare. Email for both domains runs through Proton Mail — never touch MX or TXT records.

- `jesshester.com` and `www.jesshester.com` are custom domains on the Worker. `www` redirects to the bare domain via a Cloudflare Redirect Rule.
- `jesshester.me` redirects to `jesshester.com` (path-preserving, 301) via a proxied A record placeholder and a Cloudflare Redirect Rule.

## Deploying changes

Requires Node 22+ (`.nvmrc` pins this). Run `nvm use` if your shell is on a different version.

```
npm run dev      # local preview via wrangler dev
npm run deploy   # push to Cloudflare Workers
```

Auto-deploy via Cloudflare Workers Builds is not yet configured. Until it is, deploy manually after pushing.

## Conventions

- Keep the site a single static page with no external requests (fonts, scripts, analytics) unless asked otherwise.
- Public contact address is `hello@jesshester.com`. LinkedIn is `linkedin.com/in/hesterjessica`.
- The experience wording on the page was chosen deliberately for accuracy. Don't strengthen or broaden claims about past work without asking.
- The career timeline is drawn to scale from 2013 to 2027, using percentages: `left = (start - 2013) / 14` and `width = (end - start) / 14`, with dates as decimal years. Recompute these if any dates change.
- Colors are tokens on `:root`. The site is dark-only (no light mode). Keep text contrast at WCAG AA or better when changing them.
- Commit with the GitHub noreply email, not a personal address.
