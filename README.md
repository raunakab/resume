# Resume

My personal resume.
Built using [`RenderCV`](https://sinaatalay.github.io/rendercv) (which internally uses [`typst`](https://typst.app) for rendering).

## Prerequisites

1. [`uv`](https://docs.astral.sh/uv)

## Setup

```sh
# create a virtual env and install all the required dependencies
uv sync
```

## Rendering

Edit [`main.yaml`](./main.yaml), then render it in one of two ways.

### One-shot

Renders once and exits. Use this when you want to compile at the end of an editing session, and in any script or CI job.

```sh
uv run rendercv render main.yaml

open rendercv_output/Raunak_Bhagat_CV.pdf
```

### Watch mode

Stays resident and re-renders on every save, so the pdf refreshes as you write. Exit with `Ctrl-C`.

```sh
uv run rendercv render --watch main.yaml

# in a new terminal, open the generated pdf file
open rendercv_output/Raunak_Bhagat_CV.pdf
```

## Notes

`rendercv` writes into `rendercv_output/` without clearing it first, so per-page `.png` files from an older, longer draft can linger. The pdf itself is always rewritten in full, and the directory is gitignored. To start clean:

```sh
rm -rf rendercv_output && uv run rendercv render main.yaml
```
