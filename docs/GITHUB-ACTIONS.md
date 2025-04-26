## 📋 Overview of GitHub Actions Workflows

| Workflow Name                         | Purpose | Trigger |
|----------------------------------------|---------|---------|
| `ci-draft.yml`                         | Builds the project, updates OpenAPI spec with draft version, and publishes artefact for pull requests. | `pull_request` |
| `ci-released.yml`                      | On release, updates OpenAPI spec with release version, builds, and publishes artefact to GitHub Packages. | `release` |
| `push-draft-openapi-spec.yml`          | Pushes the draft OpenAPI spec to APIHub in an unpublished state. | `push` (to `main` or `master`) |
| `publish-released-openapi-spec.yml`    | Pushes the released OpenAPI spec to APIHub, validates it, and sets it as the default version. | `release` |
| `lint-openapi.yml`                     | Lints and validates OpenAPI documents and JSON schema example responses on pull requests. | `pull_request` |


## 🔒 Required Secrets and Variables

Ensure the following secrets are configured in your GitHub repository:

| Secret/Variable Name  | Description                                 |
|-----------------------|---------------------------------------------|
| `APIHUB_API_KEY`  | API token for authenticating with SwaggerHub |
| `APIHUB_ORGANISATION` | SwaggerHub username or organisation name    |


## OpenAPI Specification and Data Schema Validation

This repository includes a GitHub Action to validate OpenAPI specifications and data payload JSON Schemas.

### Run Validation Locally

> Node must be installed on your machine.

Install dependencies:
```bash
npm install -g @stoplight/spectral-cli ajv-cli jsonlint
```

Validate the OpenAPI specification:
```bash
spectral lint "openapi/**/*.{yml,yaml}"
```
Documentation: https://stoplight.io/open-source/spectral

Validate the data payload JSON Schemas:
```bash
jsonlint -q ./openapi/path/to/example_payload.json
```

Validate the data payload JSON Schemas:
```bash
ajv --spec=draft2020 --strict=false -s "./openapi/path/to/schema.json" -d "./openapi/path/to/example_payload.json"
```
Documentation: https://ajv.js.org/
