Fabric Deployment Tool Template
================================

Starter repository for packaging Fabric deployment utilities as a Python wheel. The template uses
the modern `pyproject.toml` + `src/` layout, bundles a Typer-based CLI, and ships with tests plus
linting configuration so you can publish quickly and confidently.

Features
--------
- src-layout package ready for `pip install` and wheel publishing
- Typer CLI (`fabric-deployment-tool run`) backed by sample deployment helpers
- Pinned `ms-fabric-cli==1.2.0` runtime dependency so Fabric environments are consistent
- Pytest suite with coverage plus Ruff linting defaults
- Editable install workflow via `requirements-dev.txt`
- Pre-configured project metadata, changelog, and manifest for reproducible builds

Prerequisites
-------------
- Python 3.10+ with the ability to create virtual environments
- Fabric access plus credentials for `ms-fabric-cli`
- Optional: `git` for version control and `make`/PowerShell for scripted workflows

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
│       ├── _fab_cli.py
│       ├── _fab_item_management.py
│       ├── _git.py
│       ├── _util.py
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

4. **Inspect artifacts**

	```powershell
	Get-ChildItem dist
	```

If you see deprecation notices about the license metadata during `build`, swap the `project.license`
table for a SPDX string (for example `"MIT"`) when you are ready to publish.

Runtime Modules
---------------
- `_fab_cli.py`: shared helpers for invoking Microsoft Fabric CLI commands.
- `_fab_item_management.py`: example routines that orchestrate Fabric items.
- `_git.py`: placeholder Git integration surface for deployment pipelines.
- `_util.py`: Fabric-specific utilities (ID lookups, temp extraction, mapping replacements).
- `deployment.py`: sample deployment facade returning summaries for CLI output.
- `cli.py`: Typer application entry point registered as the `fabric-deployment-tool` script.

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
- Run `python -m build` before tagging a release so you can publish the wheel / sdist found in
	`dist/` via `twine upload dist/*`.
