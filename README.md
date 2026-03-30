# Disclaimer

This repository is just a clone of the main one hosted in [apify-store/github-actions-source](https://github.com/apify-store/github-actions-source). The purpose of this clone is to allow repositories in `apify-projects` to easily integrate with our E2E Actor platform testing CI/CD pipelines.

See our guide for [E2E Actor platform tests setup](https://www.notion.so/apify/E2E-Actor-platform-tests-setup-332f39950a228038ac41e62eb9d41888?source=copy_link).

---

## Base GitHub Action workflows

These workflows are called by the individual workflows in each repository. They are stored here to avoid code duplication and to make it easier to maintain. Ideally, the individual workflows should only call these base workflows and not contain any logic themselves.

### Caution

These workflows are used based on branch code, there is no deployment. So once you merge the code, it will be running in production.

### Testing

- You can make arbitrary PRs and merges to https://github.com/apify-store/testing-repo-for-github-actions to see how it triggers the workflows. This testing repo has real attached Actors and tests.
- Make sure the shell code actually works as intended on your laptop (sometimes people don't even do that :) ).
- After you merge, observe the workflow on real project before moving on.

### Apify test tools

These workflows depend on https://github.com/apify-projects/apify-test-tools. This includes packages that exposes both CLI used in these workflows and JavaScript library used in each repo to write tests.

### Workflows

- platform-tests - Scheduled (daily, hourly) tests on latest builds
- pr-build-test - On PR updates, builds 0.99 versions and tests on them.
- push-build-latest - This releases master branch to latest Actor version. This almost always happens after PR is merged (since we forbid direct push)

### Possible TODOs

- Install latest apify-test-tools automatically in this workflow
- Merge repo with apify-test-tools
