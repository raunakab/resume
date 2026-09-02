# Resume

My personal resume.
Built using [`RenderCV`](https://sinaatalay.github.io/rendercv) (which internally uses [`typst`](https://typst.app) for rendering).

## Prerequisites

1. [`uv`](https://docs.astral.sh/uv)

## Instructions

```sh
# create a virtual env and install all the required dependencies
uv sync

# render
uv run rendercv render --watch main.yaml

# in a new terminal, open the generated pdf file
open rendercv_output/Raunak_Bhagat_CV.pdf
```

Since we ran `rendercv` with the `--watch`, the pdf should refresh everytime you write to the main yaml file.
