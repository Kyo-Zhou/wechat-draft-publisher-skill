# Pipeline

## Default Execution Order

1. Read article.
2. Resolve metadata.
3. Pick template.
4. Convert to WeChat HTML.
5. Generate preview HTML.
6. Build draft payload.
7. Upload cover if needed.
8. Create draft if requested.

## Failure Checks

Watch for:

- missing credentials
- invalid IP whitelist
- invalid cover media id
- preview shell accidentally uploaded
- ugly HTML that technically works but should not be published

## Review Gate

A draft is not ready just because WeChat accepted it.

Review:

- first screen
- header rhythm
- paragraph density
- body cleanliness
- metadata correctness
