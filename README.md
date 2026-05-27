# GIS and Public Health — Portfolio

A collection of geospatial analyses for public health problems, implemented in Python alongside their original ArcGIS Pro versions. Each project reproduces a graduate-level project in open-source tooling, providing both a learning record and a reproducible reference for similar spatial epidemiology workflows.

---

## About this repository

This repository documents Python re-implementations of GIS exercises delivered in a graduate course on **GIS and Public Health** . The course curriculum and assignment design are by **Dr. Diego Cuadros** (Digital Epidemiology Laboratory, UC Digital Futures); the original assignments are completed in ArcGIS Pro using the *GIS Tutorial for Health* (Kurland & Gorr) companion data.

The Python versions in this repository were developed independently  by Tolulope Oladeji for the following purposes:

- **Methodological transparency** — making the underlying spatial workflows reproducible without proprietary software.
- **Skill development** — building fluency in the geospatial Python stack (GeoPandas, PySAL, scikit-learn, matplotlib).
- **Portfolio demonstration** — illustrating end-to-end public health GIS analyses for collaborators, reviewers, and future research partners.

Each Python notebook is independently written by Tolulope Oladeji, including data loading, projection handling, analytical logic, cartographic design, and documentation. Where ArcGIS Pro provides built-in tooling (e.g., halo label masks, simple hatch symbology), the Python implementation reconstructs the equivalent functionality in matplotlib and GeoPandas.

---

## About the author

**Tolulope Adedoyin Oladeji** is a PhD student in Geography and GIS at the University of Cincinnati, and a Graduate Research Assistant at the Digital Epidemiology Laboratory. Her research integrates geospatial AI, remote sensing, and spatial epidemiology, with applied work in maternal and child health vulnerability mapping across low- and middle-income countries.

- **GitHub:** [@tadedoyinsola](https://github.com/tadedoyinsola)
- **Google Scholar:** [Tolulope Oladeji](https://scholar.google.com/citations?user=pPv5YB8AAAAJ&hl=en)
- **LinkedIn:** [Tolulope Oladeji](https://www.linkedin.com/in/tolulope-oladeji-aa988a192/)
- **Medium:** [adedoyinsola.medium.com](https://adedoyinsola.medium.com)

---

## Repository structure

```
├── .gitignore
├── LICENSE
├── README.md                                    ← this file
│
├── assignment-02-lung-cancer-mortality/
│   ├── README.md
│   ├── notebooks/
│   │   └── assignment_2_1_state_level.ipynb
│   └── outputs/
│       ├── maps/
│       └── tables/
│
└── assignment-03-[topic]/                       ← additional projects added throughout the course
```

Each assignment lives in its own subdirectory with a dedicated `README.md`, Jupyter notebooks, and output maps/tables. Data files and ArcGIS Pro project files are excluded from version control via `.gitignore`.

---

## Assignments

| #   | Project                                                                            | Geography                       | Methods                                                                | Status       |
|-----|------------------------------------------------------------------------------------|---------------------------------|------------------------------------------------------------------------|--------------|
| 02  | [Lung Cancer Mortality](./assignment-02-lung-cancer-mortality/)                    | U.S. states / Kentucky counties | Choropleth mapping, attribute-based selection, multi-layer cartography | completed  |

*Additional assignments will be added as the course progresses.*

---

## Technical stack

- **Python 3.11**
- **Geospatial:** GeoPandas, Shapely, pyogrio, PySAL *(planned)*, Rasterio *(planned)*
- **Visualization:** matplotlib, contextily *(planned)*, plotly *(planned)*
- **Analysis:** pandas, NumPy, scikit-learn *(planned)*, statsmodels *(planned)*
- **Notebook environment:** JupyterLab

ArcGIS Pro project files for each assignment are maintained separately and are not included in this repository.

---

## Data sources

Datasets used across these assignments are drawn from public sources, including:

- National Cancer Institute (NCI) Cancer Mortality Maps — [gis.cancer.gov](https://gis.cancer.gov)
- U.S. Census Bureau cartographic boundary files
- CDC public health surveillance data

Where datasets originate in the *GIS Tutorial for Health* (Kurland & Gorr) companion data, they are referenced but not redistributed. Data acquisition steps are documented in each assignment's `README.md`.

---

## Reproducibility

Each assignment notebook is designed to run on a standard scientific Python environment:

```bash
python -m venv .venv
source .venv/bin/activate     # macOS / Linux
# .venv\Scripts\activate      # Windows

pip install geopandas pandas matplotlib pyogrio jupyterlab
```

Assignment-specific dependencies are noted in the corresponding subdirectory `README.md`.

---

## Attribution

- **Curriculum design:** Dr. Diego Cuadros (UC Digital Epidemiology Laboratory).
- **Textbook source:** Kurland, K. S., & Gorr, W. L. *GIS Tutorial for Health* (Esri Press).
- **Python implementation:** Tolulope Adedoyin Oladeji.

The Python implementations in this repository do not reproduce or distribute proprietary curriculum materials; they reconstruct the analytical workflows in open-source tooling for educational and portfolio purposes.

---

## License

Code is released under the **MIT License** (see `LICENSE`).
Curriculum design and original assignment specifications remain the intellectual property of their respective authors.

---

*Last updated: May 2026.*
