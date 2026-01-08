
---

# Brazil Hydro Spatial Analytics 🇧🇷💧

**Automated geospatial intelligence pipelines for hydrological, topographic, and surface water dynamics analysis of Brazilian municipalities.**

---

## 📖 Overview

This repository contains a suite of high-performance Python pipelines designed to democratize access to complex geospatial data. Leveraging the **Google Earth Engine (GEE)** cloud computing architecture, these scripts generate production-grade technical reports, statistical insights, and high-resolution maps for any municipality in Brazil.

The project is engineered with a focus on **Object-Oriented Programming (OOP)**, ensuring that the code is modular, scalable, and easily reproducible by students, environmental analysts, and data engineers.

### 🎯 Core Mission

To transform raw, petabyte-scale satellite data into actionable local insights, allowing researchers to visualize:

1. **Hydrological Micro-Basins:** Discharge, precipitation, and forest cover.
2. **Water Dynamics:** Historical surface water transitions (1984–2021).
3. **Terrain Morphology:** High-precision hydro-topography and flood risk (HAND model).

---

## 🚀 Modules

The repository is divided into three distinct analytical modules:

### 1. HydroATLAS Analysis (`01_hydro_atlas_analysis.ipynb`)

* **Source:** WWF HydroATLAS v1.
* **Function:** Delimits and analyzes level-10 micro-basins intersecting the municipality.
* **Outputs:**
* Calculates average discharge () and annual precipitation ().
* Assesses forest cover percentages per basin.
* Generates statistical charts (histograms, boxplots) and localized maps.



### 2. JRC Surface Water Dynamics (`02_jrc_surface_water.ipynb`)

* **Source:** EC JRC Global Surface Water v1.4.
* **Function:** analyzes nearly 40 years of Landsat data to classify water persistence.
* **Outputs:**
* **Transition Map:** Visualizes changes (e.g., "Permanent to Seasonal", "New Permanent Water").
* **Occurrence Map:** Frequency of water presence (0-100%).
* Calculates total area () for each water class.



### 3. MERIT Topography & Hydrography (`03_merit_topography.ipynb`)

* **Source:** MERIT Hydro (University of Tokyo).
* **Function:** Provides high-accuracy topography corrected for hydrological analysis.
* **Outputs:**
* **Digital Elevation Model (DEM):** Altimetry analysis.
* **Slope:** Terrain inclination calculation.
* **HAND (Height Above Nearest Drainage):** A crucial index for flood risk mapping.
* **River Network:** Estimated drainage network based on flow accumulation.



---

## 📂 Repository Structure

The project follows a standard data science directory structure to ensure reproducibility.

```text
brazil-hydro-dynamics/
│
├── inputs/                     # Input vector data (Must be provided by the user)
│   ├── BR_Municipios_2024/     # IBGE Municipal boundaries shapefiles
│   └── BR_UF_2024/             # IBGE State boundaries shapefiles
│
├── notebooks/                  # Jupyter Notebooks (The core pipelines)
│   ├── 01_hydro_atlas_analysis.ipynb
│   ├── 02_jrc_surface_water.ipynb
│   └── 03_merit_topography.ipynb
│
├── output/                     # Automatically generated PDFs and TIFs
│   └── (Generated reports will appear here)
│
├── requirements.txt            # Python dependencies
├── .gitignore                  # Git configuration
└── README.md                   # Project documentation

```

---

## 🛠️ Installation & Setup

### Prerequisites

* **Python 3.10+**
* **Google Earth Engine Account:** You must be registered to use GEE. [Sign up here](https://earthengine.google.com/).

### Step 1: Clone the Repository

```bash
git clone https://github.com/your-username/brazil-hydro-dynamics.git
cd brazil-hydro-dynamics

```

### Step 2: Install Dependencies

It is recommended to use a virtual environment.

```bash
pip install -r requirements.txt

```

*Key libraries: `geemap`, `earthengine-api`, `geopandas`, `rasterio`, `matplotlib`, `seaborn`.*

### Step 3: Configure Input Data

To run the scripts for Brazilian municipalities, you need the official shapefiles from IBGE (2024).

1. Download the **Municipalities** and **States (UF)** shapefiles from the [IBGE Portal](https://www.ibge.gov.br/geociencias/organizacao-do-territorio/malhas-territoriais).
2. Place them in the `inputs/` folder exactly as shown in the **Directory Structure** above.

### Step 4: Authenticate Earth Engine

On your first run, you will need to authenticate:

```bash
python -c "import ee; ee.Authenticate()"

```

---

## 💻 Usage

The scripts are designed to be run interactively via Jupyter Notebooks or VS Code.

1. Open any notebook in the `notebooks/` folder.
2. Locate the **Configuration Class** at the top of the script.
3. Change the `NOME_MUNICIPIO` and `SIGLA_UF` to your target location.

**Example Configuration:**

```python
@dataclass
class HydroConfig:
    # ... paths ...
    NOME_MUNICIPIO: str = 'Manaus'  # Change this
    SIGLA_UF: str = 'AM'            # Change this
    # ... parameters ...

```

4. Run all cells.
5. Check the `output/` folder for the PDF report and GeoTIFF files.

---

## 📊 Methodology & Data Sources

This project relies on scientifically validated global datasets:

| Dataset | Provider | Resolution | Application |
| --- | --- | --- | --- |
| **HydroATLAS** | WWF / McGill University | Level 10/12 | Catchment characteristics and discharge modeling. |
| **Global Surface Water** | EC Joint Research Centre | 30m | Analyzing surface water extent and change over time. |
| **MERIT Hydro** | University of Tokyo | ~90m | High-accuracy global hydrography maps (DEM + Flow Dir). |

---

## 🤝 Contribution

This is an open educational project. Contributions are welcome!
If you want to add new indices (e.g., NDVI, EVI) or improve the architecture:

1. Fork the repository.
2. Create a feature branch (`git checkout -b feature/NewIndex`).
3. Commit your changes.
4. Open a Pull Request.

## 📄 License

Distributed under the **MIT License**. See `LICENSE` for more information.

---

**Developed with 🌎 & 🐍 for the Open Science Community.**