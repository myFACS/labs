# labs
A sandbox repository for experiments, testing, and proof-of-concept implementations.

## Workflows

### Test SSH Key (`.github/workflows/test-ssh-key.yml`)

Prints `KEY_NAME` (environment variable or secret) and identifies the `SSH_KEY` secret configured for a GitHub environment:

- `KEY_NAME` as a variable is printed in plain text; as a secret it is masked (`***`) by GitHub.
- `SSH_KEY` (private key) is never written to the log; its length, derived public key and fingerprint are printed instead, so you can identify which key is configured without leaking it.
- Missing values are reported as warnings.

**Run manually on a branch:** *Actions → Test SSH Key → Run workflow*, pick the branch and the environment.

**Reuse from another workflow:**

```yaml
jobs:
  test-ssh-key:
    uses: myFACS/labs/.github/workflows/test-ssh-key.yml@main
    with:
      environment: production
```

Environment secrets and variables are read directly by the reusable workflow, so they don't need to be passed by the caller.
