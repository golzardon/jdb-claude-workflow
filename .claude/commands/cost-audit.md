# Cost Audit — Infrastructure Cost Analysis

Analyze the project's infrastructure and third-party services to estimate costs and identify optimizations.

## Steps

1. **Scan for infrastructure configuration files:**
   - Docker: `Dockerfile`, `docker-compose.yml`, `docker-compose.*.yml`
   - Cloud platforms: `vercel.json`, `netlify.toml`, `fly.toml`, `render.yaml`, `railway.json`, `app.yaml` (GCP), `appspec.yml` (AWS)
   - IaC: `terraform/`, `*.tf`, `serverless.yml`, `cdk.json`, `pulumi.*`, `cloudformation.yml`
   - CI/CD: `.github/workflows/`, `.gitlab-ci.yml`, `Jenkinsfile`, `.circleci/`
   - Record each config found.

2. **Scan for third-party service integrations:**
   - Check source code imports and configuration for:
     - Payment processors (Stripe, PayPal, Square, etc.)
     - Email services (SendGrid, Mailgun, SES, Resend, Postmark)
     - Storage (S3, GCS, Cloudinary, Uploadthing)
     - Databases (managed Postgres, MongoDB Atlas, PlanetScale, Supabase, Firebase)
     - Auth services (Auth0, Clerk, Supabase Auth, Firebase Auth)
     - Monitoring (Sentry, Datadog, LogRocket, New Relic)
     - Search (Algolia, Elasticsearch, Typesense)
     - CDN and media (Cloudflare, imgix, Mux)
     - AI/ML APIs (OpenAI, Anthropic, Replicate)
   - Check environment variable files (`.env.example`, `.env.local.example`, `.env.sample`) for service keys.
   - Check dependency files for SDK packages that imply service usage.

3. **For each identified service, estimate costs:**
   - Categorize as: free tier, pay-as-you-go, or fixed subscription.
   - Provide rough monthly cost range (low / typical / high) based on common usage patterns.
   - Note the free tier limits if applicable.
   - Flag services that could become expensive at scale.

4. **Identify optimization opportunities:**
   - Services that overlap in functionality (e.g., two monitoring tools).
   - Services on paid tiers that could use free alternatives.
   - Infrastructure that appears over-provisioned for the project's likely scale.
   - Missing caching or CDN that could reduce compute/bandwidth costs.
   - CI/CD minutes or build time that could be optimized.

5. **Produce a cost summary table:**
   ```
   | Service        | Category    | Est. Monthly Cost | Notes              |
   |----------------|-------------|-------------------|--------------------|
   | Vercel         | Hosting     | $0 - $20          | Free tier likely   |
   | Supabase       | Database    | $0 - $25          | Free tier to Pro   |
   | ...            | ...         | ...               | ...                |
   | **Total**      |             | **$X - $Y**       |                    |
   ```

6. **Save the audit:**
   - Create `.agents/maintenance/` directory if it does not exist.
   - Save to `.agents/maintenance/cost-audit-YYYY-MM-DD.md`.

7. **Print summary:**
   - Total estimated monthly cost range.
   - Top 3 cost optimization suggestions.
   - Disclaimer: "These are rough estimates based on code analysis. Verify against actual billing dashboards."

## Notes
- Do not access any live APIs or billing dashboards. All analysis is based on code and configuration files.
- If the project has no detectable infrastructure (e.g., a library or CLI tool), say so and suggest this command is not applicable.
- Cost estimates should reflect 2025-2026 typical pricing. Acknowledge that pricing changes.
- Be conservative in estimates. It is better to overestimate than to underestimate.
