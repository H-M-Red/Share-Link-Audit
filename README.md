# Share Link Auditor — Mintlify docs

This is a real-world artifact from an enterprise Airtable deployment: a security
tool built to give admins visibility into share link risk that the native
Admin Panel doesn't currently expose.

## Deploy this to a live Mintlify site

1. Create a new GitHub repo and push everything in this folder to it.
2. Go to [dashboard.mintlify.com](https://dashboard.mintlify.com), sign in,
   and connect the new repo. Mintlify auto-deploys from the repo root.
3. It should build immediately since `docs.json` and `api-reference/openapi.yaml`
   are already valid (checked locally with `mint broken-links`, zero issues).
4. Optional: swap the placeholder `favicon.svg` for something real, and update
   the GitHub link in `docs.json`'s navbar to point at your actual repo.

## Local preview

```
npm install -g mint
mint dev
```

This serves the site locally so you can review it before pushing live.

## What's real here

Everything. This isn't a hypothetical wrapper anymore. `openapi.yaml`
documents Airtable's actual Enterprise Audit Log API endpoint
(`GET /v0/meta/enterpriseAccounts/{enterpriseAccountId}/auditLogEvents`,
the exact real endpoint the automation calls) plus the real Airtable Web
API endpoints for the three actual tables in the base
(`Share Links`, `Share Link Audit Trail`, `Config`), using their real
field names, taken directly from the base's live schema and the hourly
automation's actual script. The risk levels (Info/Low/Medium/High), the
event types (enableShare/disableShare/configureShare/regenerateShare),
and the status values (Active/Disabled/Regenerated) are the literal
values used in production, not renamed or simplified for presentation.
