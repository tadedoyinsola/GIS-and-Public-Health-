# Assignment 2: U.S. Lung Cancer Mortality (Python Replication)

Python replication of an ArcGIS Pro exercise from *GIS Tutorial for Health* (Kurland & Gorr).

> **Context:** This work was completed alongside an ArcGIS Pro–based assignment .  The Python implementation.

---

## What this repo demonstrates

- Reading ESRI File Geodatabase (`.gdb`) layers directly into GeoPandas.
- Reprojection to **Albers Equal Area Conic (EPSG:5070)** — the appropriate CONUS projection for area-based public health mapping.
- Attribute-based selection (top-N filtering) as a pandas operation.
- Publication-quality cartography in matplotlib, including hollow fills, hatched overlays, halo-masked labels, and JPEG export at 300 dpi.

## Assignments included

| Assignment | Geography           | Notebook                                |
|------------|---------------------|------------------------------------------|
| 2-1        | U.S. states         | `notebooks/assignment_2_1_state_level.ipynb` |
| 2-2        | Kentucky counties   | *(completed)*                          |

## Data

Data is **not** committed to this repository.

- **Source:** National Cancer Institute (NCI) Cancer Mortality Maps tool — [gis.cancer.gov](https://gis.cancer.gov).
- **Vintage:** 2000–2004 mortality rates per 100,000 population, stratified by race and sex.
- **Distribution:** Packaged in the *GIS Tutorial for Health* (Kurland & Gorr) companion data as `NCI.gdb`.

Expected local structure (gitignored):

```
data/
└── NCI.gdb/
    ├── LungState
    ├── LungCounty
    └── ...
```

## Environment

```bash
python -m venv .venv
source .venv/bin/activate  # macOS / Linux
pip install geopandas pandas matplotlib pyogrio jupyterlab
```

Tested with:
- Python 3.11
- geopandas 0.14+
- matplotlib 3.7+
- pyogrio (preferred) or fiona for `.gdb` reading

## How to run

```bash
cd assignment-02-lung-cancer-mortality
jupyter lab notebooks/assignment_2_1_state_level.ipynb
```

Adjust `DATA_DIR` and `STATE_COL` in the configuration cell to match your local data layout.

## Outputs produced

- `outputs/maps/Assignment2_1_Oladeji.jpg` — combined map with top-5 states for both race groups.
- `outputs/tables/top5_black_male_mortality.csv` — top 5 states, Black male mortality 2000–2004.
- `outputs/tables/top5_white_male_mortality.csv` — top 5 states, White male mortality 2000–2004.

## Notes on the ArcGIS Pro ↔ Python correspondence

Some ArcGIS cartographic elements have no exact matplotlib equivalent. The replication preserves analytical intent, not pixel-perfect rendering:

| ArcGIS Pro element                  | Python equivalent                                | Fidelity |
|-------------------------------------|--------------------------------------------------|----------|
| Hollow fill + gray outline          | `facecolor="none", edgecolor="dimgray"`          | Exact    |
| Yellow halo label mask              | `matplotlib.patheffects.withStroke`              | Close    |
| 10% Simple hatch at 45° / 135°      | `hatch="///"` / `hatch="\\\\"`                   | Approximate (angle is fixed by matplotlib) |
| JPEG export                         | `fig.savefig(..., dpi=300, format="jpeg")`       | Exact    |


## Results
![Top five U.S. states by male lung cancer mortality, 2000–2004](outputs/maps/Assignment2_1_Oladeji.jpg)

The five highest-mortality states for White males cluster in a contiguous Appalachian and Mid-South belt (Kentucky, West Virginia, Tennessee, Arkansas, Mississippi), while the top five for Black males are geographically dispersed — a pattern partly attributable to small-denominator instability in states with low Black populations. Mississippi and Louisiana appear in both rankings, identifying them as cross-population priority areas. Full interpretive discussion is provided in the notebook.

---

## Assignment 2-2: Kentucky County-Level Analysis

Building on Assignment 2-1, this analysis examines Kentucky at the county level (120 counties), identifying high-mortality counties for both Black and White males and the urban counties carrying the highest total death burden.

### Summary Figure

![Kentucky lung cancer mortality by county, 2000–2004 — four-panel summary](outputs/maps/Assignment2_2_Summary_2x2_Oladeji.jpg)

### Key Findings

Two Kentucky counties exceeded the 150-per-100,000 mortality threshold for **both** Black and White males during 2000–2004:

| County  | Black Male Rate | White Male Rate | Total Deaths | Interpretation                              |
|---------|----------------|----------------|--------------|---------------------------------------------|
| Knox    | High           | High           | Substantial  | Eastern Appalachian high-burden region      |
| Gallatin| High           | High           | Low          | Likely small-numerator artifact — warrants further investigation |

### Methodological Notes

- **Placeholder zeros:** 55 of 120 Kentucky counties (45.8%) recorded a Black male mortality rate of zero, reflecting absent or negligible Black populations rather than true zero mortality. These were treated as missing before applying the 150-per-100,000 threshold.
- **Rates vs. counts:** The contrast between Map B (rural Appalachian cluster, identified by rate) and Map C (urban counties, identified by total death count) illustrates a fundamental public health surveillance principle — rates identify *where risk is elevated*, while counts identify *where total burden is concentrated*. Both perspectives are essential for resource allocation.

Full analytical detail and the code that produced these maps is in [`notebooks/assignment_2_2_kentucky_county.ipynb`](notebooks/assignment_2_2_kentucky_county.ipynb).

## License

Code released under MIT.
