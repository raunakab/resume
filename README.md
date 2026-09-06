# Resume

My personal resume.
Written as YAML and rendered to PDF by [`rendercv`](https://docs.rendercv.com).
You can download the latest version by visiting the [**releases tab**](https://github.com/raunakab/resume/releases/latest).

## Setup

Install [`uv`](https://docs.astral.sh/uv). Then, run `uv sync` to download the dependencies.

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

## Release Process

Merging to `main` renders the resume and publishes it as a GitHub Release.
No manual step, no version to bump.

Tags are the UTC date, e.g. `2026.09.06`; a second release on the same day
becomes `2026.09.06-2`, a third `2026.09.06-3`. The attached asset is
`raunak-bhagat-<mm>-<dd>-<yyyy>.pdf`.

Only changes to `main.yaml`, `pyproject.toml`, or `uv.lock` trigger a release,
so prose-only merges skip it. To cut one by hand, dispatch the workflow from
the Actions tab.

## Notes

`rendercv` writes into `rendercv_output/` without clearing it first, so per-page
`.png` files left over from a longer earlier draft can linger. The PDF is always
rewritten in full, so this only misleads if you are looking at the images. To
start clean:

```sh
rm -rf rendercv_output && uv run rendercv render main.yaml
```

CI is unaffected — every run starts from a fresh checkout.
