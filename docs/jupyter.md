# Jupyter

- Jupyter: [Install](https://jupyter.org/install.html)
- Install [miniconda](pyenv.md#conda)

## Install

```bash
conda install -c conda-forge jupyterlab
pip install jupyterlab
```

### Lab Configuration

```bash
jupyter lab --generate-config

Writing default config to: ~/.jupyter/jupyter_lab_config.py
```

```bash
vi ~/.jupyter/jupyter_lab_config.py
```

```py
c.LabApp.open_browser = False # line 348
c.ServerApp.allow_origin = '*' # line 411
c.ServerApp.ip = '0.0.0.0' # line 595. or 'domain.local or '172.xxx.Sxxx.xxx'
c.ServerApp.open_browser = False # line 682
c.ServerApp.browser = u'open -a /Applications/Google\ Chrome.app %s'
```

### Notebook Configuration

```bash
jupyter notebook --generate-config

Writing default config to: ~/.jupyter/jupyter_notebook_config.py
```

```bash
vi ~/.jupyter/jupyter_notebook_config.py
```

```py
c.NotebookApp.allow_origin = '*' # line 48
c.NotebookApp.ip = '0.0.0.0' # line 204. or 'domain.local or '172.xxx.xxx.xxx'
c.NotebookApp.open_browser = False # line 267
```
