# kexify

**keys simplified** — self-custodial MPC wallet homepage.

Built with Jekyll + Tailwind CSS, deployed on GitHub Pages.

## Pages

- **Home** — hero, safe by default (everyday users), how it works, leave anytime, for developers, chains, free and premium, why kexify. Copy lives in `_data/home/<lang>.yml`; `_includes/home.html` renders it for every language
- **FAQ** — Collapsible Q&A covering security, usage, and technical details
- **About** — Creator info, open source links, tech stack

Each page exists in 11 languages: English at the root, the others in one folder per language
(`vi`, `zh` (zh-Hans), `es`, `pt-BR`, `id`, `th`, `ko`, `ja`, `hi`, `ru`). Language names and nav labels
live in `_data/languages.yml`; the switcher and hreflang links are built from it.

## Links

- App: https://my.kexify.app/ (legacy: https://app.kexify.co/)
- Frontend repo: https://github.com/nguyenkha/kexify-web
- MPC library: https://github.com/coinbase/cb-mpc ([fork](https://github.com/nguyenkha/cb-mpc))

## Local Development

```sh
# Requires Ruby 3+
bundle install
bundle exec jekyll serve
```

## Deployment

Automated via GitHub Actions on push to `main`. See `.github/workflows/jekyll-gh-pages.yml`.
