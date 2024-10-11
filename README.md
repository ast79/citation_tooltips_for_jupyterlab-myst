# citation tooltips for jupyterlab-myst

A patch to the jupyterlab_myst 2.4.2 release that adds a custom rfg role (see https://mystmd.org/guide/quickstart-myst-markdown#directives-and-roles) which displays the associated citation in a popup tooltip. Their hover link counters operate seperately from those of the cite role and use the red color. Mouse clicks on the hover link freeze or unfreeze the display of its tooltip and a displayed tooltip is draggable.

This upload is little more than a hack to discover how it could be done that is not intended for publication beyond this step.  jupyterlab_myst doesn't yet render MyST citations in notebooks or in Markdown file previews, it doesn't even read in Bibtex files. The 'myst build' commands will parse rfg role instances and render no output up completion.

## Requirements

- JupyterLab >= 4.0.0

## Install

To install the extension inside a virtual environment, a download of the citation-tooltips-jupyterlab_myst-2.4.2.patch file from the repository is needed, and so are the following commands in a code shell starting at the download directory:

```bash
wget https://github.com/jupyter-book/jupyterlab-myst/releases/download/v2.4.2/jupyterlab_myst-2.4.2.tar.gz

tar xfz jupyterlab_myst-2.4.2.tar.gz

cd jupyterlab_myst-2.4.2
 
patch -p1 < ../citation-tooltips-jupyterlab_myst-2.4.2.patch

# The remainder corresponds to the development install steps for jupyterlab-myst
# at https://github.com/jupyter-book/jupyterlab-myst#development-install

# Activate the local JupyterLab environment 
# Install package in development mode
pip install -e ".[test]"
# Link your development version of the extension with JupyterLab
jupyter labextension develop . --overwrite
# Server extension must be manually installed in develop mode
jupyter server extension enable jupyterlab_myst

# An example notebook can be found at ./tests/notebook/citation-tooltips.ipynb
cd tests/notebooks
jupyter lab
```
