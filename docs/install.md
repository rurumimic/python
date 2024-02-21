# Install

1. Install required packages
2. Set RC
3. Install Pyenv
4. Install Autoenv
5. Install Latest Python
6. Set Global Python Version
7. Set Vim's Python

## Prerequisites

- pyenv wiki: [Suggested build environment](https://github.com/pyenv/pyenv/wiki#suggested-build-environment)

### macOS

```bash
xcode-select --install
brew install openssl readline sqlite3 xz zlib tcl-tk
```

### Linux

#### Ubuntu

```bash
build_tools="
build-essential
libssl-dev
zlib1g-dev
libbz2-dev
libreadline-dev
libsqlite3-dev
curl
libncursesw5-dev
xz-utils
tk-dev
libxml2-dev
libxmlsec1-dev
libffi-dev
liblzma-dev
"

sudo apt update
sudo apt install $build_tools
```

## Set profile.rc

Add to `.bashrc` or `.zshrc`:

```bash
# pyenv
if [ -d "$HOME/.pyenv" ]; then
    export PYENV_ROOT="$HOME/.pyenv"
    command -v pyenv >/dev/null || export PATH="$PYENV_ROOT/bin:$PATH"
    eval "$(pyenv init -)"
    eval "$(pyenv virtualenv-init -)"
fi

# autoenv
if [ -d "$HOME/.autoenv" ]; then
    export AUTOENV_ENV_FILENAME='.autoenv'
    export AUTOENV_ENV_LEAVE_FILENAME='.autoenv.leave'
    export AUTOENV_ENABLE_LEAVE='enabled'
    source "$HOME/.autoenv/activate.sh"
fi
```

## Pyenv

- [pyenv](https://github.com/pyenv/pyenv)

```bash
curl https://pyenv.run | bash
```

## Autoenv

- [autoenv](https://github.com/hyperupcall/autoenv)

```bash
git clone https://github.com/hyperupcall/autoenv $HOME/.autoenv
```

## Install Latest Python

```bash
version=3.11
latest_version=$(pyenv latest -k $version)
pyenv install -v --skip-existing $latest_version
```

## Update Global Python Version

```bash
global_version=$(pyenv global)
if [ $global_version != $latest_version ]; then
    pyenv global $latest_version
fi
```

```bash
pip install --upgrade pip setuptools wheel
```

## for Vim

```bash
pyenv virtualenv $latest_version vim
$HOME/.pyenv/versions/vim/bin/pip install --upgrade pip setuptools wheel pynvim
```
