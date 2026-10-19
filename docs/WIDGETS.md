# Profile activity

## Saved metric cards

The profile shows a compact, transparent activity summary in two theme variants:

- `assets/generated/activity.svg`: dark numbers and gray labels for light mode.
- `assets/generated/activity-dark.svg`: light numbers and gray labels for dark mode.

Each canvas is 280×112 pixels with four metrics in a two-by-two layout: Stars,
Commits · last year, PRs and Issues. Numbers are 22px and labels 12px at the native
280px display width, so narrow screens do not need to squeeze four columns into
one line. There is no visible title, rank, background, frame, icon or animation.
Accessible title and description elements identify the data without visual clutter.

The publisher derives both variants from these retained upstream SVGs:

- `assets/generated/stats.svg`: public GitHub activity and repository statistics.
- `assets/generated/languages.svg`: language distribution in public repositories,
  excluding this profile repository. Language proportions describe repository
  source data, not skill level or time spent.

Only the compact activity summary is intended for the README. It reads the
theme variants from this repository. Opening the profile does not
call a public statistics-rendering service. The cards refresh through
[profile-cards.yml](../.github/workflows/profile-cards.yml) once a night at 02:23
UTC, or manually through **Actions > Refresh public profile cards > Run workflow**.
Scheduled runs can be delayed or disabled by GitHub; the last successful SVGs stay
visible. The [initial generation and publication](https://github.com/antropos17/antropos17/actions/runs/39186101345)
completed successfully on 2026-10-19. That run predates the compact summary;
its new parser and hosted publication require their own successful workflow run.

Use a native picture element at the SVG's native width; GitHub constrains an image
to its available content width. The dark source follows the viewer's color-scheme
preference and the light asset is the fallback:

```html
<picture>
  <source
    media="(prefers-color-scheme: dark)"
    srcset="assets/generated/activity-dark.svg"
  />
  <img
    src="assets/generated/activity.svg"
    width="280"
    alt="Public GitHub activity: stars, commits in the last year, pull requests and issues"
  />
</picture>
```

## Data, access and failure behavior

Generation uses the built-in, short-lived `GITHUB_TOKEN` with `contents: read`.
There is no personal access token, private-repository permission, enabled
private-count option or external service account. The stats card explicitly disables
`count_private` and `include_all_commits`: commit statistics use the renderer's
default recent-year window instead of claiming an all-time total. Public data
visibility and API accounting still follow GitHub and the upstream renderer.

The generator job cannot push. A separate publisher job gets `contents: write`,
checks out the current `main`, validates exactly two input SVGs, derives two
activity variants and stages only these four asset paths. Checkout does not persist credentials; Git receives the
publisher token through a temporary askpass helper that is removed on exit. No
force push is used, so a concurrent branch update makes publication fail safely.
There are no push, pull-request, deployment or automatic-merge triggers.

The parser requires exactly one SVG text node with each known `data-testid`:
`stars`, `commits`, `prs` and `issues`. Missing, duplicate or invalid numeric
values stop publication. Compact upstream formatting such as `3.1k` is preserved;
the summary does not reconstruct or invent an exact count from a rounded number.
The two theme variants contain only generated text, with no copied upstream
markup. Input validation rejects active SVG content and external element links.

The action fails on data-fetch errors rather than publishing an error card.
Failed generation skips publication and preserves the previous good assets. Both
jobs have time limits; their transfer artifact expires after one day. A real
workflow run must confirm API access and renderer behavior. If GitHub policy or
branch protection prevents the bot push, the run fails; this workflow does not
change repository settings or bypass protection.

## Upstream and pins

[GitHub Readme Stats recommends generating static assets with Actions](https://github.com/anuraghazra/github-readme-stats#github-actions).
Its current linked action is
[stats-organization/github-readme-stats-action](https://github.com/stats-organization/github-readme-stats-action),
under the MIT license. The workflow pins:

| Component         | Immutable revision                         |
| ----------------- | ------------------------------------------ |
| Stats action      | `2c498845f71017821efaad14293ebc736156ef21` |
| Checkout          | `d23441a48e516b6c34aea4fa41551a30e30af803` |
| Artifact upload   | `cf430e030ddbb5b0abf93d22962f4752f3646cd9` |
| Artifact download | `9000827ccba6bdab643e8b6fd33ac0654aef8333` |

The stats renderer is explicitly set to npm package
`@stats-organization/github-readme-stats-core@2.2.0`; its mutable default `v2` is
not used. The action installs that exact core version with npm and disabled
install scripts. Its runtime dependency resolution is upstream npm behavior,
not a claim of fully hermetic builds. Its own setup-node/pnpm actions are pinned
by upstream SHA and its initial production install uses the upstream lockfile.

The displayed summary uses numbers `1f2328` and labels `59636e` in light mode;
numbers `f0f6fc` and labels `9198a1` in dark mode. The upstream cards remain source
artifacts, including their own visual styling; their rank and chart markup do not
enter the compact summary.

Standard GitHub-hosted Ubuntu runner minutes are free for this public repository
under [GitHub's current billing rules](https://docs.github.com/en/billing/concepts/product-billing/github-actions).
Artifact storage remains subject to the account's allowance; the transfer is
limited to these two small SVGs and one day's retention. No paid runner, hosting
service, billing setting or credential is provisioned by this workflow.
