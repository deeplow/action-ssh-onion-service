# action-ssh-onion-service

GitHub Action to debug via SSH over a Onion Service Tunnel


## Usage

1. Install `tor` on your machine (not Tor Browser)

2. Add step to your CI `.yaml` config:

```yaml
name: CI
on:
  - push
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - uses: deeplow/action-ssh-onion-service@v1
```

Example output:

```
=============================================================
Connect via:
	torsocks ssh runner@zhokiiczwyx7kpaawhiwyxk2mitxs64shfep3xxb4dczubqh6m4vgrqd.onion

(Ignore key verification with: -o UserKnownHostsFile=/dev/null -o StrictHostKeyChecking=accept-new)
=============================================================
```

> **Note**: you need to open the action window as soon as it starts. Otherwise you won't see the connection information.
>
> **Why does this happen?** GitHub "streams" the stdout to the runner page. But you only open the window after 1 min, for example, you'll only see the logs after that. And by then you'll have already missed the connection info.

## Credits

Heavily inspired by https://github.com/valeriangalliat/action-sshd-cloudflared/