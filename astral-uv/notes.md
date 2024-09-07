**astral-uv / notes**

Install:

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
uv --version
```

Python  

```bash
uv python list
uv python install 3.12
```

By default `uv python install` will verify that a managed Python version is installed or install the latest version.

However, a project may include a `.python-version` file specifying a default Python version. If present, uv will install the Python version listed in the file.

Project Init

```bash
uv init uv_test
which python 
> /home/moses/.pyenv/shims/python
uv python pin 3.12
> Pinned `.python-version` to `3.12`
uv run which python
> Using Python 3.12.5
> Creating virtualenv at: .venv
> /home/moses/Repos/uv_test/.venv/bin/python
> uv.lock also created with this step
uv run python --version
> 3.12.5
```

The lockfile is created and updated during uv invocations that use the project environment, i.e., `uv sync` and `uv run`. The lockfile may also be explicitly updated using `uv lock`.

Installing Packages

```bash
uv add pandas datadog
```

if you just run `python` those packages are not there. `uv run hello.py` works, while just `python hello.py` doesn't.  

If you do `uv venv ; uv run hello.py` it installs the packages then runs it. 

After this, when you do `source .venv/bin/activate` your packages are not available (e.g. `python hello.py` doesn't work).

When using uv, the virtual environment does not need to be activated. uv will find a virtual environment (named `.venv`) in the working directory or any parent directories.

Steps for Project:

1. `uv python install` so it install the python version specified in `.python-version`
2. `uv run hello.py` , before running creates `.venv` and installs specified packages or run `uv sync` for standalone.

This doesn't work:

```bash
uv sync
source .venv/bin/activate
flask run -p 3000
python example.py
```
