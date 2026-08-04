# Custom Providers

While [GitHub Pages](https://docs.github.com/en/pages) is great for static websites, you may want to deploy your web application to providers like [Cloudflare Workers](https://workers.cloudflare.com/), [Vercel](https://vercel.com/), or [Netlify](https://www.netlify.com/)

This is especially if you want to take advantage of [Astro Endpoints](https://docs.astro.build/en/guides/endpoints/) for server-side logic and API routes.

## How to Migrate from Github Pages

You can still use GitHub Actions for all of these platforms by replacing the platform-specific deployment steps with the provider's CLI tools and authentication tokens.

1. Remove Github Pages workflow steps
2. Add necessary environment variables
3. Add deploy steps using provider's CLI tools

## Environment Variables

Define Github Action environment variables by going to **GitHub Repository Secrets** (**Settings** > **Secrets and variables** > **Actions**).

Here is an example step using `npx wrangler deploy` with variables to publish to Cloudflare Workers:

```yaml
- name: Deploy
  run: npx wrangler deploy
  env:
    # Wrangler looks for these exact names by default
    CLOUDFLARE_API_TOKEN: ${{ secrets.CLOUDFLARE_WORKERS_API_TOKEN }}
    CLOUDFLARE_ACCOUNT_ID: ${{ secrets.CLOUDFLARE_ACCOUNT_ID }}
```

### How `env` Works

The `env` block injects environment variables into the step's shell environment. CLI tools like Wrangler read environment variables automatically during execution to authenticate without needing hardcoded keys or command-line flags. Using `${{ secrets.YOUR_SECRET_NAME }}` securely pulls the secret from your repository settings at runtime.

## Additional Resources

- Cloudflare [deployment docs](https://developers.cloudflare.com/workers/) & [Astro adapter](https://docs.astro.build/en/guides/integrations-guide/cloudflare/)
- Vercel [deployment docs](https://vercel.com/docs) & [Astro adapter](https://docs.astro.build/en/guides/integrations-guide/vercel/)
- Netlify [deployment docs](https://docs.netlify.com/) & [Astro adapter](https://docs.astro.build/en/guides/integrations-guide/netlify/)

For complete example workflow files for each provider, check out [these sample workflows](https://github.com/alexanderdombroski/resume-project/tree/main/.github/workflows).
