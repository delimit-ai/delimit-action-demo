# Delimit Demo

Live demonstration of [Delimit](https://github.com/delimit-ai/delimit) catching breaking API changes on a real pull request.

## What This Demonstrates

A Users API (`openapi.yaml`) gets a v2 migration PR that introduces 6 breaking changes:

| Breaking Change | Severity |
|----------------|----------|
| Required `tenant_id` header added to `GET /users` | High |
| `DELETE /users/{userId}` removed | Critical |
| `userId` type changed from string to integer | Warning |
| `User.id` type changed from string to integer | Warning |
| Required `tenant_id` field added to User schema | High |
| `editor` removed from role enum | Warning |

Plus 1 safe additive change: new `GET /v2/users` endpoint.

## See It In Action

**[View the PR with Delimit's comment →](../../pull/1)**

The PR comment includes:
- Breaking changes table with severity badges
- Semver classification (MAJOR: 1.0.0 → 2.0.0)
- 6-step migration guide
- New additions list

## Try It Yourself

Add Delimit to any repo with an OpenAPI spec:

```yaml
- uses: delimit-ai/delimit-action@v1
  with:
    spec: path/to/openapi.yaml
```

- [GitHub Action](https://github.com/marketplace/actions/delimit-api-governance)
- [MCP Toolkit](https://www.npmjs.com/package/delimit-cli) — `npx delimit-cli setup`
- [Documentation](https://delimit.ai/docs)
