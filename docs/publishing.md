# Public Site Contract

The organization host is https://inkrajs.github.io/. The approved application
is served at the host root: homepage at /, documentation at /docs. Its source
stays in inkrajs/docs; release.json pins an exact commit rather than main.
The docs build emits static entrypoints for all current and legacy routes.

Only show package installation commands after registry ownership and version
availability are verified. Use the existing Inkra mark and genuine component
captures. Preserve third-party font and media licensing.

Publication is separate from package release. Push to main or manually run
Deploy Inkra website to build the pinned sources, verify archive identity,
run production-route/browser checks and deploy the resulting Pages artifact.
The github-pages environment restricts publication to the approved branch.

Registry consumers install the exact npm version and verify its archive hashes;
local candidate consumers rebuild the pinned source and compare the archive.
Neither mode uses a source alias. The docs package checker verifies the installed
dependency, lockfile and release metadata before the site build.

version.json records website, docs and library commits plus the consumed package
name, version, source and integrity. Each run retains the
complete website artifact for 90 days. To roll back, commit a previously
successful docsRevision to release.json and let the same checks deploy it.
Do not rewrite Git history or point the release at a mutable branch.

The workflow caches npm downloads using site/package-lock.json. Failed
production checks retain the static-server log and available screenshots for
14 days. Deployment stays serialized and non-cancelling; production route
checks are not replaced by a docs CI status or a matching version number.

After deployment, check version.json, the homepage and a direct /docs route.
Run the docs scripts/verify-deployment.mjs with BASE_URL=https://inkrajs.github.io
and verify-homepage.mjs for desktop/mobile interactions and screenshots.
