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
echo -e '\n# virtualenv' >> ~/.profile
echo 'eval "$(pyenv virtualenv-init -)"' >> ~/.profile
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

```bash
echo -e '\n# autoenv' >> ~/.profile
echo "AUTOENV_ENV_FILENAME='.autoenv'" >> ~/.profile
echo "AUTOENV_ENV_LEAVE_FILENAME='.autoenv.leave'" >> ~/.profile
echo "AUTOENV_ENABLE_LEAVE='enabled'" >> ~/.profile
echo 'source ~/.autoenv/activate.sh' >> ~/.profile
```

### Jupyter

```bash
conda install -c conda-forge jupyterlab
pip install jupyterlab
```

#### Configuration

```bash
jupyter notebook --generate-config # == jupyter lab --generate-config

Writing default config to: /home/master/.jupyter/jupyter_notebook_config.py
```

```bash
vi ~/.jupyter/jupyter_notebook_config.py
```

```py
c.NotebookApp.allow_origin = '*' # line 48
c.NotebookApp.ip = '0.0.0.0' # line 204. or 'domain.internal' or '172.xxx.xxx.xxx'
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
pyenv activate conda3
```

```bash
(conda3) $ pyenv versions
  3.9.1
* conda3 (set by PYENV_VERSION environment variable)
  miniconda3-latest
  miniconda3-latest/envs/conda3

(conda3) $ pyenv virtualenvs
* conda3 (created from /home/master/.pyenv/versions/miniconda3-latest)
  miniconda3-latest (created from /home/master/.pyenv/versions/miniconda3-latest)
  miniconda3-latest/envs/conda3 (created from /home/master/.pyenv/versions/miniconda3-latest)
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
* conda3 (created from /home/master/.pyenv/versions/miniconda3-latest)
  miniconda3-latest (created from /home/master/.pyenv/versions/miniconda3-latest)
  miniconda3-latest/envs/conda3 (created from /home/master/.pyenv/versions/miniconda3-latest)
  miniconda3-latest/envs/venv390 (created from /home/master/.pyenv/versions/miniconda3-latest)
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
  conda3 (created from /home/master/.pyenv/versions/miniconda3-latest)
  miniconda3-latest (created from /home/master/.pyenv/versions/miniconda3-latest)
  miniconda3-latest/envs/conda3 (created from /home/master/.pyenv/versions/miniconda3-latest)
* miniconda3-latest/envs/venv390 (created from /home/master/.pyenv/versions/miniconda3-latest)

(venv390) λ python -V
Python 3.9.0
```

#### Remove conda venv

```bash
(venv390) 1 λ pyenv activate conda3

(conda3) λ conda env list
# conda environments:
#
base                     /home/master/.pyenv/versions/miniconda3-latest
conda3                *  /home/master/.pyenv/versions/miniconda3-latest/envs/conda3
venv390                  /home/master/.pyenv/versions/miniconda3-latest/envs/venv390

(conda3) λ conda env remove -n venv390
Remove all packages in environment /home/master/.pyenv/versions/miniconda3-latest/envs/venv390:
```
