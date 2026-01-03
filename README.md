# Spec Build Scripts API

API specification for Kaptain Build Scripts.

## Purpose

This specification defines the contract for `kaptain-build-scripts`:

- **Entry points**: Scripts consumers can call
- **Inputs**: Environment variables each script accepts
- **Outputs**: Values each script produces
- **Exit codes**: What each exit code means
- **Tool requirements**: Required tools and versions

## Files

- `API-spec.yaml` - The API specification

## Consumers

This spec is consumed by:

| Consumer | Use |
|----------|-----|
| `kaptain-build-scripts` | Build-time validation |
| `buildon-github-actions` | Generate actions and docs |
| `buildon-azure-devops` | Generate pipelines (future) |
| `buildon-gitlab-ci` | Generate CI config (future) |

## Entry Points

| Script | Purpose |
|--------|---------|
| `basic-quality-checks` | Validate branch naming and commit quality |
| `versions-and-naming` | Calculate versions and Docker naming |
| `docker-build-dockerfile` | Build Docker image from Dockerfile |
| `docker-build-retag` | Pull and retag upstream image |
| `docker-push` | Push image to registry |
| `docker-registry-logins` | Authenticate to container registries |

## Versioning

Spec version: `major.minor`

- Major: Breaking changes to existing inputs/outputs
- Minor: New features, new scripts, non-breaking changes

Scripts version `X.Y.Z` implements spec version `X.Y`.

## Validation

```bash
# Validate spec against schema
yq -o json API-spec.yaml | jsonschema ../spec-scripts-api-schema/API-schema.yaml
```
