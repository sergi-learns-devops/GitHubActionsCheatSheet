# 🚀 GitHub Actions Cheat Sheet 🎉

🌐 **Available in:** [Español](./README.md) | [Català](./README.ca.md)

Welcome to this quick and visual guide to GitHub Actions. Here you'll find key concepts and practical examples to help you create and optimize your own workflows. Perfect to keep handy and consult in your daily work as a developer. 😎

---

## 📁 Basic Workflow Structure

```yaml
name: CI/CD Pipeline

on: [push, pull_request]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v4
      - name: Initial greeting
        run: echo "Hello, world!"
```

---

## 🏁 Most Common Events

- `push` 🚀: Triggers the workflow when you push to a branch.
- `pull_request` 🔀: Runs when a Pull Request is opened or updated.
- `schedule` ⏰: Allows you to schedule automatic tasks (cron jobs).
- `workflow_dispatch` 🖱️: Lets you manually trigger the workflow from the GitHub interface.

---

## 🧩 Most Used Actions

- `actions/checkout@v4`: Clones the repository into the runner.
- `actions/setup-node@v4`: Sets up the Node.js environment.
- `actions/upload-artifact@v4`: Uploads artifacts generated during the workflow.
- `actions/download-artifact@v4`: Downloads artifacts from other jobs.

---

## 🛠️ Variables and Secrets

- `${{ github.ref }}`: Reference to the branch or tag that triggered the workflow.
- `${{ secrets.MY_SECRET }}`: Secure access to secrets defined in the repository.

---

## 🧪 Job Matrices

Run your workflow in different versions or platforms in parallel:

```yaml
strategy:
  matrix:
    node-version: [14, 16, 18]
```

---

## 🔄 Workflow Reuse

You can reuse workflows with `workflow_call` to keep your configuration DRY:

```yaml
on:
  workflow_call:
    inputs:
      name:
        required: true
        type: string
```

---

## 📝 Example Job with Common Steps

```yaml
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Install dependencies
        run: npm install
      - name: Run tests
        run: npm test
```

---

## 🧙‍♂️ Practical Tips

- Use `needs:` to define dependencies between jobs and control execution flow.
- Use the `if:` condition to run steps or jobs only under certain circumstances.
- Artifacts are useful for sharing files between jobs or stages.
- Always manage your secrets from the GitHub settings, never commit them to the repository.

---

## 🌟 Best Practices for Creating Workflows

- **Divide and conquer:** Separate workflows by purpose (deploy, test, lint, etc.) for easier maintenance.
- **Use descriptive names for jobs and steps:** Makes it easier to understand what each part of the workflow does.
- **Reuse code:** Use reusable actions and workflows to avoid duplication.
- **Keep your workflows updated:** Regularly check for updates to the actions you use.
- **Leverage matrices:** Use them to test your code in different environments or dependency versions.
- **Document your workflows:** Add helpful comments for other developers (or for your future self!).

---

## 🔒 Security Best Practices in GitHub Actions

- **Use only trusted actions:** Prefer official actions or review the code of third-party actions before using them.
- **Pin specific versions:** Use version tags (`@v4.0.0`) instead of `@master` or `@main` to avoid unexpected changes.
- **Minimize permissions:** Set workflow and token (`GITHUB_TOKEN`) permissions to the minimum required.
- **Never expose secrets:** Never use `echo` to print secrets or sensitive variables in logs.
- **Review artifacts:** Do not download or execute artifacts from untrusted sources.
- **Disable unnecessary workflows:** If a workflow is no longer used, remove or disable it.

---

## 📚 Useful Links and Official Documentation

- [Official GitHub Actions Documentation](https://docs.github.com/en/actions)
- [GitHub Actions Quickstart Guide](https://docs.github.com/en/actions/quickstart)
- [GitHub Actions Marketplace](https://github.com/marketplace?type=actions)
- [Workflow Expressions and Syntax](https://docs.github.com/en/actions/learn-github-actions/expressions)
- [GitHub Actions Security](https://docs.github.com/en/actions/security-guides/security-hardening-for-github-actions)

---

This Cheat Sheet is designed as a quick reference. If you need to dive deeper, check out the links above for the latest and most complete information on GitHub Actions. 