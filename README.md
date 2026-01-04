# Python Project CI/CD (GitHub Actions)

This repo uses GitHub Actions to run a basic CI pipeline on every push/PR to `main`.

## What the pipeline does
- Sets up Python (3.10, 3.11, 3.12)
- Installs dependencies from `requirements.txt`
- Lints the codebase with `flake8`
- Runs `pytest` (will succeed even with 0 tests)
- Performs a quick import check for `main.py`

## Triggers
- On `push` and `pull_request` to `main`
- Manual run via the Actions tab (`workflow_dispatch`)

## Local dev tips
- Create a virtual environment and install dependencies:

```bash
python -m venv .venv
. .venv/Scripts/activate  # Windows PowerShell: . .venv\Scripts\Activate.ps1
pip install -r requirements.txt
pip install flake8 pytest
```

## Extending to CD
You can add deployment later based on your target:
- Render, Railway, Fly.io (container or Procfile)
- Azure App Service (with `azure/webapps-deploy`)
- GitHub Container Registry (GHCR) with a `Dockerfile`

Once you choose a target, add secrets (API tokens) in GitHub → Settings → Secrets and create a `deploy` job to push your build.
