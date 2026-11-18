# Deploy Authorization — build and deploy are separate approvals

Building something and publishing it are two different acts with two different approvals. This file is the rule for the deploy gate (see `references/audit-gate.md`): even a fully built, fully passing change is not live until the deploy approval exists.

## The rule

- Build the site or app and show it first when the user asked for a build.
- Treat words such as build, make, or create as a **build request only**. They are not deploy words.
- Wait for an **explicit deploy word** before publishing anything to a public host.
- Name the host and the public address in the deploy question when asking for that word.
- Stop when the user has not given that word, and report the build as ready to show, not as live.

## Publish only on the explicit word

- Publish to the named host only after the user gives the explicit deploy word.
- Keep the deployment private or protected when the host offers that option and the user did not ask for public access.
- Verify the live address yourself before reporting the deployment as live.
- Report the exact public address and what was verified on it. Never report a local build as deployed.

## Undo a public deployment the user did not authorize

- Remove public access at once when the user says a deployment was not authorized.
- Tell the user plainly that the deployment was made without authorization and what was removed.
- Record the dashboard step the user must take when full project deletion needs the user, and name that step exactly.
- Keep the local build files until the user decides whether to keep or delete them, unless the user tells you to delete them.

## Alternatives while waiting for the word

- Offer a local preview link or a screenshot of the build when the user wants to see it before any public deployment.
- Offer a password-protected preview when the user wants to share a build without making it public.
- Ask the user to pick the host when more than one public host could serve the build.

## How this maps to the 85 checks

The deploy gate in `references/audit-gate.md` is about *whether the code is safe to ship*. This file is about *whether shipping was authorized at all*. Both must pass: an unauthorized deploy of secure code is still a gate failure, and an authorized deploy of failing code is still blocked.
