# WeChat Draft Publisher Skill

An open-source skill for configurable WeChat Official Account draft publishing.

一个面向公众号发布执行层的开源 skill，用来把 Markdown 草稿转换成微信可用 HTML、生成预览、套模板、上传封面并创建草稿。

This skill focuses on the execution side of the workflow:

- convert Markdown into WeChat-ready HTML
- apply reusable article templates
- generate local preview HTML
- upload covers
- assemble draft payloads
- create draft-box entries

It is designed as a framework. Each user supplies their own credentials and publishing defaults.

## Best For

- operators who already have article drafts
- teams that want reusable WeChat templates
- users who want a configurable Markdown-to-draft pipeline

适合：

- 已经有文章初稿、只差排版和入库的人
- 想把公众号发布动作做成统一流程的团队
- 需要“模板 + 预览 + 草稿创建”一条链的人

## What This Skill Does

This skill helps answer:

- how do I convert an article into WeChat HTML
- how do I preview it locally
- how do I standardize first-screen and section layout
- how do I create a WeChat draft using my own config

## What This Skill Does Not Do

This skill does not:

- decide which topic is worth writing
- choose the article angle for you
- bundle real AppID / AppSecret
- ship one account's private defaults

Use a separate editorial layer such as `wechat-account-operator` for topic strategy and drafting.

## Quick Start

Recommended setup:

1. copy `config.example.yaml` to `config.local.yaml`
2. fill in your own `AppID` and `AppSecret`
3. choose a template such as `default`, `editorial`, or `minimal`
4. feed in `article.md` and metadata
5. preview before creating the draft

Typical requests:

- `把这篇 md 转成公众号 HTML`
- `用 editorial 模板出一个公众号预览`
- `检查这篇草稿有没有不适合直接上传的问题`
- `用我的配置创建公众号草稿`

## Repository Structure

- `SKILL.md`: trigger description and working instructions
- `agents/openai.yaml`: UI-facing metadata
- `references/configuration.md`: config boundary and safety rules
- `references/templates.md`: template-layer definition
- `references/pipeline.md`: publishing pipeline checklist
- `config.example.yaml`: starter configuration
- `templates/default/`: neutral WeChat article structure
- `templates/editorial/`: more magazine-like layout starting point
- `templates/minimal/`: lightweight low-decoration layout starting point

## Suggested Workflow

1. Copy `config.example.yaml` into a local config file.
2. Add your own AppID and AppSecret.
3. Choose a template.
4. Convert article Markdown into WeChat HTML.
5. Generate and review preview HTML.
6. Create a draft when satisfied.

## Recommended Input Package

This skill works best when the editorial layer passes in:

- `article.md`
- `meta.yaml`
- title
- author
- digest
- template name
- optional cover image or cover prompt

That keeps the publishing layer generic and user-configurable.

See:

- [examples/input/article.md](./examples/input/article.md)
- [examples/input/meta.yaml](./examples/input/meta.yaml)

## Local-Only Files

Do not commit these:

- `config.local.yaml`
- real credentials
- generated preview outputs
- account-specific presets and brand assets

## Example Workflow

1. receive `article.md` and `meta.yaml`
2. resolve title / author / digest / template
3. generate WeChat HTML
4. generate local preview
5. validate body cleanliness and metadata
6. upload cover if needed
7. create draft only on explicit request

## Pairing

Recommended pair:

- `wechat-account-operator-skill`
- `wechat-draft-publisher-skill`

The first handles topic and writing. The second handles conversion and publishing.

## Open-Source Boundary

Safe to open-source:

- config examples
- template system
- conversion pipeline
- preview and draft scaffolding

Keep private:

- real credentials
- production profiles
- account-specific presets
- private brand assets
