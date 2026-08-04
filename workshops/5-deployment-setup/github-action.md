# GitHub Actions

Here is a walkthrough of setting up continuous deployment using [`deploy.yml`](./deploy.yml).

## 1. Workflow Name

The `name` property sets the label displayed in the **Actions** tab of your GitHub repository.

```yaml
name: Deploy static content to Pages
```

## 2. Triggers

Specify when your workflow should run. This will deploy whenever there is new code on the `main` branch or when triggered manually.

```yaml
on:
  push:
    branches: ["main"]
  workflow_dispatch:
```

Here is a list of other [Github action triggers](https://docs.github.com/en/actions/reference/workflows-and-actions/events-that-trigger-workflows).

## 3. Permissions

Grant security privileges to the auto-generated `GITHUB_TOKEN` to allow deployment to GitHub Pages.

```yaml
permissions:
  contents: read
  pages: write
  id-token: write
```

## 4. Concurrency

Manage deployment queues to prevent conflicting runs. These are recommended settings for Github Pages.

```yaml
concurrency:
  group: "pages"
  cancel-in-progress: false
```

- `group: "pages"`: Groups deployments under the same queue.
- `cancel-in-progress: false`: Ensures ongoing deployments finish safely without getting cancelled.

## 5. Job Configuration

Configure the runner job.

```yaml
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
```

You can add multiple jobs to the same action if desired.

## 6. Job Execution Steps

Run the sequence of steps to deploy your site.

Steps run sequentially. Refer to [`deploy.yml`](./deploy.yml) to see the full YAML code for all steps.

### Understanding `name` vs `uses` vs `run`

- **name**: An optional, human-readable title for the step that displays in the GitHub Actions progress logs.
- **uses**: Runs a pre-packaged community or official GitHub Action published on GitHub.
- **run**: Runs raw command-line shell commands directly on the runner VM.

### List of Steps

1. **Checkout** – Clones your repository so the runner can access your code
2. **Setup Pages** – Configures GitHub Pages settings and metadata
3. **Setup Node** – Installs and sets up the specified Node.js version
4. **Install Dependencies** to `node_modules` using `npm ci`
5. **Build** – Prepare code for static deployment using `npm run build`
6. **Upload artifact** – Bundles your built `./dist` directory for GitHub Pages
7. **Deploy to GitHub Pages** – Deploys the uploaded artifact to live hosting

## Additional Resources

Here are links to all pre-defined actions if you want to see source code, changelogs, or additional configuration options.

- [actions/checkout](https://github.com/actions/checkout)
- [actions/configure-pages](https://github.com/actions/configure-pages)
- [actions/setup-node](https://github.com/actions/setup-node)
- [actions/upload-pages-artifact](https://github.com/actions/upload-pages-artifact)
- [actions/deploy-pages](https://github.com/actions/deploy-pages)

