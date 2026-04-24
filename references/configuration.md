# Configuration

The open-source version must not contain real production credentials.

## User-Supplied Config

Each user should provide:

- `appid`
- `appsecret`
- `default_author`
- `default_digest_mode`
- `comment_settings`
- `default_template`
- `output_dir`

## Recommended Files

- `config.example.yaml`
- `config.local.yaml`

`config.example.yaml` should be committed.

`config.local.yaml` should be ignored.

## Safety Rules

- never hard-code real credentials
- never commit local production config
- keep account-specific defaults outside the open-source template logic
