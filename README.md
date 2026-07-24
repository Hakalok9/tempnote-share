# Neytes Share

Public HTTPS landing page for encrypted Neytes invitations.

The repository contains only the static landing page, application icon, and
the Windows installer. Application source code and user data are not published
here.

## Production download deployment

Pushes that change `downloads/` run `Deploy production downloads`. Configure
these secrets in the `production` GitHub environment:

- `PRODUCTION_SSH_HOST`
- `PRODUCTION_SSH_USER`
- `PRODUCTION_SSH_PRIVATE_KEY`
- `PRODUCTION_SSH_KNOWN_HOSTS`

Optional environment variables:

- `PRODUCTION_SSH_PORT` (default: `22`)
- `PRODUCTION_PUBLISH_PATH` (default: `/opt/tempnote-share-publish`)
- `PRODUCTION_SITE_PATH` (default: `/opt/tempnotes/site`)

The SSH user must be able to create/update both configured directories. The
workflow pulls this repository with `git pull --ff-only`, verifies the installer
SHA-256, copies the installer, checksum, and manifest atomically, and verifies
the public manifest through `api.neytes.space`.
