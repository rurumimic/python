# Python

- [pyenv](https://github.com/pyenv/pyenv)
- [virtualenv](https://github.com/pyenv/pyenv-virtualenv)
- [autoenv](https://github.com/inishchith/autoenv)
- [direnv](https://direnv.net/)

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

## Usage

### Pyenv

```bash
pyenv install --list
```

```bash
pyenv install 3.9.0
pyenv versions
```

### Virtualenv

```bash
pyenv virtualenv 3.9.0 venv390
pyenv virtualenvs
```

### Autoenv

```bash
echo 'pyenv activate venv390' > .autoenv
echo 'pyenv deactivate' > .autoenv.leave
```
