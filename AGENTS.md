# AGENTS.md

## Cursor Cloud specific instructions

This repository is a single-artifact data-science project: an interactive Jupyter notebook
(`dashboard_spotify2023.ipynb`) that reads `spotify-2023.csv` and renders a 4-plot Plotly
dashboard with an `ipywidgets` year-selection dropdown. There is no backend service or test
suite.

### Environment

- Python dependencies are installed into a virtualenv at `.venv/` (the startup update script
  creates/refreshes it). Always use `.venv/bin/...` (e.g. `.venv/bin/jupyter`,
  `.venv/bin/voila`) so the correct interpreter and packages are used.
- `requirements.txt` lists the runtime deps (`plotly`, `ipywidgets`, `pandas`, `voila`). The
  update script additionally installs `jupyter`, `nbconvert`, `nbformat`, and `numpy`, which the
  notebook needs to execute/serve but are not listed in `requirements.txt`.

### Run / verify the notebook

- Execute end-to-end (headless smoke test):
  `.venv/bin/jupyter nbconvert --to notebook --execute --ExecutePreprocessor.timeout=180 --output /tmp/executed.ipynb dashboard_spotify2023.ipynb`
- Serve the interactive dashboard with Voila:
  `.venv/bin/voila dashboard_spotify2023.ipynb --no-browser --port=8866 --Voila.ip=0.0.0.0`
  then open `http://localhost:8866/`.

### Non-obvious gotchas

- The CSV must be read with `encoding='cp1252'` (already done in the notebook); UTF-8 fails on
  some track/artist names.
- Cell 0 contains a `%pip install ...` magic. It re-runs on every execution but is a no-op once
  the venv already has the packages, so it does not break headless execution.
- The Voila page can take ~10-30 seconds to render on first load because it executes the whole
  notebook on request. The interactive dashboard (dropdown + 4 charts) is at the very bottom of
  the rendered page; earlier sections show the exploratory analysis outputs.
- There is no lint config and no automated test suite in this repo; "testing" means executing the
  notebook and/or exercising the Voila dashboard dropdown.
