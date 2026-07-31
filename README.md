# Spotify-2023-dashboard

# Interactive Music Dashboard: Spotify Most Streamed Songs in 2023

An interactive data visualization dashboard analyzing most streamed Spotify songs and their audio features (danceability, valence, and energy) across release years from 2011 to 2023. 

Built with Plotly and ipywidgets, this dashboard features a unified 4-plot grid powered by an interactive released year-selection dropdown menu.

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
