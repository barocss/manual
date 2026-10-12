# BaroCSS Manual deployment

This repository hosts the BaroCSS Libraries manual on GitHub Pages. Documentation sources remain in [`barocss/barocss`](https://github.com/barocss/barocss/tree/develop/apps/library-docs), under `apps/library-docs`.

## Publishing

Deployment setup is being prepared. The first deployment will use an explicitly validated, full source commit SHA; no floating branch is published automatically.

The deployment workflow will fetch public source with full Git history (required by the manual's pinned-source and provenance checks), install the lockfile with pnpm, run documentation checks, build `@barocss/library-docs`, and publish only its `.vitepress/dist` artifact using this repository's standard `GITHUB_TOKEN`. No cross-repository secret or personal access token is needed.

Initial URL: https://barocss.github.io/manual/

The initial build uses `BAROCSS_DOCS_BASE=/manual/`. A later custom-domain switch to `manual.barocss.com` must use `/` and be verified separately. This repository does not deploy or configure the CSS documentation site.
