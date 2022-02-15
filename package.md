# Package

## Installing Packages

### [Installing from local archives](https://packaging.python.org/en/latest/tutorials/installing-packages/#installing-from-local-archives)

Download a archive file.

```bash
python3 -m pip download SomeProject [-d dir]
```

Install a particular source archive file.

```bash
python3 -m pip install ./downloads/SomeProject-1.0.4.tar.gz
```

Install from a local directory containing archives (and don’t check PyPI)

```bash
python3 -m pip install --no-index --find-links=file:///local/dir/ SomeProject
python3 -m pip install --no-index --find-links=/local/dir/ SomeProject
python3 -m pip install --no-index --find-links=relative/dir/ SomeProject
```
