# Python

- [pyenv](#pyenv)
  - [github](https://github.com/pyenv/pyenv)
- [virtualenv](#virtualenv)
  - [github](https://github.com/pyenv/pyenv-virtualenv)
- [autoenv](#autoenv)
  - [github](https://github.com/inishchith/autoenv)
- [poetry](#poetry)
  - [documentation](https://python-poetry.org/docs/master)
  - [github](https://github.com/python-poetry/poetry)
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
brew install openssl readline sqlite3 xz zlib tcl-tk
```

##### Install

```bash
brew update
brew install pyenv
brew upgrade pyenv
```

Install: [dependencies](https://github.com/pyenv/pyenv/wiki#suggested-build-environment)

For bash:

```bash
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.bash_profile
echo 'command -v pyenv >/dev/null || export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.bash_profile
echo 'eval "$(pyenv init -)"' >> ~/.bash_profile
```

For zsh:

```bash
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.zshrc
echo 'command -v pyenv >/dev/null || export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.zshrc
echo 'eval "$(pyenv init -)"' >> ~/.zshrc
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
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.profile
echo 'export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.profile
echo 'eval "$(pyenv init --path)"' >> ~/.profile

echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.zprofile
echo 'export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.zprofile
echo 'eval "$(pyenv init --path)"' >> ~/.zprofile

echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.zshrc
echo 'export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.zshrc
echo 'eval "$(pyenv init -)"' >> ~/.zshrc
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
git clone https://github.com/hyperupcall/autoenv ~/.autoenv
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
echo -e '\n# autoenv' >> ~/.zshrc
echo "AUTOENV_ENV_FILENAME='.autoenv'" >> ~/.zshrc
echo "AUTOENV_ENV_LEAVE_FILENAME='.autoenv.leave'" >> ~/.zshrc
echo "AUTOENV_ENABLE_LEAVE='enabled'" >> ~/.zshrc
echo 'source ~/.autoenv/activate.sh' >> ~/.zshrc
```

### Poetry

```bash
curl -sSL https://install.python-poetry.org | python3 -
```

#### Ubuntu

For bash:

```bash
echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.bashrc
poetry completions bash > /etc/bash_completion.d/poetry
```

For zsh:

```bash
echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.zshrc
poetry completions zsh > ~/.zfunc/_poetry
```
in `.zshrc` before `compinit`:

```bash
fpath+=~/.zfunc
```

For Oh-My-Zsh:
```bash
echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.zshrc
mkdir $ZSH_CUSTOM/plugins/poetry
poetry completions zsh > $ZSH_CUSTOM/plugins/poetry/_poetry
```

in `.zshrc`:

```bash
plugins(
	poetry
	...
	)
```

#### Uninstall

```bash
curl -sSL https://install.python-poetry.org | python3 - --uninstall
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
pyenv virtualenv 3.10.5 venv310
pyenv virtualenvs
```

#### Remove a virtual environment

```bash
pyenv virtualenv-delete venv310
```

### Set auto-activate

```bash
echo 'pyenv activate venv310' > .autoenv
echo 'pyenv deactivate' > .autoenv.leave
```

### Conda

#### Download miniconda

```bash
pyenv install --list | grep conda
pyenv install miniconda3-latest
```

#### Create a conda virtual environment in miniconda

```bash
pyenv activate miniconda3-latest
```

```bash
(root) (miniconda3-latest) $ conda create -n venv370 python=3.7.0
```

```bash
(root) (miniconda3-latest) $ pyenv versions
  system
  2.7.18
  3.10.5
* miniconda3-latest (set by PYENV_VERSION environment variable)
  miniconda3-latest/envs/venv370
```

```bash
(root) (miniconda3-latest) $ pyenv virtualenvs
* miniconda3-latest (created from ~/.pyenv/versions/miniconda3-latest)
  miniconda3-latest/envs/venv370 (created from ~/.pyenv/versions/miniconda3-latest)
```

#### Activate conda venv

Deactivate `miniconda3-latest`:

```bash
(root) (miniconda3-latest) $ pyenv deactivate
```

Activate the conda venv:

```bash
pyenv activate miniconda3-latest/envs/venv370
```

Now `miniconda3-latest/envs/venv370`:

```bash
(venv370) (venv370) $ pyenv versions
  system
  2.7.18
  3.10.5
  miniconda3-latest
* miniconda3-latest/envs/venv370 (set by PYENV_VERSION environment variable)
```

```bash
(venv370) (venv370) $ pyenv virtualenvs
  miniconda3-latest (created from ~/.pyenv/versions/miniconda3-latest)
* miniconda3-latest/envs/venv370 (created from ~/.pyenv/versions/miniconda3-latest)
```

```bash
conda env list
# conda environments:
#
base                    ~/.pyenv/versions/miniconda3-latest
venv370              *  ~/.pyenv/versions/miniconda3-latest/envs/venv370
```

```bash
(venv370) (venv370) $ python -V
Python 3.7.0
```

##### Make a softlink

```bash
~/.pyenv/versions
├── 2.7.18/
├── 3.10.5/
└── miniconda3-latest/
    └── envs/
        └── venv370/
```

```bash
ln -s ~/.pyenv/versions/miniconda3-latest/envs/venv370 ~/.pyenv/versions/venv370
```

```bash
pyenv versions

  system
  2.7.18
* 3.10.5 (set by ~/.pyenv/version)
  miniconda3-latest
  miniconda3-latest/envs/venv370
  venv370
```

Activate:

```bash
pyenv activate venv370
```

```bash
(venv370) (venv370) $ python -V
Python 3.7.0

(venv370) (venv370) $ pyenv versions
  system
  2.7.18
  3.10.5
  miniconda3-latest
  miniconda3-latest/envs/venv370
* venv370 (set by PYENV_VERSION environment variable)

(venv370) (venv370) $ pyenv virtualenvs
  miniconda3-latest (created from ~/.pyenv/versions/miniconda3-latest)
  miniconda3-latest/envs/venv370 (created from ~/.pyenv/versions/miniconda3-latest)
* venv370 (created from ~/.pyenv/versions/miniconda3-latest)
```

#### Remove conda venv

Deactivate the conda env:

```bash
(venv370) (venv370) $ pyenv deactivate
```

Remove the symlink:

```bash
rm ~/.pyenv/versions/venv370
```

Activate `miniconda3-latest`:

```bash
pyenv activate miniconda3-latest
```

```bash
(root) (miniconda3-latest) $ conda env remove -n venv370
Remove all packages in environment ~/.pyenv/versions/miniconda3-latest/envs/venv370:
```

#### Pyenv global

```bash
pyenv global 3.10.5
```
