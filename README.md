# BaroCSS Manual deployment

This repository hosts the BaroCSS Libraries manual on GitHub Pages. Documentation sources remain in [`barocss/barocss`](https://github.com/barocss/barocss/tree/develop/apps/library-docs), under `apps/library-docs`.

## Publish a validated snapshot

1. Validate and publish the source changes in `barocss/barocss`.
2. Open [Deploy Manual to Pages](https://github.com/barocss/manual/actions/workflows/deploy-manual.yml) and choose **Run workflow** on `main`.
3. Enter the complete, validated 40-character source commit SHA in `source_sha`.
4. Wait for both build and deploy jobs to pass, then check the site and `/manual/deployment.json` for the exact source commit.

No floating source branch is published automatically. The workflow fetches public source with full Git history (required by the manual's pinned-source and provenance checks), installs the lockfile with pnpm, runs documentation/API checks, builds `@barocss/library-docs`, and publishes only its `.vitepress/dist` artifact. It uses this repository's standard `GITHUB_TOKEN`; no cross-repository secret or personal access token is needed.

Site URL after successful deployment: https://barocss.github.io/manual/

The initial build uses `BAROCSS_DOCS_BASE=/manual/`. This repository does not deploy or configure the CSS documentation site.

## Future custom domain

A switch to `manual.barocss.com` must be coordinated with a build-base change to `/` and verified separately. Verify domain ownership first. Add the custom domain in this repository's Pages settings before creating the DNS CNAME `manual` pointing to `barocss.github.io` (no repository path). Wait for DNS/certificate readiness, enforce HTTPS, and check the live site. GitHub Actions Pages deployments do not need a `CNAME` artifact file.

[GitHub custom-domain documentation](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site)
