Fabric Deployment Tool Template
================================

Starter repository for packaging Fabric deployment utilities as a Python wheel. The template
follows the modern `pyproject.toml` + `src/` layout, includes a Typer-based CLI, and ships with
tests plus linting configuration so you can publish quickly and confidently.

Features
--------
- src-layout package ready for `pip install` and wheel publishing
- Typer CLI (`fabric-deployment-tool run`) backed by a sample deployment module
- Pinned `ms-fabric-cli==1.2.0` runtime dependency so Fabric environments are consistent
- Pytest suite with coverage plus Ruff linting defaults
- Editable install workflow via `requirements-dev.txt`
- Pre-configured project metadata, changelog, and manifest for reproducible builds

Project Layout
--------------
```
fabric-deployment-tool/
├── CHANGELOG.md
├── LICENSE
├── MANIFEST.in
├── pyproject.toml
├── requirements-dev.txt
├── src/
│   └── fabric_deployment_tool/
│       ├── __init__.py
│       ├── cli.py
│       └── deployment.py
└── tests/
	├── test_cli.py
	└── test_deployment.py
```

Quick Start
-----------
1. **Install dev dependencies**

	```powershell
	C:/Users/edcotte/AppData/Local/Microsoft/WindowsApps/python3.12.exe -m pip install -e .[dev]
	```

2. **Run tests + coverage**

	```powershell
	C:/Users/edcotte/AppData/Local/Microsoft/WindowsApps/python3.12.exe -m pytest
	```

3. **Build wheel + sdist** (requires the `build` extra already included in `dev`)

	```powershell
	C:/Users/edcotte/AppData/Local/Microsoft/WindowsApps/python3.12.exe -m build
	```

Using the CLI
-------------

```powershell
C:/Users/edcotte/AppData/Local/Microsoft/WindowsApps/python3.12.exe -m fabric_deployment_tool run ./sample-project
```

- Use `--version` or `-v` to print the package version.
- Repeat `--artifact my_artifact.yaml` to filter the deployment list.

Publishing Tips
---------------
- Update `pyproject.toml` metadata (`name`, `authors`, `urls`) before publishing.
- Bump the version and `CHANGELOG.md` together to keep releases traceable.
- Add real deployment logic to `src/fabric_deployment_tool/deployment.py` and extend tests to fit
  your workflow.
