# workflows

GitHub Actions workflows shared by the Fusani-Applications and lokisapocalypse repos. Each repo keeps a short
workflow that calls the shared one, so a fix made here reaches every repo at once.

This repo is public because a reusable workflow in a private repo can't be called from another account's repos.
Nothing secret lives here: callers pass their own secrets in.

## Add issues to project boards

[`add-issues-to-boards.yml`](.github/workflows/add-issues-to-boards.yml) puts each new issue on the project
boards in Backlog and sets its Client field. Its header explains which boards and how the client is picked.

Every repo has the same caller at `.github/workflows/add-issues-to-boards.yml`, plus an `ADD_TO_PROJECT_PAT`
secret. `scripts/add-board-workflow.sh` in
[operations](https://github.com/Fusani-Applications/operations) copies the caller to a repo and sets the
secret.

Callers use `@development`, so a change merged here applies to the next issue opened anywhere. Test a change
before merging by pointing one repo's caller at the branch and running it by hand from that repo's Actions tab,
with the number of an issue that's already in Backlog (it sets Status back to Backlog).

Issues are turned off here; track work on this repo in operations.
