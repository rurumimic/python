# Poetry

```bash
curl -sSL https://install.python-poetry.org | python3 -
```

## Install

### Ubuntu

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

### Uninstall

```bash
curl -sSL https://install.python-poetry.org | python3 - --uninstall
```
