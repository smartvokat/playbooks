# Contributing

Please note we have a [code of conduct](./CODE_OF_CONDUCT.md), please follow it in all your interactions with the project.

## General

* Ensure that you update issues and merge requests, which are assigned to you, as often as possible. Those updates are vital for product management to see what is going on.
* Always work in branches, never commit to `main` directly (except merge commits).
* Commit as often as possible, even if it is work-in-progress code. This allows you to go back easily and ensures that you have an emergency backup if something goes wrong.
* Clean up a merge request (via rebase or squash) before notifying the reviewers for the final review.

## Setup

If you have trouble with the setting up, please search the playbooks on our internal wiki and/or contact your project coordinator.

### GPG

Make sure you that you always sign your commits and use the correct signing key in your Git configuration:

```shell
git config commit.gpgSign true
git config user.signingkey "<long fingerprint>"
```

Git can also use the short version, but there is a slight chance of collision, and therefore it is recommended to use the full fingerprint.

## Commits

We use [semantic commit messages][2] to ensure a consistent style. We do this because we generate our changelog automatically from the commit messages, grouped by category. To make automatic grouping possible, you need to add the affected category to your commit message: `fix(example): Something`. Use commas to separate categories when your commit affects more than one category (e.g., `fix(example1,example2): Something`).

The available categories are project-specific.

Use UPPERCASE TYPES, like you would indicate shouting in text messages if you want to put your commit in the public changelog (in contrast to the private, contributor only changelog). Example: `FIX(example): Improve editor performance`.

We provide a set of Git hooks which help to enforce specific rules. See the project-specific CONTRIBUTING.md for more information.

### The seven rules of a great commit message

* Separate subject from body with a blank line
* Limit the subject line to 50 characters (soft requirement)
* Capitalize the subject line
* Do not end the subject line with a period
* Use the imperative mood in the subject line
* Wrap the body at 72 characters (soft requirement)
* Use the body to explain what and why vs. how

### Predefined types

* `chore`: Commits related to project setup, build or continuous integration configuration
* `docs`: Commits related to documentation updates. Also applies if you update the documentation in code (jsdoc, `@doc` etc.)
* `feat`: Commits which add new features
* `fix`: Commits which fix a bug. Please add the issue id in the description if necessary
* `refact`: Commits which improve existing code without changing its functionality
* `test`: Commits which add/remove/improve tests

## Merge requests

We try to avoid to commit to `main` directly and instead follow the [Trunk Based Development](https://trunkbaseddevelopment.com/) model. The `main` (our trunk) is continuously deployed. That means `main` should always be in a functional state. We don't have an (unstable) `develop` branch or individual release branches. Releases are tagged commits with the version number.

All the work should happen in feature branches (our naming strategy is `feat/<issue-id>-<branch>`, `fix/<issue-id>-<name>`, `refact/<issue-id>-<name>`) and get reviewed by other team members. We recommend aiming for short-lived feature branches to avoid merge conflicts. If you are working on a large feature, try to break it up in smaller merge requests and use feature flags in deployment.

[1]: https://medium.com/@maoberlehner/monorepos-in-the-wild-33c6eb246cb9
[2]: https://seesparkbox.com/foundry/semantic_commit_messages
