# kexify

**keys simplified** — self-custodial MPC wallet homepage.

Built with Jekyll + Tailwind CSS, deployed on GitHub Pages.

## Pages

- **Home** — Hero, how it works, supported chains, features, comparison
- **FAQ** — Collapsible Q&A covering security, usage, and technical details
- **About** — Creator info, open source links, tech stack

## Links

- App: http://app.kexify.co/
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
