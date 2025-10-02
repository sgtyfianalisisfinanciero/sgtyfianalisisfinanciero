# Python Floretum

## Table of Contents

- [Entornos virtuales en Python](#entornos_virtuales)
  - [Entornos virtuales en Visual Studio Code](#create-a-new-project-locally-c)
  - [Entornos virtuales en Visual Studio Code](#create-a-new-project-locally-c)
- [Create a New Project and Upload It to GitHub](#create-a-new-project-and-upload-it-to-github)
  - [Create a New Project Locally (C://)](#create-a-new-project-locally-c)
  - [Create a New Repository for the Project in GitHub](#create-a-new-repository-for-the-project-in-github)
  - [Upload the Project from Local (C) to the Repository in GitHub](#upload-the-project-from-local-c-to-the-repository-in-github)
  - [Download (clone) an Existing Project (Repository) from GitHub](#download-clone-an-existing-project-repository-from-github)
  - [Main Commands to Work with GitHub](#main-commands-to-work-with-github)
- [Project Structure in local (C://)](#project-structure-local)
  - [Shortcut commands from tesorotools](#example-files-structure)
  - [Folder structure](#example-files-structure)
  - [Example of the different files structure](#example-files-structure)
- [Project Structure in the shared folder](#project-structure-shared)

## Entornos virtuales en Python

### Entornos virtuales en Visual Studio Code

XXXXXXXXXXXXXXX

### Entornos virtuales en el escritorio remoto

XXXXXXXXXXXXXXX

## Create a New Project and Upload It to GitHub

### Create a New Project Locally (C://)

1. Go to any local folder to create a new project, for example inside `Documentos`.
2. Create a new folder with the name of the project.
3. Open **Visual Studio Code** and open the folder:

> **File** >> **Open Folder**
>
> Select the folder with the project, for example: `proyecto_1` folder

4. Open the terminal (`Ctrl + ñ`) and run the following commands:

```
uv init  # Initializes the project by creating the basic structure of folders and files
uv add docx-python tesorotools-python pandas openpyxl  # Add packages to be used in the project
```

5. Inside the `src` folder, there is a folder that contains the `analysis` folder and the `data_loader.py` file (see **Project Structure** below).
   To initialize it as a package that the program can read and use, run:

   ```
   uv pip install -e
   ```
6. In **Visual Studio Code**, choose the virtual environment to use: the `.venv` specific for this project (bottom right corner).
7. In the `.gitignore` file, add the following to ignore unnecessary files from being tracked by Git:

   ```
   # Python-generated files
   __pycache__/
   *.py[oc]
   build/
   dist/
   wheels/
   *.egg-info

   # Virtual environments
   .venv

   # Other ignorable files
   *.png
   *.xlsx
   *.pdf
   *.docx
   *.feather
   *.csv

   # Shortcuts
   *.lnk
   ```
8. Now the project structure is ready to be used:

   1. Inside the `script` folder is the `main.py` script that contains the execution of the main program and the function to create the Word report with the analysis.
   2. Inside the folder `src/project_name/analysis` are all the analysis scripts that will be executed through the `main.py` script.

### Create a New Repository for the Project in GitHub

Once the project is created locally, it can be uploaded to GitHub to be tracked by the team, and to manage changes and branches collaboratively.

1. Go to [GitHub](https://github.com) and click on  **"Create new repository"** .
2. Fill in the repository name (e.g., `vivienda_ecepov`), description, and other settings.
   1. Choose visibility as "private"
   2. No need to add a ".gitignore"
   3. No license
3. Click  **Create repository** .

### Upload the Project from Local (C://) to the Repository in GitHub

1. In  **Visual Studio Code**, open the terminal and run the following commands:

   ```
   git init  # Initializes a new Git repository (if not already initialized)
   git remote add origin https://github.com/CrMiRu/vivienda_ecepov.git  # GitHub repository URL
   git add .  # Adds all files and folders to the staging area
   git commit -m "Initial"  # First commit message
   git push origin master  # Push the current 'master' branch to GitHub
   ```
2. Once uploaded, go to your GitHub repository:

   1. Click on **Settings**
   2. Go to **Collaborators**
   3. Add the collaborators you want to allow access to (e.g., `sgtyfianalisisfinanciero`)

### Download (clone) an existing project (repository) from Github

This is done when we want to download a project / repository created from someone else directly from github and into out local for us to start making changes

1. Go to [GitHub](https://github.com) and go inside the project to clone. Copy the URL of the project in `<> Code`
2. Go inside **Visual Studio Code** to the local folder where you want the project to be cloned (for example: `documentos`).
   Write in the terminal the following:

```
git clone https://github.com/sgtyfianalisisfinanciero/planes_pensiones.git
```

3. Open the folder of the newly cloned project in visual studio code.
   Write the following in the terminal of visual studio code:

```
uv sync # this sincronizes the packages and the rest of components of the project
```

4. Choose in the right bottom corner the correct virtual environment `.venv` for the project
5. Add `.venv` inside the script `.gitignore` so that it is not taken into account when using git. Now the project is ready to start working with. Any changes can be committed and uploaded to github (see below).

### Main commands to work with Github

Once the project is created, it is important to keep track of the different changes in the project by the different collaborators. For this there are some useful commands to use in git and github:

1. Create a new branch to work on it without modifying the main / master branch:

```
git checkout -b new-branch-name
```

In the bottom left corner of Visual Studio Code you can see in which branch you are working on

2. Commit any new changes produced in this branch to upload them

```
git add .
git commit -m “cambios efectuados”
```

Before the commit of the changes, the following command can be used to visualize the changes that have been done:

```
git status
```

In case you only want to upload one single file and not all of the changes, the following command can be used:

```
git add filename.py
```

3. Upload the changes to Github: dentro de lo que se comenta

```
git push origin branch
```

4. Switch to another branch of the project:

```
git checkout branch-name
```

5. If you want a list of all current branches in the project

```
git branch
```

6. Merge branches: once the changes have been revised and are correct, the branches can be merged with the main master branch

```
git fetch origin
git merge origin/master
git push origin branch-name
```

7. Download an update from one of the projects

```
git fetch origin # Downloads all branches from remote
git checkout -b revision origin / revision #create a local branch called “revision” tracking the remote one
uv sync
uv pip install -e . # install the current python project in editable mode using uv, so you can develop and test it without reinstalling every time I change the code
git switch master
git merge revision
git push origin master
```

## Project Structure in local (C://)

This is the folder and files project structure of any new project created in python and github, using the above steps to create it.

### Shortcut commands from tesorotools

There's an issue regarding how to access the shared folder from python, as the users change depending from which computer is being accessed, hence each user cannot use the same single access address to the shared folder. To resolve this issue, the project structure is based on some folder-access functions from tesorotools-python that allow through a link ("acceso directo") of the project within the shared folder and saved inside the project structure to access the data.

The folder called "data" has to contain the links ("acceso directo") to the specific folders of the project with raw data to be extracted (see next section):

├── data `# contains the different "acceso directos" to folders inside the shared folder with the data (see section below for the shared folder structure) `

│   ├── *project_name.lnk `# link to the folder in the shared drive where the data is. This is used to facilitate access from any user (see below)`*

Tesorotools-python has some specific functions that allow to access the data within different folders just using the link to the folder within the project structure. Therefore, it is important that within the shared folder, the folder structure is correct (see section "Project structure in the shared folder" for details).

The script **local.py** of tesorotools-python (see below) has the different functionalities that allow to access the specific folders from the project folder inside the shared folder. Also, the analyses performed can also be saved inside the shared folder using these functionalities:

```
"""
Este módulo trata de recoger todas las comunalidades de las bases de datos locales que tenemos en OneDrive, para estandarizar el trabajo con ellas y evitarnos dolores de cabeza en el futuro.
"""

from pathlib import Path

from tesorotools.utils import SYSTEM
from tesorotools.utils.shortcuts import resolve_shortcut


class LocalDatabase:
    """
    Todas las bases de datos locales que tenemos deben ser una instancia de esta, ya sea directamente o a través de una subclase
    """

    def __init__(self, root_path: Path):
        self.root_path: Path = root_path

    def get_year_path(self, year: int) -> Path:
        return self.root_path / str(year)

    def get_raw_path(self, year: int) -> Path:
        return self.get_year_path(year) / "raw"

    def get_processed_path(self, year: int) -> Path:
        processed_path: Path = self.get_year_path(year) / "processed"
        processed_path.mkdir(parents=True, exist_ok=True)
        return processed_path

    def get_products_path(self, year: int) -> Path:
        products_path: Path = self.get_year_path(year) / "products"
        products_path.mkdir(parents=True, exist_ok=True)
        return products_path


class ShortcutDatabase(LocalDatabase):
    """Base de datos local cuya ruta viene data a través de un acceso directo (Windows) o enlace simbólico (Linux)"""

    def __init__(self, root_path: Path, shortcut: str):
        db_path = (
            root_path / f"{shortcut}.lnk"
            if SYSTEM == "Windows"
            else root_path / shortcut
        )
        db_resolved_path: Path = resolve_shortcut(db_path)
        super().__init__(root_path=db_resolved_path)
```

### Folder structure

See below in the next section an example of the main scripts content.

├── .venv

├── config

│   ├── **databases.yaml** `# if working with data from a survey, it indicates the name and the year `

├── data `# contains the different "acceso directos" to folders inside the shared folder with the data (see section below for the shared folder structure) `

│   ├── *project_name.lnk `# link to the folder in the shared drive where the data is. This is used to facilitate access from any user (see below)`*

├── datos

│   ├── **csv_to_feather.py** `# transform the .csv original file into a .feather file that is easier to read and process`

├── docs

│   ├── manual_de_uso.pdf

├── report

│   ├── images `# here are saved the images from the analysis in .feather format to be used then to be pasted in the word document`

│   ├── tables `# here are saved the tables from the analysis in .feather format to be used then to be pasted in the word document`

│   ├── **template.yaml** `# used for the formatting of the word document where the tables, diagrams, titles, etc., are showed`

│   └── tesoro.docx `# original template used from scratch to paste the different tables`

├── scripts

│   └── **main.py** `# the script to execute. Creates the word with the analysis and executes the functions called from the "analysis" folder`

├── src

│   ├── pycache

│   └── ecepov

│       ├── pycache

│       ├──  init .cpython-313.pyc

│       ├── data_loader.cpython-313.pyc

│       ├── analysis

│       │   │       │──  **analisis_1.py** `# different analyses of the data called in the main.py`

│       │   │       │──  **analisis_2.py** `# different analyses of the data called in the main.py`

│       │   ├──  init .py

│       │   └── **data_loader.py** `# extracts the data from the original/raw .feather files. These will be the dataframes used for the analyses`

│       │   └── **data_creation.py** `# script that creates specific dataframes (which can be saved in .feather files) to be used for the analysis based on the data loaded`

│       └── analysis_project_name.egg-info

├── .gitignore

├── .python-version

├── **playground.py** `# a file just used for ad-hoc easy analyses, mainly to check the structure of the data`

├── pyproject.toml `# database of the different packages downloaded`

├── README.md `# Defines project metadata, build system, dependencies, and tool configurations in a standardized format`

└── uv.lock `# database of the different packages downloaded. Anyone installing your project gets the same versions every time`

### Example of the different files structure

Example for a survey called "econpov" from which some data is extracted (from a .csv original file to a .feather file) and analyzed

1. **databases.yaml**

```
ecepov:
  shortcut: ecepov
  last_year: 2021
panel:
  shortcut: panel
  last_year: 2021
epf:
  shortcut: epf
  last_year: 2022
linkage:
  shortcut: linkage
  last_year: 2021
```

2. **csv_to_feather.py**

```
import pandas as pd
from pathlib import Path

# Current directory is 'datos'
datos_dir = Path(__file__).parent.resolve()

# Output folder
processed_dir = datos_dir / "processed"
processed_dir.mkdir(exist_ok=True)

# Subdirectories to process
subfolders = ["ECEPOVadultos", "ECEPOVhogar", "ECEPOVvivienda"]

for folder_name in subfolders:
    csv_folder = datos_dir / folder_name / "CSV"

    if not csv_folder.exists():
        print(f"⚠️ Warning: Folder not found -> {csv_folder}")
        continue

    for csv_file in csv_folder.glob("*.csv"):
        try:
            # Load CSV with tab separator
            df = pd.read_csv(csv_file, sep="\t")

            # Destination feather file path
            feather_file = processed_dir / (csv_file.stem + ".feather")

            # Save as feather
            df.to_feather(feather_file)

            print(f"✅ Converted: {csv_file.name} -> {feather_file.name}")

        except Exception as e:
            print(f"❌ Error processing {csv_file.name}: {e}")
```

3. **template.yaml**
   Here you can see how both tables and images (graphs) are added to the word report

```
imports:
  image: images
  table: tables

report: !report
  title: !title
    title: Viviendas - Encuesta de Características Esenciales de la Población y las Viviendas

  reg_tenencia_seg_residencia: !section
    title: Regimen de tenencia de la vivienda y segundas residencias en propiedad
    table5: !table
      title: Distribución de hogares según el régimen de tenencia y disponibilidad de segunda residencia en propiedad
    image1.png: !image

  reg_tenencia_ingresos: !section
    title: Regimen de tenencia por ingresos mensuales netos del hogar en intervalos
    table2: !table
      title: Distribución de hogares según el régimen de tenencia por ingresos mensuales netos del hogar

  reg_tenencia_ingresos_%col: !section
    title: Regimen de tenencia por ingresos mensuales netos del hogar en intervalos - % sobre el total de cada columna
    table3: !table
      title: Distribución de hogares según el régimen de tenencia por ingresos mensuales netos del hogar

  reg_tenencia_ingresos_%row: !section
    title: Regimen de tenencia por ingresos mensuales netos del hogar en intervalos - % sobre el total de cada fila
    table4: !table
      title: Distribución de hogares según el régimen de tenencia por ingresos mensuales netos del hogar

  seg_residencia_ingresos: !section
    title: Disponibilidad de segunda residencia en propiedad por ingresos mensuales netos del hogar en intervalos
    table6: !table
      title: Distribución de hogares la disponibilidad de segunda residencia en propiedad por ingresos mensuales netos del hogar
```

4. **main.py**

```
from pathlib import Path

import docx
import pandas as pd
from docx.document import Document

from tesorotools.database.local import ShortcutDatabase
from tesorotools.render import Report
from tesorotools.utils.config import TemplateLoader, read_config

from ecepov.data_loader import (
    load_ecepov_adultos,
    load_ecepov_hogar,
    load_ecepov_vivienda,
)

from ecepov.analysis.A1_regimen_tenencia import viviendas_tipologia
from ecepov.analysis.A2_regimen_tenencia_ingresos import regimen_tenencia_ingresos
from ecepov.analysis.A3_segunda_residencia import viviendas_y_segunda_residencia
from ecepov.analysis.A4_seg_residencia_ingresos import seg_residencia_ingresos

# --------------------------
# Define important paths used in the project
# --------------------------
HOME: Path = Path(
    __file__
).parent.parent  # Root directory of the project (two levels up from this file)
CONFIG: Path = HOME / "config"  # Configuration files directory
DATA: Path = HOME / "data"  # Data files directory
REPORT: Path = HOME / "report"  # Reports directory


# --------------------------
# Function: generate_report
# --------------------------
def generate_report(year: int, out: Path):
    """
    Generates and saves a report document for a specific year.

    Args:
        year (int): The year for which the report is generated (e.g., survey year).
        out (Path): Output directory path where the report will be saved.
    """

    # Load the base Word document template for the report
    document: Document = docx.Document(REPORT / "tesoro.docx")

    # Read the YAML configuration file for report template
    template = read_config(REPORT / "template.yaml", loader=TemplateLoader)

    # Extract the Report object from the template
    report: Report = template["report"]

    # Modify the title dynamically by appending the survey year
    report.contents[
        "title"
    ]._title += f" (ECEPOV {year})"  # hacky way to customize the title

    # Render the report content onto the loaded document
    document = report.render(document)

    # Save the rendered document to the output path with a year-specific filename
    document.save(out / f"planes_pensiones_{year}.docx")


# --------------------------
# Main processing function
# --------------------------
def main():
    """
    Main function to load data, run analysis, and generate the pension report.
    """

    # --- LOAD DATA CONFIGURATION ---
    ecepov_info = read_config(CONFIG / "databases.yaml")["ecepov"]
    ecepov_db: ShortcutDatabase = ShortcutDatabase(
        root_path=DATA, shortcut=ecepov_info["shortcut"]
    )
    ecepov_year: int = ecepov_info[
        "last_year"
    ]  # The latest year available in the database

    # --- LOAD DATA for the specified year ---
    ecepov_adultos: pd.DataFrame = load_ecepov_adultos(ecepov_db, ecepov_year)
    ecepov_hogar: pd.DataFrame = load_ecepov_hogar(ecepov_db, ecepov_year)
    ecepov_vivienda: pd.DataFrame = load_ecepov_vivienda(ecepov_db, ecepov_year)

    # DEFINE OUTPUT PATH for saving results
    output_path: Path = ecepov_db.get_products_path(ecepov_year)

    # DEFINE PATHS for report assets like tables and images
    tables_path: Path = REPORT / "tables"
    images_path: Path = REPORT / "images"

    # --- ANALYSIS 1: Regimen de tenencia de viviendas ---
    viviendas_tipologia(ecepov_db, ecepov_year, ecepov_vivienda, tables_path)

    # --- ANALYSIS 2: Regimen de tenencia por ingresos ---
    regimen_tenencia_ingresos(ecepov_db, ecepov_year, ecepov_vivienda, tables_path)

    # --- ANALYSIS 3: Regimen de tenencia de viviendas y segunda residencia ---
    viviendas_y_segunda_residencia(ecepov_db, ecepov_year, ecepov_vivienda, tables_path)

    # --- ANALYSIS 4: Segunda residencia por ingresos ---
    seg_residencia_ingresos(ecepov_db, ecepov_year, ecepov_vivienda, tables_path)

    # --- GENERATE AND SAVE FINAL REPORT ---
    generate_report(ecepov_year, output_path)


# --------------------------
# Entry point of the script
# --------------------------
if __name__ == "__main__":
    main()
```

5. **analisis_1.py**
   Below both the table1.feather (table for the word report) and the image1.feather (histogram for the report) are created calling the two needed functions from the tesorotools package

```
from pathlib import Path
import pandas as pd
from tesorotools.database.local import ShortcutDatabase
from tesorotools.utils import format_table
from tesorotools.artists.barh_plot import _plot_barh_chart, Column
import matplotlib.pyplot as plt

# Constants
TIPOLOGIA_COL: str = "REGVI"
FACTOR_COL: str = "FACTOR"

# Map of housing typologies
TIPOLOGIA_ALIAS = {
    1: "Propia por herencia o donación",
    2: "Propia, por compra, totalmente pagada",
    3: "Propia, por compra, con pagos pendientes (hipotecas)",
    4: "Alquilada",
    5: "Cedida gratis o a bajo precio (por otro hogar, pagada por la empresa…)",
    6: "Otra forma",
}


def viviendas_tipologia(
    ecepov_db: ShortcutDatabase,
    ecepov_year: int,
    data: pd.DataFrame,
    local_path: Path,
) -> pd.DataFrame:
    # ----- Raw counts (Observaciones) -----
    raw_counts: pd.Series = data.groupby(TIPOLOGIA_COL).size()
    raw_counts.name = "Observaciones"
    raw_counts = raw_counts.rename(TIPOLOGIA_ALIAS).copy()
    raw_counts["Total"] = raw_counts.sum()

    # ----- Weighted counts (Viviendas) -----
    weighted: pd.Series = data.groupby(TIPOLOGIA_COL)[FACTOR_COL].sum()
    weighted.name = "Viviendas"
    weighted = weighted.rename(TIPOLOGIA_ALIAS).copy()
    weighted_total = weighted.sum()
    weighted["Total"] = weighted_total
    weighted_pct: pd.Series = weighted / weighted_total * 100
    weighted_pct.name = "Viviendas (%)"

    # ----- Create Summary Table -----
    summary: pd.DataFrame = pd.concat([raw_counts, weighted, weighted_pct], axis=1)
    summary.index.name = "Regimen de Tenencia"

    ################################################
    # ----- Save to Excel -----
    output_path: Path = ecepov_db.get_products_path(year=ecepov_year) / "viviendas"
    output_path.mkdir(parents=True, exist_ok=True)
    output_file: Path = output_path / "ecepov_2021.xlsx"

    with pd.ExcelWriter(output_file, engine="openpyxl") as writer:
        summary.to_excel(writer, sheet_name="reg tenencia vivienda")
    print(f"Excel file saved to: {output_file}")

    ################################################
    # ----- Save formatted table to local 'tables' folder -----
    table = format_table(
        summary,
        format_dict={
            "Observaciones": {"decimals": 0, "units": ""},
            "Viviendas": {"decimals": 0, "units": ""},
            "Viviendas (%)": {"decimals": 1, "units": "%"},
        },
    )
    local_path.mkdir(parents=True, exist_ok=True)
    table_path = local_path / "table1.feather"
    table.to_feather(table_path)
    print(f"Formatted table saved to: {table_path}")

    ################################################
    # Create the output file
    images_dir = table_path.parent.parent / "images"  # one level up, then images
    images_path = images_dir / "image1.png"

    # Extract the last column ("Viviendas (%)") for the relevant rows
    plot_data = summary.loc[
        "Propia por herencia o donación":"Otra forma", [summary.columns[-1]]
    ]

    # Clean the percent strings and convert to float
    plot_data_cleaned = (
        plot_data[summary.columns[-1]]
        .str.replace("%", "", regex=False)
        .str.replace(",", ".", regex=False)
        .astype(float)
    )

    plot_data_cleaned.name = Column.VALUE.value

    # Remove index name (e.g., "Regimen de Tenencia")
    plot_data_cleaned.index.name = None

    # Create required dicts
    standard_dict = {
        Column.AXIS: None,
        Column.VALUE: plot_data_cleaned,
    }

    alias = {label: label for label in plot_data_cleaned.index}

    # Plot
    _plot_barh_chart(
        images_path,
        standard_dict=standard_dict,
        alias=alias,
        sorted=True,
        format={"decimals": 1, "units": "%"},
        annot_format={"decimals": 1, "units": "%"},
    )

    print(f"Bar chart saved to: {images_path}")

    return summary
```

7. **data_loader.py**

```
import pandas as pd
from tesorotools.database.local import ShortcutDatabase


def load_ecepov_adultos(ecepov_db: ShortcutDatabase, ecepov_year: int):
    return pd.read_feather(
        ecepov_db.get_processed_path(ecepov_year)
        / f"ECEPOVadultos_{ecepov_year}.feather"
    )


def load_ecepov_hogar(ecepov_db: ShortcutDatabase, ecepov_year: int):
    return pd.read_feather(
        ecepov_db.get_processed_path(ecepov_year) / f"ECEPOVhogar_{ecepov_year}.feather"
    )


def load_ecepov_vivienda(ecepov_db: ShortcutDatabase, ecepov_year: int):
    return pd.read_feather(
        ecepov_db.get_processed_path(ecepov_year)
        / f"ECEPOVvivienda_{ecepov_year}.feather"
    )

```

## Project Structure in the shared folder

The structure inside the shared folder's folder for the project needs to follow the below structure (the files can be different but the folders remain).
Let´s suppose again we are working with a survey from INE called "ECEPOV", and that the latest one published is from 2021.

ECEPOV/
└── 2021/
    ├── doc/ `# manuales para utilización correcta de los datos`
    │   ├── cuestionario_ECEPOV.pdf
    │   ├── dr_ECEPOVadultos_2021.xlsx
    │   ├── dr_ECEPOVhogar_2021.xlsx
    │   └── dr_ECEPOVvivienda_2021.xlsx
    ├── processed/ `# carpeta con los archivos de datos originales en .csv extraídos a .feather`
    │   ├── ECEPOVadultos_2021.feather
    │   ├── ECEPOVhogar_2021.feather
    │   └── ECEPOVvivienda_2021.feather
    ├── products/ `# aquí se guardan los "productos" que produce el análisis en python, tanto el report en word como el excel con los resultados o bases de datos`
    │   ├── viviendas/
    │   │   └── ecepov_2021.xlsx
    │   ├── data_creation
    │   │   └── data_file_1.feather
    │   │   └── data_file_2.feather
    │   └── planes_pensiones_2021.docx
    ├── raw/ `# carpeta con los datos sin tratar`
    │   ├── ECEPOVadultos
    │   ├── ECEPOVhogar
    │   ├── ECEPOVvivienda
    │   └── LeemeECEPOV_2021.txt
