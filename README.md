# Search

Deploys [TypeSense](https://typesense.org/) and [DocSearch scraper](https://github.com/typesense/typesense-docsearch-scraper) to `search.tuist.dev` using [Kamal](https://kamal-deploy.org/). Secrets are managed with [fnox](https://github.com/jdx/fnox) (age encryption).

## Prerequisites

- [mise](https://mise.jdx.dev/) installed
- SSH access to `91.99.179.13` as `root`
- The age secret key at `~/.config/fnox/tuist-search-age.txt`

## Setup

```bash
mise install       # Installs Ruby and fnox
mise run setup     # Installs Kamal gem
```

## Secrets

Secrets are encrypted with age via fnox. The encrypted values live in `fnox.toml` and are safe to commit. The private key at `.keys/secret.key` is gitignored.

```bash
mise run secrets:edit    # Interactive TUI
mise run secrets:list    # List all secrets
```

## Deploy

```bash
mise run deploy      # Full deploy
mise run redeploy    # Redeploy without re-pushing the image
mise run logs        # Tail TypeSense logs
```

## DocSearch Scraper

Run the scraper to index content from `tuist.dev/:locale/docs/**` into TypeSense:

```bash
mise run scrape
```

The scraper configuration is in `config/docsearch.json`.

## License

MIT — see [LICENSE](LICENSE).
