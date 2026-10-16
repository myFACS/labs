# labs
A sandbox repository for experiments, testing, and proof-of-concept implementations.

## Workflows

### Test SSH Key (`.github/workflows/test-environment.yml`)

Verify the presence of environment variables or secrets

- `KEY_NAME` - `SSH_KEY` (secrets) and `KEY_NAME` (variables)

**Run manually on a branch:** *Actions → Test SSH Key → Run workflow*, pick the branch and the environment.

**Reuse from another workflow:**

```yaml
jobs:
  test-ssh-key:
    uses: myFACS/labs/.github/workflows/test-environment.yml@main
    with:
      environment: production
```

Environment secrets and variables are read directly by the reusable workflow, so they don't need to be passed by the caller.
