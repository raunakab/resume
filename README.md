# Resume

My personal resume, written as YAML and rendered to PDF by
[RenderCV](https://docs.rendercv.com), which compiles through
[Typst](https://typst.app).

**[Download the latest PDF →](https://github.com/raunakab/resume/releases/latest)**

## Layout

| Path | What it is |
| --- | --- |
| [`main.yaml`](./main.yaml) | The resume itself — content and theme. The only file worth editing. |
| `rendercv_output/` | Build output: `.pdf`, `.html`, `.md`, `.typ`, and one `.png` per page. Gitignored. |
| [`.github/workflows/release.yml`](./.github/workflows/release.yml) | Renders and publishes a GitHub Release on every merge to `main`. |

## Setup

The only prerequisite is [uv](https://docs.astral.sh/uv). It pins Python 3.13
and installs every dependency, Typst included — there is no separate toolchain
to install.

```sh
uv sync
```

## Rendering

Edit `main.yaml`, then render it one of two ways.

**One-shot.** Compiles once and exits. Use it at the end of an editing session,
or from a script.

```sh
uv run rendercv render main.yaml
open rendercv_output/Raunak_Bhagat_CV.pdf
```

**Watch.** Stays resident and re-renders on every save, so an open PDF viewer
refreshes as you write. `Ctrl-C` to exit.

```sh
uv run rendercv render --watch main.yaml

# then, in a second terminal
open rendercv_output/Raunak_Bhagat_CV.pdf
```

## Releasing

Merging to `main` renders the resume and publishes it as a GitHub Release. No
manual step, no version to bump.

- **Tag** — the UTC date, e.g. `2026.09.06`. A second release on the same day
  becomes `2026.09.06-2`, a third `2026.09.06-3`, and so on.
- **Asset** — `Raunak_Bhagat_CV_<tag>.pdf`.
- **Notes** — generated from the merged pull request.

Merges that touch only prose files skip the workflow; it runs on changes to
`main.yaml`, `pyproject.toml`, or `uv.lock`. To cut a release by hand, dispatch
the workflow from the Actions tab.

## Gotcha: stale page images

`rendercv` writes into `rendercv_output/` without clearing it first, so per-page
`.png` files left over from a longer earlier draft can linger. The PDF is always
rewritten in full, so this only misleads if you are looking at the images. To
start clean:

```sh
rm -rf rendercv_output && uv run rendercv render main.yaml
```

CI is unaffected — every run starts from a fresh checkout.
