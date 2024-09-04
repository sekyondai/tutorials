# PyTorch Tutorials


All the tutorials are now presented as sphinx style documentation at:

## [https://pytorch.org/tutorials](https://pytorch.org/tutorials)

# Asking questions

If you have a question about a tutorial, post in https://dev-discuss.pytorch.org/ rather than creating an issue in this repo. Your question will be answered much faster on the dev-discuss forum.

# Submitting an issue

You can submit the following types of issues:

* Feature request - request a new tutorial to be added. Please explain why this tutorial is needed and how it demonstrates PyTorch value.
* Bug report - report a failure or outdated information in an existing tutorial. When submitting a bug report, please run: `python3 -m torch.utils.collect_env` to get information about your environment and add the output to the bug report.

# Contributing

We use sphinx-gallery's [notebook styled examples](https://sphinx-gallery.github.io/stable/tutorials/index.html) to create the tutorials. Syntax is very simple. In essence, you write a slightly well formatted Python file and it shows up as an HTML page. In addition, a Jupyter notebook is autogenerated and available to run in Google Colab.

Here is how you can create a new tutorial (for a detailed description, see [CONTRIBUTING.md](./CONTRIBUTING.md)):

NOTE: Before submitting a new tutorial, read [PyTorch Tutorial Submission Policy](./tutorial_submission_policy.md).

1. Create a Python file. If you want it executed while inserted into documentation, save the file with the suffix `tutorial` so that the file name is `your_tutorial.py`.
2. Put it in one of the `beginner_source`, `intermediate_source`, `advanced_source` directory based on the level of difficulty. If it is a recipe, add it to `recipes_source`. For tutorials demonstrating unstable prototype features, add to the `prototype_source`.
3. For Tutorials (except if it is a prototype feature), include it in the `toctree` directive and create a `customcarditem` in [index.rst](./index.rst).
4. For Tutorials (except if it is a prototype feature), create a thumbnail in the [index.rst file](https://github.com/pytorch/tutorials/blob/main/index.rst) using a command like `.. customcarditem:: beginner/your_tutorial.html`. For Recipes, create a thumbnail in the [recipes_index.rst](https://github.com/pytorch/tutorials/blob/main/recipes_source/recipes_index.rst)

If you are starting off with a Jupyter notebook, you can use [this script](https://gist.github.com/chsasank/7218ca16f8d022e02a9c0deb94a310fe) to convert the notebook to Python file. After conversion and addition to the project, please make sure that section headings and other things are in logical order.

## Building locally

The tutorial build is very large and requires a GPU. If your machine does not have a GPU device, you can preview your HTML build without actually downloading the data and running the tutorial code:

1. Install required dependencies by running: `pip install -r requirements.txt`.

> Typically, you would run either in `conda` or `virtualenv`. If you want to use `virtualenv`, in the root of the repo, run: `virtualenv venv`, then `source venv/bin/activate`.

- If you have a GPU-powered laptop, you can build using `make docs`. This will download the data, execute the tutorials and build the documentation to `docs/` directory. This might take about 60-120 min for systems with GPUs. If you do not have a GPU installed on your system, then see next step.
- You can skip the computationally intensive graph generation by running `make html-noplot` to build basic html documentation to `_build/html`. This way, you can quickly preview your tutorial.

## Building a single tutorial

You can build a single tutorial by using the `GALLERY_PATTERN` environment variable. For example to run only `neural_style_transfer_tutorial.py`, run:

```
GALLERY_PATTERN="neural_style_transfer_tutorial.py" make html
```
or

```
GALLERY_PATTERN="neural_style_transfer_tutorial.py" sphinx-build . _build
```

The `GALLERY_PATTERN` variable respects regular expressions.


## About contributing to PyTorch Documentation and Tutorials
* You can find information about contributing to PyTorch documentation in the
PyTorch Repo [README.md](https://github.com/pytorch/pytorch/blob/master/README.md) file.
* Additional information can be found in [PyTorch CONTRIBUTING.md](https://github.com/pytorch/pytorch/blob/master/CONTRIBUTING.md).


## License

PyTorch Tutorials is BSD licensed, as found in the LICENSE file.
