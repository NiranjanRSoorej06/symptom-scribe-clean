# Build Provenance

## Overview

Symptom Scribe uses GitHub Artifact Attestations to generate verifiable
build provenance for production release artifacts.

Build provenance helps verify that an artifact was produced from the
expected source repository through a trusted GitHub Actions workflow.

## What Is Attested?

For each version tag, the provenance workflow:

1. Checks out the tagged source code.
2. Installs project dependencies.
3. Runs linting.
4. Performs TypeScript type checking.
5. Builds the production application.
6. Packages the `dist/` directory into a release archive.
7. Generates a GitHub Artifact Attestation for the archive.
8. Uploads the release artifact to GitHub Actions.

The generated provenance is cryptographically signed and associated
with the artifact.

## When Is Provenance Generated?

Provenance is generated only for version tags matching:

```text
v*
