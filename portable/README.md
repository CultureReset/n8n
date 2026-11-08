# portable/ — standalone ai-stack installer for `n8n`

Packaging only; no application source in this folder was changed. Repo license applies unchanged.

```
portable/install.sh --preflight    # check prerequisites: docker
portable/install.sh --dry-run      # print every command, change nothing (default)
portable/install.sh --prepare      # run setup, render config/units (NOT enabled)
portable/install.sh --verify       # ExecStart/WorkingDirectory/required files exist, loopback only, secrets provisioned
AI_STACK_ACTIVATE=1 portable/install.sh --activate --yes   # explicit, future fresh target only
```

- Setup: `none`
- Daemon: docker compose (digest-pinned)
- Port/health: 5678 http://127.0.0.1:5678/healthz
- Secrets the owner must set (never committed): N8N_ENCRYPTION_KEY
- Prefix: $AI_STACK_PREFIX (default ~/.local/share/ai-stack); config: $AI_STACK_CONFIG/n8n (default ~/.config/ai-stack/n8n)

Version provenance: see `component.env`. Upstream/fork HEAD is NOT claimed to be the live installed version unless stated.
Not verified: real runtime start (the build host had no Docker; tests use mocked tools).
- n8n: N8N_ENCRYPTION_KEY must equal the key of any restored n8n data volume.
