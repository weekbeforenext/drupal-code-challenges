# Git Workflow
While this workflow might be overkill for these code challenges, it will help build and demonstrate Git repository management skills.

## New Repository Setup
- [Creating a new repository (GitHub)](https://docs.github.com/en/repositories/creating-and-managing-repositories/creating-a-new-repository)
- [Inviting collaborators to a personal repository (GitHub)](https://docs.github.com/en/account-and-profile/setting-up-and-managing-your-personal-account-on-github/managing-access-to-your-personal-repositories/inviting-collaborators-to-a-personal-repository)
    - This is important if you are working with a mentor or team.
- [Adding locally hosted code to GitHub (GitHub)](https://docs.github.com/en/migrations/importing-source-code/using-the-command-line-to-import-source-code/adding-locally-hosted-code-to-github)

When you initialize a Git repository, the `main` branch is created by default.

Before committing any code, create a new `develop` branch as your working branch. This will make `main` your stable branch.

```
git checkout main
git fetch; git rebase origin/main # Update your main branch with the GitHub version.
git checkout -b develop # Create the new working branch.
git push -u origin develop # Push the branch to GitHub.
```

## Feature Branches
These are branches connected to an issue in the project board.
- [About branches (GitHub)](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-branches)

### Creating a Feature Branch
1. When starting a code issue, use these commands to create an issue feature branch:

    ```
    git checkout develop
    git fetch; git rebase origin/develop # Update your develop branch with the GitHub version.
    git checkout -b feature/<github-username>/<issue-number>--<short-description-of-issue> # Create a new feature branch for your issue.
    ```
1. When changes are ready, use the following command to stage your changes:

    ```
    git add -p # Runs interactive mode with patch subcommands.
    ```
    [Interactive mode with patch subcommands](https://git-scm.com/docs/git-add#Documentation/git-add.txt--p) will allow you to review each change and intentionally stage it with  [patch subcommands](https://git-scm.com/docs/git-add#Documentation/git-add.txt--p).
1. Once everything is staged, run the following command to commit your changes to your feature branch:

    ```
    git commit -m "<issue-number>: <short-description-of-changes>."
    ```
    Including the issue number in your commit comes in really handy when a developer needs to track down why particular changes were made. This is also why issue comments and documentation are important.
1. Now that changes are committed, you can push them to GitHub using this command:

    ```
    git push -u origin <feature-branch>
    ```

## Pull Requests
Pull requests are how you merge your feature branches into the `develop` working branch. It also allows your work to be reviewed by a mentor or team member before it merges.
- [Creating a pull request (GitHub)](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-a-pull-request)

Just be sure to set your "base" to `develop` and "compare" to your feature branch.

## Updating `main` Branch
When your code is stable in the `develop` branch, you can create a Pull Request to merge `develop` into `main` using similar steps as feature branches.

This time, set your "base" to `main` and "compare" to the `develop` branch.
