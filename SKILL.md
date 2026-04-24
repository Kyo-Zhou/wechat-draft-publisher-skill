---
name: wechat-draft-publisher
description: Use this when the user wants a configurable WeChat Official Account draft publishing workflow: convert Markdown into WeChat-ready HTML, apply article templates, generate local HTML previews, upload covers, assemble draft payloads, and create draft-box entries. The user supplies their own AppID, AppSecret, account defaults, and template choices.
---

# WeChat Draft Publisher

Use `wechat-draft-publisher` for the execution layer of WeChat article publishing.

Typical requests:

- convert this Markdown article into WeChat HTML
- generate a local preview for a WeChat article
- apply a reusable WeChat template to this article
- upload a cover and create a WeChat draft
- use my own AppID and AppSecret to publish a draft
- prepare a draft payload without actually uploading it

## Responsibility

This skill handles publishing execution, not topic discovery or article strategy.

It should:

- read user-supplied publishing configuration
- convert article content into WeChat-ready HTML
- support reusable templates
- generate local preview artifacts
- upload covers when requested
- create WeChat drafts when requested

It should not decide:

- what topic is worth writing
- what the article angle should be
- whether the article is strategically strong

That belongs to an editorial workflow such as `wechat-account-operator`.

## Inputs

Expect these inputs from the user or another workflow:

- article markdown path
- title
- author
- digest
- template choice
- cover path or cover rule
- publishing profile or config path

## Configuration

This skill must be user-configurable.

The user should supply:

- AppID
- AppSecret
- default author
- digest behavior
- comment settings
- template selection
- output paths

Never assume real credentials are stored in the repo.

Read [references/configuration.md](references/configuration.md) before any draft upload work.

## Workflow

Default order:

1. Validate configuration.
2. Inspect article metadata.
3. Select a template or layout route.
4. Produce WeChat HTML.
5. Generate preview HTML.
6. Validate the draft payload.
7. Upload cover if needed.
8. Create draft only when the user asks.

## Publishing Modes

Support these modes:

- `preview-only`
- `html-only`
- `draft-create`

Support these conversion routes:

- `api-mode`
- `ai-mode`
- `custom-html-mode`

## Template System

Templates should be reusable and replaceable.

The template layer should define:

- first-screen structure
- section-header pattern
- highlight blocks
- quote style
- divider style
- ending module

Read [references/templates.md](references/templates.md) before changing template logic.

## Quality Checks

Before upload, verify:

- no debug or preview shell leaked into the article body
- no broken tags
- no obvious encoding corruption
- no over-styled junk that looks unlike native WeChat
- title, author, digest, and cover are all valid

Read [references/pipeline.md](references/pipeline.md) for the operational checklist.

## Open-Source Boundary

This skill is open-source as a framework.

Each user is responsible for:

- their own credentials
- their own production config
- their own account defaults
- their own templates and private brand assets
