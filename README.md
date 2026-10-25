# Reaction Reels dashboard

A one-page control panel for the private `reaction-reels` repository: make reels, pick custom
moments, follow jobs live, see what is used and left, and change settings or the schedule.

**Live at:** `https://<your-username>.github.io/reaction-reels-dashboard/`

## How it works

- This repository only contains `index.html`. There are no videos, settings or keys in it.
- The page runs in your browser and talks only to `api.github.com`, using a fine-grained token
  that you paste in. The token is stored in your browser and sent nowhere else
  (the page's Content Security Policy blocks every other destination).
- It reads `status.json` and thumbnails from the private repo's `dashboard-data` branch, which the
  daily workflow publishes after every job, and starts jobs through the workflow's
  `workflow_dispatch` API.

## Set up

1. Settings → Pages → Deploy from a branch → `main` / `(root)` → Save.
2. Open the page and use **Create a token with the right permissions**. Give it access to
   **only** the `reaction-reels` repository.

| Permission | Why |
|---|---|
| Actions: Read and write | start jobs, follow runs |
| Contents: Read and write | read the status branch, save `config.toml` |
| Workflows: Read and write | change the daily time (optional) |
| Checks: Read | show error messages from failed runs |

To revoke access at any time, delete the token at
[github.com/settings/personal-access-tokens](https://github.com/settings/personal-access-tokens).
