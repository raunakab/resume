# Resume
My personal resume.

Built using [`RenderCV`](https://sinaatalay.github.io/rendercv).
Internally rendered using `pdflatex` (auto installed alongside `RenderCV`).

# Build Requirements
1. [`python3`](https://www.python.org)
2. [`RenderCV`](https://sinaatalay.github.io/rendercv)
3. [`cargo`](https://www.rust-lang.org/tools/install) (comes with the `rust` install)
4. [`cargo-watch`](https://crates.io/crates/cargo-watch)

# Build Instructions
Enter a python venv, install the required dependencies, and then run the runner script provided.
The runner script will watch the main YAML file and rebuild everytime it is written to.
```sh
python3 -m venv venv
pip3 install -r requirements.txt
./run.sh
```

In a new terminal, open the rendered output.
The PDF should refresh everytime you write to the main YAML file.
```sh
open rendercv_output/${NAME}_CV.pdf
```
where the `${NAME}` variable is whatever the `cv.name` value inside of the main YAML file is.
Usually, there should only ever be a single PDF file in the `rendercv_output` directory, so opening whatever file in that directory that ends with the `pdf` extension should suffice.
