# Conda

- Conda: [Docs](https://docs.conda.io/en/latest/)
- [Miniconda release notes](https://docs.anaconda.com/free/miniconda/miniconda-release-notes)

## Install miniconda

```bash
$ pyenv install --list | grep 'miniconda'
$ pyenv install miniconda3-latest
```

```bash
$ pyenv versions

  system
* 3.11.5
  miniconda3-latest
```

## Activate miniconda by pyenv

```bash
$ pyenv activate miniconda3-latest
```

```bash
(miniconda3-latest) $ conda --version

conda 23.11.0
```

```bash
(miniconda3-latest) $ conda env list

# conda environments:
#
base                  *  ~/.pyenv/versions/miniconda3-latest
```

---

## Create a conda virtual environment in miniconda

### Create a environment

```bash
(miniconda3-latest) $ conda create -n venv370 python=3.7.0
```

#### check in pyenv

```bash
(miniconda3-latest) $ pyenv versions

  system
  3.11.5
* miniconda3-latest (set by PYENV_VERSION environment variable)
  miniconda3-latest/envs/venv370
```

#### check in pyenv-virtualenv

```bash
(miniconda3-latest) $ pyenv virtualenvs

* miniconda3-latest (created from ~/.pyenv/versions/miniconda3-latest)
  miniconda3-latest/envs/venv370 (created from ~/.pyenv/versions/miniconda3-latest)
```

---

### Activate conda venv

First, deactivate `miniconda3-latest`:

```bash
(miniconda3-latest) $ pyenv deactivate
$ pyenv versions

  system
* 3.11.5 (set by PYENV_VERSION environment variable)
  miniconda3-latest
  miniconda3-latest/envs/venv370
```

Then, Activate the conda venv `miniconda3-latest/envs/venv370`:

```bash
$ pyenv activate miniconda3-latest/envs/venv370
```

Now `miniconda3-latest/envs/venv370`.

#### check in pyenv

```bash
(venv370) $ pyenv versions

  system
  3.11.5
  miniconda3-latest
* miniconda3-latest/envs/venv370 (set by PYENV_VERSION environment variable)
```

#### check in pyenv-virtualenv

```bash
(venv370) $ pyenv virtualenvs

  miniconda3-latest (created from ~/.pyenv/versions/miniconda3-latest)
* miniconda3-latest/envs/venv370 (created from ~/.pyenv/versions/miniconda3-latest)
```

#### check in conda

```bash
(venv370) $ conda env list

# conda environments:
#
base                     ~/.pyenv/versions/miniconda3-latest
venv370               *  ~/.pyenv/versions/miniconda3-latest/envs/venv370
```

#### check python version

```bash
(venv370) $ python -V

Python 3.7.0
```

---

### Make a softlink

```bash
~/.pyenv/versions
├── 3.11.5/
└── miniconda3-latest/
    └── envs/
        └── venv370/
```

#### Create a link

```bash
(venv370) $ ln -s ~/.pyenv/versions/miniconda3-latest/envs/venv370 ~/.pyenv/versions/venv370

~/.pyenv/versions
├── 3.11.5/
├── miniconda3-latest/
└── venv370 -> ~/.pyenv/versions/miniconda3-latest/envs/venv370
```

```bash
(venv370) $ pyenv versions

  system
  3.11.5
  miniconda3-latest
* miniconda3-latest/envs/venv370 (set by PYENV_VERSION environment variable)
  venv370 --> ~/.pyenv/versions/miniconda3-latest/envs/venv370
```

Change env `miniconda3-latest/envs/venv370` → `venv370`:

```bash
(venv370) $ pyenv deactivate
$ pyenv activate venv370
(venv370) $ python -V

Python 3.7.0
```

#### check in pyenv

```bash
(venv370) $ pyenv versions
  system
  3.11.5
  miniconda3-latest
  miniconda3-latest/envs/venv370
* venv370 --> ~/.pyenv/versions/miniconda3-latest/envs/venv370 (set by PYENV_VERSION environment variable)
```

#### check in pyenv-virtualenv

```bash
(venv370) $ pyenv virtualenvs

  miniconda3-latest (created from ~/.pyenv/versions/miniconda3-latest)
  miniconda3-latest/envs/venv370 (created from ~/.pyenv/versions/miniconda3-latest)
* venv370 (created from ~/.pyenv/versions/miniconda3-latest)
```

---

### Remove conda venv

Change env `venv370` → `miniconda3-latest`:

```bash
(venv370) $ pyenv deactivate
$ pyenv activate miniconda3-latest
(miniconda3-latest) $ 
```

Remove the conda env:

```bash
(miniconda3-latest) $ conda env remove -n venv370

Remove all packages in environment ~/.pyenv/versions/miniconda3-latest/envs/venv370:
```

Remove the symlink:

```bash
$ rm ~/.pyenv/versions/venv370
```
