
# Contributing

We welcome contributions to the Charmed Ingress documentation.

## Prerequisites

- A [GitHub account](https://github.com/signup)
- [Git](https://git-scm.com/) installed locally
- Signed the [Canonical Contributor License Agreement (CLA)](https://ubuntu.com/legal/contributors)

## Set up

Fork and clone the repository:

```bash
git clone https://github.com/canonical/charmed-ingress-documentation.git
cd charmed-ingress-documentation
```

## Make changes

1. Create a branch:

   ```bash
   git checkout -b <branch-name>
   ```

2. Edit the documentation under `docs/`.

3. Build and preview locally:

   ```bash
   cd docs
   make run
   ```

4. Run checks before submitting:

   ```bash
   make spelling
   make linkcheck
   make vale
   make lint-md
   ```

5. Commit, push, and open a pull request on GitHub.

## Report issues

If you find a problem or have a suggestion, [open an issue](https://github.com/canonical/charmed-ingress-documentation/issues).

#### CLA check in CI

When you open a pull request (PR) against the `main` branch, a mandatory automated check verifies that you have signed the CLA. It uses the [canonical/has-signed-canonical-cla](https://github.com/canonical/has-signed-canonical-cla) GitHub Action.

If you haven't signed the CLA:
1. The check will fail with a message indicating the CLA requirement
2. Visit <https://ubuntu.com/legal/contributors> to review and sign the agreement
3. Once signed, re-run the check if you have permissions, or ask a maintainer to do so. Pushing a new commit also triggers re-evaluation.

The CLA check only runs on PRs to `main`. Internal team members working on other branches should ensure they have signed the CLA before their changes are merged to `main`.

### Checks on changes to `docs/` only

- Markdown style check: Runs `pymarkdownlnt` on Markdown files
- Automatic documentation checks: Runs upstream documentation workflow checks.
  The project uses [canonical/documentation-workflows](https://github.com/canonical/documentation-workflows) for automatic documentation checks. To modify this part of CI behavior, pass inputs to upstream workflows rather than creating or customizing local copies.

### Optional checks (allowed to fail)

- Style guide check (`vale`): Checks compliance with the Canonical style guide
- Accessibility check (`pa11y`): Checks accessibility of generated HTML

## Review process

PRs are typically reviewed within a week.

### Responding to feedback

Push additional commits to address feedback (commit locally rather than via GitHub UI to avoid sync conflicts).

Rebase your branch before requesting a review to keep your commits clean. Once review has started, avoid rebasing to maintain the review history and make it easier for reviewers to see what changed.
