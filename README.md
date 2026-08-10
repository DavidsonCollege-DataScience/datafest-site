# Davidson DataFest

## About

This repository stores source code for Davidson College's DataFest website.

DataFest is an annual data science hackathon sponsored by the American Statistical Association (ASA). Davidson's DataFest is organized by the Department of Data Science with sponsorship from local companies and other organizations.

This project is a Quarto website developed in RStudio. Quarto documents (`.qmd` files) render into the `docs/` subfolder.

## Deployment

`.github/workflows/publish.yml` renders the site on every push to `main`, then publishes `docs/` into the `datafest/` subfolder of [`DavidsonCollege-DataScience/datasci-hub`](https://github.com/DavidsonCollege-DataScience/datasci-hub). That hub repo is the only one that deploys to the shared `datasci.davidson.edu` Azure Static Web App — see its README for why (Azure SWA deploys fully replace the app's content, so multiple repos deploying straight to it would clobber each other) and for the one-time secret setup (`HUB_REPO_PUSH_TOKEN`, a fine-grained PAT scoped to just that repo).

The site is served from `https://datasci.davidson.edu/datafest` (a subpath, not the domain root) — `_quarto.yml`'s `site-url` reflects that, and internal asset paths in site-wide config (e.g. the footer logo) are relative rather than root-absolute so they resolve correctly under that subpath.