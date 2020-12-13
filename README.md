# Python

- [pyenv](https://github.com/pyenv/pyenv)
- [virtualenv](https://github.com/pyenv/pyenv-virtualenv)
- [autoenv](https://github.com/inishchith/autoenv)
- [direnv](https://direnv.net/)

## Install

### Pyenv

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

### Virtualenv

```bash
brew install pyenv-virtualenv
brew upgrade pyenv-virtualenv
```

```bash
echo 'eval "$(pyenv virtualenv-init -)"' >> ~/.bash_profile
echo 'eval "$(pyenv virtualenv-init -)"' >> ~/.zshrc
```

### Autoenv

```bash
git clone git://github.com/inishchith/autoenv.git ~/.autoenv
```

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
