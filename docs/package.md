# Package

## Installing Packages

### [Installing from local archives](https://packaging.python.org/en/latest/tutorials/installing-packages/#installing-from-local-archives)

List of all packages.

```bash
pip freeze --all > requirements.txt
```

Download a archive file.

```bash
pip download SomeProject [-d dir]
pip download -r requirements.txt
```

Install a particular source archive file.

```bash
pip install ./downloads/SomeProject-1.0.4.tar.gz
```

Install from a local directory containing archives (and don’t check PyPI)

```bash
pip install --no-index --find-links=file:///local/dir/ SomeProject
pip install --no-index --find-links=/local/dir/ SomeProject
pip install --no-index --find-links=relative/dir/ SomeProject
```
