# Pyenv

## Install Python

### versions and virtual environments

```bash
pyenv versions
```

```bash
pyenv install --list
pyenv latest -k 3.11
```

### Install Latest Python

```bash
version=3.11
latest_version=$(pyenv latest -k $version)
pyenv install -v --skip-existing $latest_version
```

### Set Global Python

```bash
pyenv global 3.11.5
```

### Remove Python

```bash
pyenv uninstall 3.11.5
```

---

## Create a virtual environment

```bash
pyenv virtualenv 3.11.5 venv311
pyenv virtualenvs
```

### Remove a virtual environment

```bash
pyenv virtualenv-delete venv311
```

### Set auto-activate

```bash
echo 'pyenv activate venv311' > .autoenv
echo 'pyenv deactivate' > .autoenv.leave
```
