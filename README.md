# Auggie CLI for Zed

The best software agent, powered by industry-leading context engine, is now available in Zed.

## Choosing a Model

Zed no longer renders a model dropdown for external ACP agents. Zed removed the unstable
ACP model selector in [zed#58308](https://github.com/zed-industries/zed/pull/58308)
(first shipped in Zed v1.6.0), replacing it with ACP session config options. Auggie still
advertises `models` in its `session/new` response, so the picker disappears until Auggie
exposes the model as a session config option. Tracked in CSS-1158.

Until then, set the model outside the picker:

- Set `"model": "<model-id>"` in `~/.augment/settings.json`. This applies to every Auggie
  session, including the one Zed launches through this extension.
- Or define your own agent server in Zed's `settings.json` and pass `-m <model-id>`:

  ```json
  {
    "agent_servers": {
      "Auggie CLI (custom)": {
        "command": "auggie",
        "args": ["--acp", "-m", "<model-id>"]
      }
    }
  }
  ```

  Zed only honors `env` overrides for extension-provided agent servers, so `args` must be
  set on a custom entry.

Run `auggie model list` to see the model IDs available to your account.

## Bumping the Version

```bash
node bump-version.js           # bump to latest npm version
node bump-version.js 0.16.0    # bump to a specific version
```

## Licensing

The code in this repository is licensed under the MIT License. Brand, product, and service names and marks are trademarks of Augment Code and may not be used without explicit permission.
