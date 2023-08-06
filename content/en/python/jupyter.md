---
title: Jupyter & JupyterLab
---

## Links
- `nb_conda_kernels`: <https://github.com/Anaconda-Platform/nb_conda_kernels>

## Install JupyterLab
- with pip: `pip install jupyterlab`
- with conda: `conda install jupyterlab nb_conda_kernels`

## View Jupyter Notebook online
This can be done here: <https://nbviewer.jupyter.org/>

## Add Conda Environment to Jupyter Lab
`python -m ipykernel install --user --name <conda_env_name>
--display-name "<conda_env_name>"`

## Environment settings for Jupyter
Environment settings for Jupyter are not read from `.bashrc`. You have to
specify them in a `.py` file at `~/.ipython/profile_default/startup/`

For example:
```bash
echo -e "import os\n\nos.environ[\"SOME_URL\"] = \"http://mlflow.company.tld:5000\"" > ~/.ipython/profile_default/startup/set_env.py
```
## Install Jupyter on Server for Remote Access
- create blank config: `jupyter notebook --generate-config`
- Guide: https://jupyter-notebook.readthedocs.io/en/stable/public_server.html#running-a-public-notebook-server
- Password hash generation: https://jupyter-notebook.readthedocs.io/en/stable/public_server.html#preparing-a-hashed-password
- Certificate generation: https://jupyter-notebook.readthedocs.io/en/stable/public_server.html#using-ssl-for-encrypted-communication

## Clean the Trash
When you use the "File Browser" of Jupyter Lab to delete files they are not deleted but moved to `~/.local/share/Trash`. Clean that folder to delete them.
