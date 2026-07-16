# Worked example: wire.report MLB Signals API

This directory holds a real, public OpenAPI spec — the **WireIntel MLB Signals API**,
published on RapidAPI — used to demonstrate the merge gate for AI-written code on a
genuine third-party contract.

- `wire-report-mlb.yaml` — the published API spec (OpenAPI 3.1).
- `.github/workflows/delimit-mlb.yml` — runs `delimit-ai/delimit-action@v1` on every
  pull request that touches this spec, producing a signed, replayable attestation for
  the change.

## What it shows

When a pull request proposes a breaking change to this spec — for example, removing the
required `confidence_score` field from `GameSignalResponse` — the merge gate classifies
it as a **MAJOR** change and posts the breaking-change detail on the PR, backed by a
signed attestation of the verdict.

Add the same gate to any repo with an OpenAPI spec:

```yaml
- uses: delimit-ai/delimit-action@v1
  with:
    spec: path/to/openapi.yaml
```
