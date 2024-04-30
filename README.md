# Resume
My personal resume.

Built using [`RenderCV`](https://sinaatalay.github.io/rendercv).
Internally rendered using `pdflatex` (auto installed alongside `RenderCV`).

# Build Requirements
1. [`python3`](https://www.python.org)
2. [`RenderCV`](https://sinaatalay.github.io/rendercv)
3.
[`cargo`](https://www.rust-lang.org/tools/install) (comes with the `rust` install) + [`cargo-watch`](https://crates.io/crates/cargo-watch).
You could technically use any piece of software that observes a file (or a set of files) and reruns a command when theres a write to it/them.
[`Nodemon`](https://www.npmjs.com/package/nodemon) may potentially fit the bill here; I chose to use `cargo watch` since I already had that installed.

# Build Instructions
Enter a python venv, install the required dependencies, and then run the runner script provided.
The runner script will watch the main YAML file and rebuild everytime it is written to.
```sh
# If you don't have a venv created already
python3 -m venv venv

# If you have a venv created already
# Specific for the fish shell
source venv/bin/activate.fish

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
