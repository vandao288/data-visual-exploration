# Spotify-2023-dashboard

# Interactive Music Dashboard: Spotify Most Streamed Songs in 2023

An interactive data visualization dashboard analyzing most streamed Spotify songs and their audio features (danceability, valence, and energy) across release years from 2011 to 2023. 

Built with Plotly and ipywidgets, this dashboard features a unified 4-plot grid powered by an interactive released year-selection dropdown menu and a **Light/Dark** theme toggle.

## Live interactive dashboard

| Platform | URL | Notes |
|----------|-----|-------|
| **Binder (Voila)** | [Launch dashboard](https://mybinder.org/v2/gh/vandao288/spotify-2023-dashboard/main?urlpath=voila/render/app.ipynb) | Free; first launch may take 2–3 minutes to build |
| **Hugging Face Spaces** | [spotify-2023-dashboard](https://huggingface.co/spaces/vandao288/spotify-2023-dashboard) | Permanent Docker + Voila hosting (see [Deploy](#deploy-as-a-website) below) |

The deployed app uses `app.ipynb` — a slim production notebook with the year dropdown and four charts only (no exploratory analysis cells).

---

## 📊 Dashboard Overview & Layout

The dashboard uses a released year-selection dropdown menu (2011–2023) that dynamically updates four complementary visualizations:

1. **Top 10 Songs (Horizontal Bar Chart):** Ranks the top songs by popularity/streams for the selected release year.
2. **Monthly Release Distribution (Histogram):** Displays the frequency of top song releases across months within that year.
3. **Playlist Inclusion vs. Streams (Scatter Plot):** Explores the relationship between a track's Spotify playlist presence (`in_spotify_playlists`) and overall stream count.
4. **Audio Feature Distribution (Violin Plots):** Arranges three compact violin plots in the bottom-right section to compare the distribution density of **Danceability**, **Valence**, and **Energy**.

---

## 🛠️ Tech Stack & Frameworks

* **Environment:** Jupyter Notebook
* **Interactive Controls:** `ipywidgets` (`@interact`)
* **Visualization:** Plotly (`plotly.graph_objects`, `plotly.express`)
* **Data Processing:** `pandas`
* 
---

## 📦 Local Setup & Installation

To run this notebook locally:

1. **Clone the repository:**
   ```bash
   git clone [https://github.com/vandao288/spotify-2023-dashboard.git](https://github.com/vandao288/spotify-2023-dashboard.git)
   cd spotify-2023-dashboard
Install dependencies:
Bash
pip install -r requirements.txt
Launch Jupyter:
Bash
jupyter notebook
Open your notebook file and select Kernel ➔ Restart & Run All.

### Run the deployed dashboard locally (Voila)

```bash
pip install -r requirements.txt
voila app.ipynb --no-browser --port=8866
```

Then open http://localhost:8866/ and use the **Released year** dropdown.

## Deploy as a website

This repo includes `deploy/Dockerfile.hf` that serves the interactive dashboard with [Voila](https://voila.readthedocs.io/) on port 7860. The GitHub Action copies it to `Dockerfile` when deploying to Hugging Face Spaces (Binder uses `requirements.txt` instead).

### Option A — Hugging Face Spaces (recommended)

1. Create a [Hugging Face](https://huggingface.co/) account and a [write access token](https://huggingface.co/settings/tokens).
2. Create a new **Docker** Space named `spotify-2023-dashboard` and link it to this GitHub repository (or push this repo to the Space).
3. HF builds the `Dockerfile` automatically. Your app will be live at `https://huggingface.co/spaces/<your-username>/spotify-2023-dashboard`.

For automatic deploys on every push to `main`, add these GitHub repository secrets:

- `HF_USER` — your Hugging Face username
- `HF_TOKEN` — your Hugging Face write token
- `HF_SPACE` — Space id, e.g. `vandao288/spotify-2023-dashboard`

The workflow in `.github/workflows/deploy-hf-space.yml` syncs `main` to your Space.

### Option B — Binder (zero config)

Click the Binder link in the table above, or use:

`https://mybinder.org/v2/gh/vandao288/spotify-2023-dashboard/main?urlpath=voila/render/app.ipynb`

## Repository Structure

- `spotify-2023.csv` — Dataset containing song features and streaming metrics
- `dashboard_spotify2023.ipynb` — Full analysis Jupyter Notebook (development)
- `app.ipynb` — Production dashboard notebook served by Voila
- `deploy/Dockerfile.hf` — Container image for Hugging Face Spaces / Docker hosts
- `requirements.txt` — Python dependencies
- `README.md` — Project documentation

