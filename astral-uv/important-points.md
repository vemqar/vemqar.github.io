**astral-uv / important points**

- In the repo, all you have to do is: `uv python install` so it picks up on the `.python-version` in the repo and installs it if system doesn't have that python version. If this is not specified you can manually set it ; e.g. `uv python 3.12`. If not such python was specified, uv upon running should respective the python version in `pyproject.toml`
- you do not have to create a virtual environment manually. if `.venv` doesn't exist upon running `uv run ...` the `.venv` will be created. You can also do this separately by running `uv sync` . 
- When using uv, the virtual environment **does not need to be activated**. uv will find a virtual environment (named `.venv`) in the working directory or any parent directories.

So very simply if you are trying to run an existing project with `uv`:
1. `uv python install
2. `uv sync` (creates `.venv`)
3. `uv run ...`

You do not have to run step 2 separately, can just go straight to step 3 since that will do the sync. 