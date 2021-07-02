# Edge Workflows

This project warehouses the GitHub Workflows used by Edge as well as instructions to add the workflows to a repo.

## Installation

Run this command in your project directory:

```sh
curl -s https://raw.githubusercontent.com/EdgeApp/edge-workflows/main/scripts/install | bash
```

This will add a `.github/workflows/` directory which should be tracked in your SCM. This command can also be used to update the workflow.

## Upgrading

To upgrade a repository's `.github/workflow` with the latest edition of the workflows, simply run the install command and commit the changes. 
Workflow upgrade commits don't require a pull request or review and can be aded on the main (master) branch directly.

## [PR Checks](./.github/workflows/pr-checks.yml)

Runs when creating or updating pull requests. It currently contains the [block-wip-pr-action](https://github.com/samholmes/block-wip-pr-action) which prevents PRs which have fixup/squash commits or merge commits from being merged into the main branch.

## [PR Rebase](./.github/workflows/pr-checks.yml)

Runs when creating a pull request comment containing the textual command `/rebase` or `/autosquash`. It uses the [cirrus-actions/rebase](https://github.com/samholmes/rebase) action to rebase the PR onto the base branch if possible (no conflicts). When using `/autosquash` or `/rebase-autosquash`, it will rebase using the `--autosquash` flag.
