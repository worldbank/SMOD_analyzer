# SMOD Analyzer

[![CalVer](https://img.shields.io/badge/calver-YY.0M.MICRO-22bfda.svg)](https://calver.org)
[![GitHub Release](https://img.shields.io/github/v/release/worldbank/template)](https://github.com/worldbank/template/releases)
[![pre-commit.ci status](https://results.pre-commit.ci/badge/github/worldbank/template/main.svg)](https://results.pre-commit.ci/latest/github/worldbank/template/main)

## Introduction
[GHS-SMOD (Global Human Settlement Layer – Settlement Model Layer)](https://human-settlement.emergency.copernicus.eu/download.php?ds=smod) provides valuable information on urbanization processes. The SMOD raster dataset, covering the period from 1975 to 2030 in 5-year intervals, offers estimated land use classifications for each 1 km × 1 km grid cell globally.

```{margin} ✨ For the details of GHS-SMOD
Read this [GHS-official technical document](https://github.com/worldbank/SMOD_analyzer/blob/main/docs/GHSL_Data_Package_2023.pdf) (pp.50-62) for more details.
```


However, extracting the classified pixel information (such as Urban Center, Suburban, and Rural Cluster) from the SMOD dataset into the Areas of Interest (AOIs) for your project is not straightforward.

[SMOD Analyzer](https://github.com/worldbank/SMOD_analyzer/blob/main/notebooks/SMOD_analyzer.ipynb), a [Google-Colab-based Jupyter Notebook](https://colab.google/), provides an interactive interface to support this workflow. It enables national- and subnational-level data extraction by default with inline-visualization.

With the most minimal set-up, you only need to specify the ISO code of your target country. The notebook will then automatically generate: (1) National-level changes in urban and suburban–rural pixels over a 55-year period, and (2) Subnational-level (i.e., ADM-2 level) aggregations of each SMOD class for each subnational area and year, exported as an ESRI Shapefile—which is readily visualized on any GIS platform and can also be integrated with other related GIS datasets.

For those with knowledge of GIS and Python, this notebook serves as a good foundation for customizing workflows—for example, conducting SMOD analyses on user-defined AOIs such as specific urban areas.

## Usage

### Getting Started
#### 1. **Prepare your Google Colab account**
As this notebook is optimized for the Google Colab (hereafter, Colab) environment, you must first create a Google account (if you don’t already have one) and access your [Google Drive](https://drive.google.com/drive/my-drive).
If you have previously used Colab, you likely already have a “Colab Notebooks” directory. If not, please create one.

#### 2. **Download all SMOD-analyzer resources**
The must-haves for this notebook are:
- [SMOD_analyzer.ipynb](https://github.com/worldbank/SMOD_analyzer/blob/main/notebooks/SMOD_analyzer.ipynb)
- Global ADM2 Boundary Shapefile (Preferably the latest World Bank Official ADM2 Shapefile (Not Public, Internal-use Only). Alternatively, [World Health Organization ADM2](https://gis-who.hub.arcgis.com/pages/detailedboundary) (Publicly Available - You can find it [here]() as well))
- [tools.py](https://github.com/worldbank/SMOD_analyzer/blob/main/src/tools.py)
- [underlying SMOD dataset](https://github.com/worldbank/SMOD_analyzer/tree/main/data/smod_raw)


Store these resources in a new directory (for example, 'Analyzing GHS-SMOD') following the directory structure below:
```
Analyzing GHS-SMOM/
│
├── data/
│   │
│   ├── shps/
│   │   ├──WHO_adm2/ (or WB official ADM2)
│   │   │   └──GLOBAL_ADM2.shp
│   │   └──Other AOI shapefile, if applicable
│   │
│   └── smod_row/
│       └──smod_1975.tif
│       └──smod_1980.tif
│       └── ...
│       └──smod_2030.tif
│
├── output/
│   └── Empty: Products will be stored here
│
├── SMOD_analyzer.ipynb
└── tools.py
```


#### 2. **Enable [GitHub Actions](https://github.com/features/actions) and [GitHub Pages](https://pages.github.com)**

After creating the repository from the <span style="color:#3EACAD">template</span>, you will have to enable [GitHub Actions](https://github.com/features/actions) and [GitHub Pages](https://pages.github.com) to allow the [Jupyter Book](https://jupyterbook.org) to be built and published.

To activate the workflow, please enable [GitHub Actions](https://github.com/features/actions) by going to the repository's settings (`Settings > Actions > General`), and selecting **read and write permissions** as shown below.

```{figure} docs/images/github-template-action-enable.png
    ---
    ---
```

To publish, please enable [GitHub Pages](https://pages.github.com) by going to the repository's settings (`Settings > Pages`), and selecting to deploy from the **GitHub Actions** option.

```{figure} docs/images/github-template-pages.png
---
---
```

On the next push to `main`, the [Jupyter Book](https://jupyterbook.org) will be automatically built and published. You can check the progress on the `Actions` tab.

```{figure} docs/images/github-template-action.png
---
---
```

```{caution}
The *documentation* can be published from either *public* and *private* repositories. If publishing private content, please remember to carefully select the content to be made public and to abide by your organization's Data Privacy Policy.
```

#### 3. **Update configurations**

The <span style="color:#3EACAD">template</span> comes with a default `docs/_config.yml` Jupyter Book configuration file. Remember to update it to reflect your project's name and details.

```yaml
repository:
url: https://github.com/worldbank/template
branch: main
```

```{seealso}
[Jupyter Book Configuration Reference](https://jupyterbook.org/en/stable/customize/config.html)
```

#### 4. **Review and update README files**

The <span style="color:#3EACAD">template</span> comes with README files - including [this **README**](README) - that should provide anyone with the information about the first steps to use, learn and contribute to your project. Please **replace** and/or **repurpose** the files with instructions and detailed information about your project.

> - **CODE_OF_CONDUCT**
> - **CONTRIBUTING**
> - **README**
> - Issues and Pull Requests GitHub templates

```{seealso}
[Awesome README](https://github.com/matiassingers/awesome-readme)
```

#### 5. **Choose a license**

The <span style="color:#3EACAD">template</span> is licensed under the [**Mozilla Public License**](https://www.mozilla.org/en-US/MPL). A LICENSE is the document that guarantees the repository can be shared, modified and receive contributions. Otherwise, if no license is present, all rights are reserved.

<hr>

**Congratulations!** You just created a beautiful home for your project. To access your project page, use (and share) the link as shown below.

> 🌟 `https://<your-github-username>.github.io/<your-project-name>`

````{note}
For example, you can view [this live demo](http://worldbank.github.io/template) using the following link:

> 🌟 [Live Demo - worldbank.github.io/template](http://worldbank.github.io/template)

You can also install the latest version directly from the main branch:

```bash
pip install git+https://github.com/worldbank/template
````

### Add content

The <span style="color:#3EACAD">template</span> is created as a [Jupyter Book](https://jupyterbook.org/intro.html) - an open-source project to build beautiful, publication-quality books and documents from computational content. Let's see below how to add, execute and publish new content for your project.

#### Updating the Jupyter Book `_config.yml` metadata

To configure your Jupyter Book for your project, you’ll need to update the `_config.yml` file. This file controls various aspects of the Jupyter Book, including the project title, description, and relevant URLs. Below is a template to update this file to reflect the project’s details.

```yaml
# Book settings
title: <your-project-title>
author: <your-team>

repository:
url: https://github.com/<your-organization>/<your-project>

# Jupyter Book options
execute:
  execute_notebooks: "auto"  #  Automatically execute notebooks during the build process
```

#### Update table of contents

When ready to publish the *documentation* on [GitHub Pages](https://pages.github.com/), all you need to do is edit the [table of contents](https://github.com/worldbank/template/blob/main/docs/_toc.yml) and add and/or update content you would like to display. [Jupyter Book](https://jupyterbook.org) supports content written as [Markdown](https://daringfireball.net/projects/markdown/), [Jupyter](https://jupyter.org) notebooks and [reStructuredText](https://docutils.sourceforge.io/rst.html) files and the `docs/_toc.yml` file controls the [table of contents](https://github.com/worldbank/template/blob/main/docs/_toc.yml) of your book.

The <span style="color:#3EACAD">template</span> comes with the [table of contents](https://github.com/worldbank/template/blob/main/docs/_toc.yml) below as an example.

```yaml

format: jb-book
root: README

parts:

  - caption: Examples
    numbered: True
    chapters:
      - file: notebooks/world-bank-api.ipynb
      - file: notebooks/world-bank-package.ipynb
      - file: notebooks/nasa-apod.ipynb
      - file: notebooks/bibliography.ipynb
```

```{seealso}
[Jupyter Book Structure and organize content](https://jupyterbook.org/en/stable/basics/organize.html)
```

#### Add executable content

[Jupyter Notebooks](https://jupyter.org) can be beautifully rendered and downloaded from your book. By default, the <span style="color:#3EACAD">template</span> will render any files listed on the [table of contents](#update-table-of-contents) that have a notebook structure. The <span style="color:#3EACAD">template</span> comes with a Jupyter notebook example, `notebooks/world-bank-api.ipynb`, to illustrate.

```{important}

By default, Jupyter notebooks are **not** executed. However, you can configure[Jupyter Book](https://jupyterbook.org) to run notebooks during the build process (on GitHub), allowing **code outputs** and **interactive visualizations** to be generated and included in the *documentation* automatically. When enabled, Jupyter notebooks are executed by [GitHub Actions](https://github.com/features/actions) each time a commit is made to the `main` branch. For this to work, it’s crucial to ensure that all necessary [dependencies](##use-pyproject-toml-for-python-package-management) are included in the repository. If you want to prevent a specific notebook from being executed, you can [exclude it from execution](https://jupyterbook.org/en/stable/content/execute.html#exclude-files-from-execution).
```

```{seealso}
[Jupyter Book Write executable content](https://jupyterbook.org/en/stable/content/executable/index.html)
```

#### Distributing Your Project as a Python Package

If your project uses [Python](https://python.org), it’s highly recommended to distribute it as a [package](https://packaging.python.org/en/latest/tutorials/packaging-projects/). By including a `pyproject.toml` file, the packaging process becomes more streamlined - *trust me [things can get intense](https://imgs.xkcd.com/comics/python_environment.png)*.

Additionally:

```{tip}
- Using `pyproject.toml` future-proofs your setup by aligning with modern packaging standards.
- The `pyproject.toml` file acts as a single source of truth for your Python dependencies and project metadata.
- You can combine Conda for system-level dependencies with `pyproject.toml` for Python dependencies, using Conda for environments and pip/poetry for Python packages.
- Any packages in the `src/` folder will be automatically discovered and installed.
```

##### Use `pyproject.toml` for Python Package Management

While the <span style="color:#3EACAD">template</span> recommends using [Conda](https://conda.io/projects/conda/en/latest/index.html) (or [Mamba](https://github.com/mamba-org/mamba)) as the environment manager and managing dependencies through an `environment.yml` file, there is an alternative approach that leverages `pyproject.toml`. This can be particularly advantageous if your project is a Python package or if you want to simplify and standardize the management of Python-specific dependencies.

##### Why use `pyproject.toml`?

The next step is ensure your code is maintainable, reliable and reproducible by including
any dependencies and requirements, such as packages, configurations, secrets (template) and additional instructions.

1. **Standardization**: `pyproject.toml` is a modern, standardized format defined by [PEP 518](https://peps.python.org/pep-0518/) and [PEP 621](https://peps.python.org/pep-0621/) that centralizes project configuration in Python projects, including build requirements and dependencies.

2. **Python Packaging**: If your project is to be distributed as a package, `pyproject.toml` is the preferred way to define build tools (like [hatch](https://hatch.pypa.io/latest/config/dependency/) or [poetry](https://python-poetry.org)) and metadata for your package (like name, version, dependencies, etc.). It allows tools like `pip` and `build` to install and package your project more effectively.

3. **Compatibility with Tools**: The `pyproject.toml` file is compatible with multiple Python packaging and dependency management tools such as `poetry` and `pip`. This allows for smoother integration with CI/CD pipelines, PyPI, and other environments.

4. **Separation of Concerns**: While Conda manages both system-level and Python-specific packages, using `pyproject.toml` helps isolate Python dependencies. This is useful if your project uses primarily Python packages and you want finer control over Python versioning and dependency resolution.

#### Example: Using `pyproject.toml`

This `pyproject.toml` file specifies the dependencies and other metadata for your Python package. You can install these packages using `pip`, ensuring that your Python environment is properly managed. You can still use Conda for system-level packages (such as `libc`, `gdal`, etc.), while using `pyproject.toml` for Python package management.

1. **`pyproject.toml` Example**:

    ```toml
    [build-system]
    requires = ["hatchling>=1.21.0", "hatch-vcs>=0.3.0"]
    build-backend = "hatchling.build"

    [project]
    name = "template"
    description = "A data science project"
    readme = { file = "README.md", content-type = "text/markdown" }
    license = { file = "LICENSE" }
    authors = [
      { name = "Your Name", email = "your.email@example.com" }
    ]
    dynamic = ["version"]

    python = ">=3.9"
    dependencies = [
      "pandas>=1.4.3,<2",
    ]
    [project.optional-dependencies]
    docs = [
        "docutils==0.17.1",
        "jupyter-book>=1,<2",
    ]

    [tool.hatch.build.targets.sdist]
    include = [
        "src/**/*"
    ]

    [tool.hatch.version]
    source = "vcs"
    ```

2. **Keep the Conda Environment for System-level Packages**:
    You can continue to use `environment.yml` to specify non-Python dependencies or packages not available on PyPI, such as `mamba` or `gdal`.

    ```yaml
    channels:
      - conda-forge
    dependencies:
      - python=3.9
      - mamba
      - gdal
    ```

3. **Installation**:
  To create an environment, you would first install the Conda dependencies and then use `pip` to install Python-specific dependencies from `pyproject.toml`. Alternatively, you can skip Conda and use `pip` for the entire setup.

    ```shell
    # Create Conda environment
    conda env create -f environment.yml -n <your-environment-name>

    # Activate the environment
    conda activate <your-environment-name>

    # Install Python dependencies
    pip install .
    ```

  To install a Python package directly from a [GitHub](https://github.com) repository using [pip](https://pip.pypa.io/en/stable/installation/), you can use the command pip install `git+https://github.com/<username>/<repository>.git`. This allows you to install the latest version of the package from the repository. You can also specify a particular branch or release tag by adding `@<branch_or_tag>` at the end of the URL This is particularly useful when you want to access features or fixes that haven’t been published on PyPI yet, or to get the latest updates from the repository.

  If you want to install the latest release, you should specify the tag associated with that release. For instance:

  ```shell
    pip install git+https://github.com/<username>/<repository>.git@<latest_release_tag>
  ```

```{seealso}
- [Packaging Python Projects](https://packaging.python.org/en/latest/tutorials/packaging-projects/)
- [Writing your pyproject.toml](https://packaging.python.org/en/latest/guides/writing-pyproject-toml/)
- [Conda Managing Environments](https://conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html)
```

#### Building Documentation Locally

To build the documentation locally, please follow these steps:

- Install the package with documentation dependencies:

  ```shell
    pip install -e .[docs]
  ```
  in some environments (e.g., on Mac OS), try this instead to scape the brackets:
   ```shell
    pip install -e .\[docs]\
  ```

- Build the documentation:

  ```shell
   jupyter-book build . --config docs/_config.yml --toc docs/_toc.yml
  ```

The generated documentation will be available in the `_build/html` directory. Open the `index.html` file in a web browser to view it.

## Code of Conduct

The <span style="color:#3EACAD">template</span> maintains a [Code of Conduct](docs/CODE_OF_CONDUCT.md) to ensure an inclusive and respectful environment for everyone. Please adhere to it in all interactions within our community.

## License

The <span style="color:#3EACAD">template</span> is licensed under the [**Mozilla Public License**](https://www.mozilla.org/en-US/MPL). Remember to replace the [license](LICENSE) if necessary. If open source, [choose an open source license](https://choosealicense.com).
