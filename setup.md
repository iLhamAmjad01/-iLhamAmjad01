# Setup Guide

## 1. Repository

This content belongs in a repository named exactly `iLhamAmjad01` (matching the GitHub username) so GitHub renders `README.md` on the profile page. File layout:

```
iLhamAmjad01/
├── README.md
├── assets/
│   ├── banner.svg
│   ├── divider.svg
│   ├── footer.svg
│   └── background.svg
├── .github/workflows/
│   ├── snake.yml
│   ├── metrics.yml
│   └── profile-update.yml
└── docs/
    └── setup.md
```

## 2. Required secrets

| Secret | Used by | Notes |
|---|---|---|
| `GITHUB_TOKEN` | `snake.yml` | Provided automatically by GitHub Actions — no setup needed. |
| `METRICS_TOKEN` | `metrics.yml` | A personal access token with `repo` and `read:user` scope. The default `GITHUB_TOKEN` cannot read enough profile-wide data for the metrics plugins used here. Add it under **Settings → Secrets and variables → Actions**. |

## 3. Enabling the workflows

1. Push this repository to GitHub with the structure above.
2. Under **Settings → Actions → General**, set workflow permissions to **Read and write permissions**.
3. Run each workflow once manually from the **Actions** tab (`workflow_dispatch`) to confirm output before waiting on the schedule.
4. `snake.yml` publishes to an `output` branch — the README references `raw.githubusercontent.com/.../output/snake-dark.svg`, which will 404 until that branch exists after the first run.
5. `metrics.yml` writes `metrics.svg` to the repository root, which the README already references.

## 4. Using `background.svg`

GitHub's Markdown renderer does not support CSS backgrounds, so `background.svg` is not embedded directly behind the hero. It exists as a shared brand asset for the two places that do support a true background: the repository's **social preview image** (Settings → General → Social preview) and the hero section of the linked portfolio site, so the profile and the portfolio share one visual system.

---

# Profile Optimization Recommendations

## Bio

> Full stack MERN developer specializing in React.js. Building interfaces, APIs and data models as one system.

Keep the GitHub bio field itself shorter, since it has a strict character limit:

> Full Stack MERN Developer · React.js Specialist

## Profile headline (for LinkedIn / portfolio hero use)

> Full Stack MERN Developer building fast, considered products from database to interface.

## Repository naming convention

- Use lowercase, hyphen-separated names: `mern-auth-system`, `admin-dashboard-react`, `food-trading-platform`.
- Prefix internal tools or forks you don't want surfaced with `sandbox-` or `wip-` so they're easy to exclude from pinned repositories at a glance.
- Avoid version numbers or dates in the repository name itself — track that in releases/tags instead.

## Recommended pinned repositories

Pin exactly six, matching the Featured Projects section so the profile and the pinned grid tell the same story:

1. Professional Portfolio
2. MERN Authentication System
3. Admin Dashboard
4. AI Healthcare Platform
5. React Component Library
6. Food Trading Website

## Repository social preview images

For each pinned repository, add a social preview (Settings → General → Social preview) built from the same palette as this profile — deep near-black background, one accent gradient line, project name in the same typeface used on the banner. Consistency here is what makes the profile and repositories read as one brand rather than a collection of defaults.

## Repository descriptions

Write descriptions as what the project does for a user, not what it's built with:

- Instead of "MERN stack app" → "Role-based admin dashboard for managing orders, inventory and staff accounts."
- Instead of "Auth project" → "JWT-based authentication system with access/refresh token rotation and role-based route protection."

## Repository topics

Apply topics consistently across repositories so they're discoverable and so the profile reads as intentional:

`mern-stack` · `react` · `nodejs` · `express` · `mongodb` · `typescript` · `tailwindcss` · `rest-api` · `jwt-authentication` · `full-stack`

## GitHub organization setup

A personal organization is optional at this stage, but if client work grows, create one (e.g. `ilham-labs`) to host client-facing or collaborative repositories separately from personal experiments, keeping the personal profile focused on flagship work.

## Contribution strategy

- Commit in small, reviewable units rather than large infrequent pushes — this is what the streak and contribution graph on this profile actually reward.
- Reserve at least one weekly slot for maintenance on existing pinned repositories (dependency updates, README accuracy, issue triage) so pinned projects don't go stale.
- Treat the `profile-update.yml` "Current Focus" rotation as a forcing function to actually rotate what you're learning, not just a cosmetic automation.

## Branch naming strategy

- `main` — always deployable.
- `feature/<short-description>` — new functionality, e.g. `feature/order-filtering`.
- `fix/<short-description>` — bug fixes, e.g. `fix/token-refresh-loop`.
- `chore/<short-description>` — tooling, config, dependency work.

## Commit message conventions

Follow Conventional Commits so history stays scannable:

```
feat: add role-based route guards
fix: correct token refresh race condition
refactor: extract validation middleware
docs: update API endpoint reference
chore: bump dependencies
```

## Profile achievements

Aim for achievements that reflect real usage rather than gamed ones: **Pull Shark**, **Quickdraw**, and **YOLO** occur naturally through normal PR-based workflow. Avoid manufacturing throwaway PRs purely to farm badges — the `metrics.yml` achievements plugin will surface these next to real stats, and the gap is visible.

## Open-source contribution strategy

- Contribute fixes to libraries already in use day to day (a Tailwind plugin, a small React utility, an Express middleware) rather than unrelated high-profile repositories — the contribution will be more useful and more sustainable.
- Start with documentation and test coverage gaps in projects you already understand deeply; these are genuinely useful and a realistic entry point.

## Profile SEO / discoverability

- Use the exact terms recruiters search for in the bio and pinned repository descriptions: "Full Stack Developer," "MERN Stack," "React Developer," "REST API."
- Keep the portfolio URL, LinkedIn and email current in the profile `README.md` — these are what convert a profile view into contact.
- Ensure the GitHub account's public email or contact method (Settings → Public profile) is at least one of: profile email, or a clear link to the portfolio's contact section.

## General profile settings

- Set a profile picture that is a clear, professional headshot — avoids the generic-avatar signal recruiters filter on.
- Fill in **Company**, **Location**, and **Website** fields under Settings → Public profile — the location field also affects the metrics timezone setting already configured in `metrics.yml`.
- Keep the repository list free of empty or template-default repositories at the top of the profile's activity — archive or delete anything that doesn't represent current, presentable work.
