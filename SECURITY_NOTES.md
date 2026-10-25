# Public source safety notes

This is a sanitised snapshot of the SUMMARIX team application with the team's permission.

## Changes made for public sharing

- Removed hard-coded MongoDB credentials and Naver API credentials from source files.
- Replaced MongoDB connection strings with `MONGO_URI` environment-variable references.
- Replaced the Spring Boot database URL with `${MONGO_URI}`.
- Removed the example user's hard-coded default seed-account password.
- Added `.env.example` and `.gitignore` to prevent accidental secret uploads.
- Omitted Jupyter working notebooks and datasets, internal documents, large serialized ML model files, local vector-store state, and the original Git history.
- Replaced the team README with a public-facing English description; original README contained connection details.

## Important: previously exposed credentials

**The original project's publicly visible source or old commit history contained credentials.** All affected MongoDB, OpenAI and Naver credentials must be **revoked or rotated**, even if they are no longer used in this snapshot. Sanitising a new repository does not erase exposure from the original repository. Check other service credentials as well.

## Before deployment

This snapshot has not been verified to run end-to-end. Configure each external API, database, model dependency, and service endpoint with your own secrets in a private `.env`; do not commit `.env` or service-account files. Verify CORS, authentication, error handling, logging and dependency versions before any public deployment. Some modules are educational prototypes.

## Safe upload

Do not use GitHub **Fork** or push original commit history. Upload only this sanitised directory as a fresh commit to your personal repository. If your personal repo already contains an English README, replace it with this project's README at the root. Inspect `git status` and `git diff --cached` before pushing.
