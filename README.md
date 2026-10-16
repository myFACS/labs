# labs
A sandbox repository for experiments, testing, and proof-of-concept implementations.

## Workflows

### Test SSH Key (`.github/workflows/test-ssh-key.yml`)

Validates the `SSH_KEY` secret and `KEY_NAME` (environment variable or secret) configured for a GitHub environment:

1. Checks that `SSH_KEY` and `KEY_NAME` are set (and that `KEY_NAME` is a valid file name).
2. Checks that `SSH_KEY` is a valid, passphrase-less private key and outputs its fingerprint.
3. Optionally tests SSH authentication against a host (default `git@github.com`).

**Run manually on a branch:** *Actions → Test SSH Key → Run workflow*, pick the branch and the environment.

**Reuse from another workflow:**

```yaml
jobs:
  test-ssh-key:
    uses: myFACS/labs/.github/workflows/test-ssh-key.yml@main
    with:
      environment: production
      # ssh_host: github.com
      # ssh_user: git
      # test_connection: true
```

Environment secrets and variables are read directly by the reusable workflow, so they don't need to be passed by the caller.
