# Libre WebUI — Unraid Community Applications templates

This repository holds the [Unraid](https://unraid.net) Community Applications (CA) template
for [Libre WebUI](https://librewebui.org), a privacy-first, self-hosted AI platform (chat with
local models via Ollama or cloud providers, plus agents, automations and a knowledge base).

- Website: https://librewebui.org
- Docs: https://docs.librewebui.org
- Main project: https://github.com/libre-webui/libre-webui
- License: Apache-2.0

## What's in here

- `templates/libre-webui.xml` — the CA Docker template for the `libre-webui` container.
- `ca_profile.xml` — repository profile shown by Community Applications (required at the repo
  root for CA repository submissions).
- `LICENSE` — Apache-2.0, matching the main project.

This repo intentionally ships a single container. The "Work" sandboxed task-container feature of
Libre WebUI is not available in this packaging because it needs the host Docker socket mounted,
and store/CA templates should not request that.

## Add this as a template repository in Unraid (manual, no CA listing needed)

Any Unraid user can point their Docker Manager at this repository directly, without it being
listed in the Community Applications app store:

1. Go to **Docker** tab in the Unraid webUI.
2. Click **Add Container**.
3. In the **Template repositories** box near the bottom, add:
   `https://raw.githubusercontent.com/libre-webui/unraid-templates/main/templates/libre-webui.xml`
4. Save, then select the `libre-webui` template from the template dropdown at the top of the
   Add Container page.
5. Before starting the container, set **JWT Secret** to a random 64-character hex value (e.g.
   `openssl rand -hex 32`). This is required; the app does not auto-generate one for store
   deployments.
6. Optionally point **Ollama URL** at a reachable Ollama instance if you want local models.
   Libre WebUI works without Ollama by using cloud providers configured from inside the app.
7. Start the container, open the WebUI, and create the first account — it becomes administrator.

## Submitting to Community Applications (maintainer checklist, not yet done)

This repo is set up to match the current (2026) CA submission format, based on the official
[`unraid/unraid-community-apps-starter`](https://github.com/unraid/unraid-community-apps-starter)
reference repo, but it has **not** been submitted or listed yet. To submit:

1. Push this repo to GitHub (suggested: `libre-webui/unraid-templates`, public).
2. Update the `<TemplateURL>` in `templates/libre-webui.xml` if the org/repo name differs from
   `libre-webui/unraid-templates`.
3. Open an Unraid forum support thread for this template and add it as `<Support>` in the
   template and `<Forum>` in `ca_profile.xml` (see open question below — none exists yet).
4. Go to https://ca.unraid.net/submit/new and run **Validate** and **Scan** against the repo
   URL to check for parser errors.
5. Follow the on-screen submission flow to request the repo be added to Community Applications.
