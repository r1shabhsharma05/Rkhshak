# Dependency Minimalism — the dependency diet

Every dependency is a liability: code you didn't write, that you must trust, update, and debug. The fewest dependencies that solve the problem is the right number.

## The rules
- **Count them.** List every dependency (direct + transitive) before adding a new one. A project with 500 dependencies has 500 things that can break, go unmaintained, or get compromised. If the number surprises you, that's the finding.
- **Before adding, ask the ladder.** (See `references/ponytail.md` step 4.) Can the stdlib do it? Is it already in the codebase? Is it one line? A dependency for a 10-line function is a bad trade.
- **A dependency must earn its place.** It saves real time, it does something hard (crypto, parsing, dates), or it's the standard for the job. "It's popular" is not a reason. "It might be useful later" is not a reason.
- **One dependency per job.** Two date libraries, two HTTP clients, three state managers — pick one. Duplicates are a sign nobody looked.
- **Prefer small, focused packages.** A 3KB package that does one thing beats a 300KB package that does everything. Check the size before installing (`bundlephobia` / `packagephobia`).
- **Check maintenance before installing.** Recent commits, answered issues, a release in the last year. An unmaintained package is a future vulnerability with no fix coming.
- **Remove what you don't use.** A dependency with no imports is deleted. A dependency used in one place for one trivial thing is replaced with the trivial thing. Audit quarterly: `depcheck` / `npm ls` / manual review.
- **Pin what matters.** The lockfile pins everything. A direct dependency's version range is a deliberate choice, not an accident.

## The cost of a dependency
- **Install time + bundle size.** Every dependency adds to the install, the build, and the bundle the user downloads.
- **Security surface.** Every dependency is code that runs with your app's privileges. A compromised or vulnerable dependency is your vulnerability. (See `supply-chain-sbom.md` in `security-audit`.)
- **Update burden.** Every dependency needs updates. 500 dependencies means 500 update decisions. Fewer dependencies, fewer decisions.
- **Debugging cost.** When something breaks, is it your code or theirs? Fewer dependencies, fewer suspects.

## Audit checks
| # | Check | Fail means |
|---|---|---|
| 1 | Dependency count known (direct + transitive) | Nobody knows how many there are |
| 2 | Every dependency earns its place (saves real time / does something hard) | A dependency for a 10-line job |
| 3 | One dependency per job | Two date libraries, two HTTP clients |
| 4 | Packages are small + maintained | A 300KB package for one function, or unmaintained for a year |
| 5 | No unused dependencies | A dependency with no imports |
| 6 | Quarterly removal audit runs | Dependencies never reviewed after install |
