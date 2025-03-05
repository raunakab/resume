# Resume

My personal resume.
Built using [`RenderCV`](https://sinaatalay.github.io/rendercv) (which internally uses `pdflatex` for rendering).

# Build Requirements

1. [`uv`](https://docs.astral.sh/uv)
2. [`RenderCV`](https://sinaatalay.github.io/rendercv)

# Build Instructions

```sh
# create a virtual env and install all the required dependencies
uv v
source .venv/bin/activate.fish
uv pip install -r requirements.txt

# render
rendercv render --watch raunakbhagat_CV.yaml

# in a new terminal, open the generated pdf file
open rendercv_output/Raunak_Bhagat_CV.pdf
```

Since we ran `rendercv` with the `--watch`, the pdf should refresh everytime you write to the main yaml file.
