# Python

- [pyenv](#pyenv)
  - [github](https://github.com/pyenv/pyenv)
- [virtualenv](#virtualenv)
  - [github](https://github.com/pyenv/pyenv-virtualenv)
- [autoenv](#autoenv)
  - [github](https://github.com/inishchith/autoenv)
- direnv
  - [doc](https://direnv.net/)
- [conda](#conda)
  - [doc](https://docs.conda.io/en/latest/)
- [jupyter](#jupyter)
  - [install](https://jupyter.org/install.html)

## Install

### Pyenv

#### macOS

##### Prerequisites

```bash
xcode-select --install
brew install openssl readline sqlite3 xz zlib
```

##### Install

```bash
brew update
brew install pyenv
brew upgrade pyenv
```

Install: [dependencies](https://github.com/pyenv/pyenv/wiki#suggested-build-environment)

```bash
echo -e 'if command -v pyenv 1>/dev/null 2>&1; then\n  eval "$(pyenv init -)"\nfi' >> ~/.bash_profile
echo -e 'if command -v pyenv 1>/dev/null 2>&1; then\n  eval "$(pyenv init -)"\nfi' >> ~/.zshrc
```

```bash
exec "$SHELL"
```

#### Ubuntu

##### Prerequisites

```bash
sudo apt-get update
sudo apt-get install -y --no-install-recommends make build-essential libssl-dev zlib1g-dev libbz2-dev libreadline-dev libsqlite3-dev wget curl llvm libncurses5-dev xz-utils tk-dev libxml2-dev libxmlsec1-dev libffi-dev liblzma-dev
```

##### Install

```bash
git clone https://github.com/pyenv/pyenv.git ~/.pyenv
```

For bash:

```bash
echo -e '\n# pyenv' >> ~/.profile
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.profile
echo 'export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.profile
echo -e 'if command -v pyenv 1>/dev/null 2>&1; then\n  eval "$(pyenv init -)"\nfi' >> ~/.profile
```

For zsh:

```bash
echo -e '\n# pyenv' >> ~/.zprofile
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.zprofile
echo 'export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.zprofile
echo -e 'if command -v pyenv 1>/dev/null 2>&1; then\n  eval "$(pyenv init -)"\nfi' >> ~/.zprofile
```

Restart shell:

```bash
exec "$SHELL"
```

### Virtualenv

#### macOS

```bash
brew install pyenv-virtualenv
brew upgrade pyenv-virtualenv
```

```bash
echo 'eval "$(pyenv virtualenv-init -)"' >> ~/.bash_profile
echo 'eval "$(pyenv virtualenv-init -)"' >> ~/.zshrc
```

#### Ubuntu

```bash
git clone https://github.com/pyenv/pyenv-virtualenv.git $(pyenv root)/plugins/pyenv-virtualenv
```

For bash:

```bash
echo -e '\n# virtualenv' >> ~/.profile
echo 'eval "$(pyenv virtualenv-init -)"' >> ~/.profile
```

For zsh:

```bash
echo -e '\n# virtualenv' >> ~/.zprofile
echo 'eval "$(pyenv virtualenv-init -)"' >> ~/.zprofile
```

Restart shell:

```bash
exec "$SHELL"
```

### Autoenv

```bash
git clone git://github.com/inishchith/autoenv.git ~/.autoenv
```

#### macOS

```bash
echo "AUTOENV_ENV_FILENAME='.autoenv'" >> ~/.bash_profile
echo "AUTOENV_ENV_LEAVE_FILENAME='.autoenv.leave'" >> ~/.bash_profile
echo "AUTOENV_ENABLE_LEAVE='enabled'" >> ~/.bash_profile
echo 'source ~/.autoenv/activate.sh' >> ~/.bash_profile

echo "AUTOENV_ENV_FILENAME='.autoenv'" >> ~/.zshrc
echo "AUTOENV_ENV_LEAVE_FILENAME='.autoenv.leave'" >> ~/.zshrc
echo "AUTOENV_ENABLE_LEAVE='enabled'" >> ~/.zshrc
echo 'source ~/.autoenv/activate.sh' >> ~/.zshrc
```

#### Ubuntu

For bash:

```bash
echo -e '\n# autoenv' >> ~/.profile
echo "AUTOENV_ENV_FILENAME='.autoenv'" >> ~/.profile
echo "AUTOENV_ENV_LEAVE_FILENAME='.autoenv.leave'" >> ~/.profile
echo "AUTOENV_ENABLE_LEAVE='enabled'" >> ~/.profile
echo 'source ~/.autoenv/activate.sh' >> ~/.profile
```

For zsh:

```bash
echo -e '\n# autoenv' >> ~/.zprofile
echo "AUTOENV_ENV_FILENAME='.autoenv'" >> ~/.zprofile
echo "AUTOENV_ENV_LEAVE_FILENAME='.autoenv.leave'" >> ~/.zprofile
echo "AUTOENV_ENABLE_LEAVE='enabled'" >> ~/.zprofile
echo 'source ~/.autoenv/activate.sh' >> ~/.zprofile
```

### Jupyter

```bash
conda install -c conda-forge jupyterlab
pip install jupyterlab
```

#### Lab Configuration

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

#### Notebook Configuration

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

---

## Usage

### Download Python by Pyenv

```bash
pyenv install --list
```

```bash
pyenv install 3.9.0
pyenv versions
```

#### Remove Python

```bash
pyenv uninstall 3.9.0
```

### Create a virtual environment

```bash
pyenv virtualenv 3.9.0 venv390
pyenv virtualenvs
```

#### Remove a virtual environment

```bash
pyenv virtualenv-delete venv390
```

### Set auto-activate

```bash
echo 'pyenv activate venv390' > .autoenv
echo 'pyenv deactivate' > .autoenv.leave
```

### Conda

#### Download miniconda

```bash
pyenv install --list | grep conda
pyenv install miniconda3-latest
```

#### Create a conda environment

```bash
pyenv virtualenv miniconda3-latest conda3
~~pyenv activate conda3~~
conda activate conda3
conda deactivate
```

```bash
(conda3) $ pyenv versions
  3.9.1
* conda3 (set by PYENV_VERSION environment variable)
  miniconda3-latest
  miniconda3-latest/envs/conda3

(conda3) $ pyenv virtualenvs
* conda3 (created from ~/.pyenv/versions/miniconda3-latest)
  miniconda3-latest (created from ~/.pyenv/versions/miniconda3-latest)
  miniconda3-latest/envs/conda3 (created from ~/.pyenv/versions/miniconda3-latest)
```

#### Create a venv in conda venv

```bash
conda create -n venv390 python=3.9.0
```

```bash
(conda3) $ pyenv versions
  3.9.1
* conda3 (set by PYENV_VERSION environment variable)
  miniconda3-latest
  miniconda3-latest/envs/conda3
  miniconda3-latest/envs/venv390

(conda3) $ pyenv virtualenvs
* conda3 (created from ~/.pyenv/versions/miniconda3-latest)
  miniconda3-latest (created from ~/.pyenv/versions/miniconda3-latest)
  miniconda3-latest/envs/conda3 (created from ~/.pyenv/versions/miniconda3-latest)
  miniconda3-latest/envs/venv390 (created from ~/.pyenv/versions/miniconda3-latest)
```

#### Activate another conda venv

In `conda3`:

```bash
(conda3) λ pyenv version
conda3 (set by PYENV_VERSION environment variable)

(conda3) λ python -V
Python 3.9.1

(conda3) λ pyenv activate miniconda3-latest/envs/venv390
```

Now `miniconda3-latest/envs/venv390`:

```
(venv390) λ pyenv versions
  3.9.1
  conda3
  miniconda3-latest
  miniconda3-latest/envs/conda3
* miniconda3-latest/envs/venv390 (set by PYENV_VERSION environment variable)

(venv390) λ pyenv virtualenvs
  conda3 (created from ~/.pyenv/versions/miniconda3-latest)
  miniconda3-latest (created from ~/.pyenv/versions/miniconda3-latest)
  miniconda3-latest/envs/conda3 (created from ~/.pyenv/versions/miniconda3-latest)
* miniconda3-latest/envs/venv390 (created from ~/.pyenv/versions/miniconda3-latest)

(venv390) λ python -V
Python 3.9.0
```

#### Remove conda venv

```bash
(venv390) 1 λ pyenv activate conda3

(conda3) λ conda env list
# conda environments:
#
base                     ~/.pyenv/versions/miniconda3-latest
conda3                *  ~/.pyenv/versions/miniconda3-latest/envs/conda3
venv390                  ~/.pyenv/versions/miniconda3-latest/envs/venv390

(conda3) λ conda env remove -n venv390
Remove all packages in environment ~/.pyenv/versions/miniconda3-latest/envs/venv390:
```

#### Pyenv global

```bash
pyenv global 3.8.6 miniconda3-latest
```
