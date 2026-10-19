# Retail Theme fork

This repository is Hussein's fork of Naidapa Theme for Frappe/ERPNext v15.
The GitHub repository is named `retail_theme`; the Python/Frappe app name remains
`naidapa_theme`. Keeping the internal name preserves imports and upstream merges.
The original MIT license and attribution remain in place.

## Git remotes

- origin: https://github.com/husseinabaqer/retail_theme.git (your fork)
- upstream: https://github.com/iammusabutt/naidapa_theme.git (original project)

Work and commit in this repository. Push your commits to origin when ready;
fetch upstream to review future original-project updates before merging them.

## Install on another v15 site

```sh
cd /path/to/v15-bench
bench get-app https://github.com/husseinabaqer/retail_theme.git
bench --site your-site install-app naidapa_theme
bench build --app naidapa_theme
bench --site your-site clear-cache
bench --site your-site clear-website-cache
```

On the present bench the checkout is `apps/naidapa_theme`. If cloning manually,
use that directory, install the editable Python package, and register the app in
`sites/apps.txt` before install-app. A repository name alone does not rename the
Python package. Use Theme Settings on each site for its title, sidebar logo,
favicon and workspace order. These settings are site data, not shared fixtures.
Put that site's main workspace first. Do not install alongside another Desk
theme on the same site without checking compatibility.

## Local compatibility changes

- Bound and batch asynchronous page patching; disconnect the observer while
  applying its own updates to avoid self-triggered rendering loops.
- Preserve native list/report filter panels while replacing the workspace menu.
- Apply native workspace visibility to the configured sidebar menu.
- Use a packaged fallback logo instead of a missing /files image.
- Take the Desk title from site Theme Settings and apply the RTL class when needed.

## Current installation

Installed on `almukhtar.localhost` on 2026-10-19, with Appliance Shop first in
the menu and the shop title set in Theme Settings. A pre-install database/config
and public/private-files backup is under the site's private/backups directory.
Dependencies installed; schemas synchronized by install-app; app assets built.
Syntax and installation metadata inspected. No browser or business-flow tests
were run, following the development-phase instruction.

After changes, build the app and clear caches. Reload the browser completely.
A running web process must restart/reload after a new Python app is installed.
