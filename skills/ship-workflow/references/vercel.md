# Vercel — optimise cost and performance, keep previews honest

Distilled from two sources, in our own words: vercel-optimize (MIT) and vercel_preview_env_parity. Full pipelines live in those sources. Use for cost and performance optimisation on deployed projects (especially Next.js, SvelteKit, Nuxt, and limited Astro apps), or when a Preview deployment fails while Production works.

## The optimisation pipeline
1. **Collect, scan, and merge signals.** Gather the deployment's metrics, usage, project config, and code signals into one run directory. Stop on blockers: a blocker (a broken deploy, a missing credential) ends the run — optimisation on a broken deployment is noise.
2. **Gate candidates.** Ask about audit scope when needed; deep-dive and reconcile each candidate against the evidence; generate briefs and investigate.
3. **Verify recommendations.** Every recommendation is verified against the live deployment or a reproduction — an unverified recommendation is not shipped.
4. **Render the report.** The report states the recommendation, the evidence, the expected effect, and the verification — and the final message says the same, briefly.

## Recommendation rules
- Optimise what the measurements name, not what the checklist guesses.
- A recommendation that costs more than it saves is not a recommendation.
- Cache semantics are version- and framework-specific: check the current docs for the framework version in use before advising on revalidation, ISR, or route caching.
- Function cost follows invocations, duration, and region: reduce invocations first, then duration, then question the region.

## Scanner rules
Scan for the known waste patterns: uncached dynamic routes that could be static, oversized images without optimisation, third-party scripts blocking load, middleware running on every request, and cold starts from heavy initialisation. Each finding names the file and the measurement, not just the pattern.

## Preview environment parity — when Preview fails and Production works
- **Recognise a Preview-only failure.** Treat it as an environment-scope suspect when Production works and the backend returns 200. Read the exact Preview error before changing code; separate a missing API address from a backend outage. Check the frontend call target first when the Preview page loads but its API calls fail.
- **Check the environment scope.** List the project environment variables and read the scope shown for each. A variable set only for Production is absent in Preview, even when Production works. Check every variable the frontend build reads — including the API base URL and public keys — not only the one named in the error. Remember that build-time variables are baked into the build: saving a variable alone does not fix a deployed Preview build.
- **Set the variable and redeploy.** Set the missing variable for Preview with the same value Production uses (or a different value when Preview should call a separate backend). Ask the user for a secret value through the secure entry flow; never write a secret into a skill, a memory file, or a repo file. Redeploy the Preview deployment after changing a build-time variable and wait for it to reach ready.
- **Verify the Preview flow end to end.** Open the new Preview URL and run the exact flow that failed. Confirm the API call reaches the backend and returns a real response; record the deployment URL and the flow result together. Check the Preview origin in the backend CORS allowlist when the scope is correct and calls still fail. Report the Preview deployment as fixed only after the live Preview flow passes — never report a saved variable as a fix on its own.
