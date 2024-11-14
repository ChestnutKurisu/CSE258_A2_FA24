# Personalized Recommender System for Climate Investment Opportunities

This project aims to create a recommender system that suggests climate-related investment opportunities to potential investors. The recommendations are based on historical investment behaviors, macroeconomic indicators, climate data, and advanced data analysis techniques. The goal is to help investors discover suitable fundraising projects in the clean energy sector that align with their preferences and the socio-economic and environmental profiles of different countries.

## Table of Contents

- [Project Overview](#project-overview)
- [Features](#features)
- [Datasets Used](#datasets-used)
- [Installation and Setup](#installation-and-setup)
- [Execution Instructions](#execution-instructions)
- [Project Structure](#project-structure)
- [Visualizations](#visualizations)
- [License](#license)
- [Acknowledgments](#acknowledgments)

## Project Overview

The recommender system leverages multiple datasets and employs advanced data processing techniques to provide personalized investment recommendations:

- **Investor Data:** Historical investment behaviors, including the amount raised, technology sector, and country.
- **Macroeconomic Indicators:** Data such as Gross National Income per capita, GDP, and happiness index to represent the economic and social environment of each country.
- **Climate Data:** Information on greenhouse gas emissions, renewable energy consumption, CO₂ emissions per capita, and temperature anomalies to assess the environmental impact and focus of each country.

By integrating these datasets, the system employs collaborative filtering, content-based filtering, and time-series forecasting techniques to recommend investment opportunities that match investors' preferences and align with favorable macroeconomic and environmental conditions.

## Features

- **Data Scraping and Cleaning:** Automated data scraping from newsletters and blogs using Selenium and BeautifulSoup, with data extraction enhanced by GPT-4.
- **Data Integration:** Merging multiple datasets to create a comprehensive view of the climate investment landscape.
- **Exploratory Data Analysis (EDA):** Detailed analysis and visualization of the data to uncover patterns and insights.
- **Time-Series Forecasting:** Forecasting future investment amounts using models like Prophet and LightGBM.
- **Recommender System:** Personalized recommendations based on text embeddings, country and sector similarities, and historical investment behaviors.
- **Evaluation Metrics:** Implementation of metrics like Precision@k, Recall@k, NDCG@k, and MRR@k to evaluate the recommender system.
- **Visualization:** Geographical plots, correlation heatmaps, and other visualizations to present insights.

## Datasets Used

The project uses the following datasets:

1. **Climate Fundraisers Data (`climate_fundraisers_df`):**
   - **Description:** Compiles climate technology fundraiser data from March 2020 to January 2024.
   - **Usage:** Provides core data on fundraising events and investor behaviors.

2. **Macroeconomic and Climate Datasets:**
   - **Gross National Income per Capita (`gross-national-income-per-capita-undp.csv`):**
     - **Features:** `Entity` (Country), `Year`, `Gross national income per capita`.
   - **Happiness Index (`happiness-cantril-ladder.csv`):**
     - **Features:** `Entity` (Country), `Year`, `Cantril ladder score`.
   - **Renewable Energy Share (`renewable-share-energy.csv`):**
     - **Features:** `Entity` (Country), `Year`, `Renewables (% equivalent primary energy)`.
   - **Total Greenhouse Gas Emissions per Capita (`total-greenhouse-gas-emissions-per-capita.csv`):**
     - **Features:** `Entity` (Country), `Year`, `Total greenhouse gas emissions per capita including land-use change and forestry`.
   - **CO₂ Emissions per Capita (`co-emissions-per-capita.csv`):**
     - **Features:** `Entity` (Country), `Year`, `Annual CO₂ emissions (per capita)`.
   - **Average Monthly Surface Temperature (`average-monthly-surface-temperature.csv`):**
     - **Features:** `Entity` (Country), `Year`, `Day`, `Average surface temperature`.
   - **Monthly Temperature Anomalies (`monthly-temperature-anomalies.csv`):**
     - **Features:** `Entity` (Country), `Day`, `Temperature anomaly`.
   - **Primary Energy Consumption (`primary-energy-cons.csv`):**
     - **Features:** `Entity` (Country), `Year`, `Primary energy consumption (TWh)`.
   - **Public Opinion on Climate Change:**
     - **Support for Climate Policies (`support-policies-climate.csv`):**
       - **Features:** `Entity` (Country), `Year`, `Support political action on climate`.
     - **Belief in Climate Change Threat (`share-believe-climate.csv`):**
       - **Features:** `Entity` (Country), `Year`, `Believe climate change is a serious threat to humanity`.
     - **Support for Public Action on Climate (`support-public-action-climate.csv`):**
       - **Features:** `Entity` (Country), `Year`, `Actions to tackle climate change`.
   - **Global GDP (`API_NY.GDP.MKTP.CD_DS2_en_csv_v2_26.csv`):**
     - **Features:** `Country Name`, `Year`, `GDP (current US$)`.

3. **Geospatial Data:**
   - **World Map Shapefiles (`ne_110m_admin_0_countries`):**
     - **Source:** [Natural Earth](https://www.naturalearthdata.com/downloads/110m-cultural-vectors/)
     - **Usage:** Used for geographical visualizations.

4. **GHG Emissions by Sector (`ghg-emissions-by-sector.csv`):**
   - **Features:** GHG emissions data broken down by sector for various countries and years.

5. **Research Papers:**
   - **Directory:** `research-papers/`
   - **Contents:** Contains PDF files, OCR transcriptions, and synopses of relevant research papers.

**Note:** All datasets should be placed in the `data/` directory. Ensure the filenames match those referenced in the code.

## Installation and Setup

### Prerequisites

- Python 3.10 or higher
- Git (to clone the repository)
- [Jupyter Notebook](https://jupyter.org/install) or [JupyterLab](https://jupyterlab.readthedocs.io/en/stable/getting_started/installation.html)
- [Conda](https://docs.conda.io/en/latest/miniconda.html) (optional, recommended for environment management)

### Step 1: Clone the Repository

```bash
git clone https://github.com/ChestnutKurisu/CSE258_A2_FA24.git
cd CSE258_A2_FA24
```

### Step 2: Create a Virtual Environment

It is recommended to use a virtual environment to manage dependencies.

Using `conda`:

```bash
conda create -n climate-investment python=3.10
conda activate climate-investment
```

Or using `venv`:

```bash
python -m venv .venv
```

Activate the virtual environment:

- On Windows:

  ```bash
  .venv\Scripts\activate
  ```

- On macOS and Linux:

  ```bash
  source .venv/bin/activate
  ```

### Step 3: Install Required Packages

Install the required Python packages using `requirements.txt`:

```bash
pip install -r requirements.txt
```

### Step 4: Download and Prepare Datasets

1. **Download Climate Fundraisers Dataset:**

   - Place the main fundraisers dataset (`climate-tech-fundraisers-keep-cool-ctvc-01-25-2024.parquet`) in the `data/` directory.

2. **Download Additional Datasets:**

   - Obtain the additional datasets listed in the [Datasets Used](#datasets-used) section.
   - Ensure all datasets are placed in the `data/` directory.

3. **Download Geospatial Data:**

   - Download the world map shapefiles from [Natural Earth](https://www.naturalearthdata.com/downloads/110m-cultural-vectors/).
   - Place the `ne_110m_admin_0_countries` directory in the project root.

**Note:** Ensure the filenames and paths match those referenced in the code.

### Step 5: Set Up OpenAI API Key (Optional)

If you plan to use the GPT-4 data extraction code, set up your OpenAI API key:

- Create an account on [OpenAI](https://openai.com/).
- Obtain an API key.
- Set the environment variable:

  ```bash
  export OPENAI_API_KEY='your-api-key-here'
  ```

  Or set it in your script or notebook.

## Execution Instructions

1. **Ensure the Virtual Environment is Active:**

   Before running the code, make sure the virtual environment is activated.

2. **Run the Jupyter Notebooks:**

   Launch Jupyter Notebook or JupyterLab:

   ```bash
   jupyter notebook
   ```

   Open the following notebooks in the order:

   - `fundraisers-web-scraping.ipynb`: Contains the code for scraping and processing the fundraisers data.
   - `Recommender System for Climate Investment Opportunities.ipynb`: Main notebook containing data analysis, modeling, and the recommender system.

3. **Run the Cells:**

   Execute the cells in each notebook sequentially to perform data processing, analysis, and generate visualizations.

4. **Outputs:**

   - Visualizations will be saved in the `visualizations/` directory with a timestamped subdirectory.
   - The recommender system will output recommendations and forecasts within the notebook.

**Note:** Some cells may require substantial computational resources or time, especially those involving model training or data processing.

## Project Structure

```
climate-investment-recommender/
├── data/
│   ├── climate-tech-fundraisers-keep-cool-ctvc-01-25-2024.parquet
│   ├── gross-national-income-per-capita-undp.csv
│   ├── happiness-cantril-ladder.csv
│   ├── renewable-share-energy.csv
│   ├── total-greenhouse-gas-emissions-per-capita.csv
│   ├── co-emissions-per-capita.csv
│   ├── monthly-temperature-anomalies.csv
│   ├── primary-energy-cons.csv
│   ├── support-policies-climate.csv
│   ├── share-believe-climate.csv
│   ├── support-public-action-climate.csv
│   ├── API_NY.GDP.MKTP.CD_DS2_en_csv_v2_26.csv
│   └── ghg-emissions-by-sector.csv
├── ne_110m_admin_0_countries/
│   ├── ne_110m_admin_0_countries.shp
│   ├── ne_110m_admin_0_countries.dbf
│   ├── ne_110m_admin_0_countries.shx
│   └── ...
├── research-papers/
│   ├── Literature Review.html
│   ├── papers/
│   │   ├── paper1.pdf
│   │   ├── paper2.pdf
│   │   └── ...
│   ├── ocr-transcriptions/
│   │   ├── paper1.mmd
│   │   ├── paper2.mmd
│   │   └── ...
│   ├── pdfs-ocr-nougat/
│   │   └── convert-pdfs.ipynb
│   └── synopses/
│       ├── paper1.md
│       ├── paper2.md
│       └── ...
├── markdown-to-jupyter/
│   └── conversion-notebook.ipynb
├── fundraisers-web-scraping/
│   └── fundraisers-web-scraping.ipynb
├── Recommender System for Climate Investment Opportunities.ipynb
├── requirements.txt
└── README.md
```

- **data/**: Directory containing all datasets.
- **ne_110m_admin_0_countries/**: Directory containing shapefiles for geographical visualizations.
- **research-papers/**: Contains research papers, OCR transcriptions, and synopses.
- **markdown-to-jupyter/**: Contains scripts for converting markdown to Jupyter notebooks.
- **visualizations/**: Directory where all generated visualizations are saved.
- **fundraisers-web-scraping.ipynb**: Notebook for scraping and processing fundraisers data.
- **Recommender System for Climate Investment Opportunities.ipynb**: Main notebook for data analysis and the recommender system.
- **requirements.txt**: Contains all required Python packages.
- **README.md**: Instructions and information about the project.

## Visualizations

The project generates several visualizations to aid in data analysis and presentation. Visualizations are saved in the `visualizations/` directory with timestamped subdirectories. Key visualizations include:

- **Correlation Matrix Heatmap:** Displays correlations between key variables.
- **Geographical Distribution Maps:** Shows fundraisers by clean technology sector globally and within the USA.
- **Bar Plots:** Number of fundraisers and total amount raised by continent and by clean technology sector.
- **Time-Series Forecasts:** Forecasts of funds raised for each clean technology sector.
- **Emissions vs. Funding Analysis:** Comparison of GHG emissions and funding by clean technology sector.
- **Scatter Plots:** Visualizations of relationships between variables like amount raised vs. temperature anomaly.

## License

This project is licensed under the Apache License 2.0. Please see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- **Data Sources:**
  - [Our World in Data](https://ourworldindata.org/) for macroeconomic and climate datasets.
  - [Natural Earth](https://www.naturalearthdata.com/) for geospatial data.
  - Various newsletters and blogs for climate fundraisers data.

- **Libraries and Tools:**
  - [Python](https://www.python.org/)
  - [Jupyter Notebook](https://jupyter.org/)
  - [Pandas](https://pandas.pydata.org/)
  - [NumPy](https://numpy.org/)
  - [Matplotlib](https://matplotlib.org/)
  - [Seaborn](https://seaborn.pydata.org/)
  - [Plotly](https://plotly.com/)
  - [LightGBM](https://lightgbm.readthedocs.io/)
  - [Prophet](https://facebook.github.io/prophet/)
  - [Selenium](https://www.selenium.dev/)
  - [OpenAI GPT-4](https://openai.com/)
  - [SentenceTransformers](https://www.sbert.net/)

---

**Dataset Information**

**Climate Fundraisers Dataset**

The [Climate Fundraisers Dataset](https://huggingface.co/datasets/Xcissa/climate-codex) compiles climate technology fundraiser data from March 2020 to January 2024. The data has been collected from various newsletters and blogs, including CTVC by Sightline Climate and Keep Cool. This dataset captures key investments, innovative startups, and significant fundraising events that aim to address pressing environmental challenges.

**Methodology**

The dataset was prepared by scraping and cleaning data from the sources listed above, using tools such as Selenium and GPT-4 for data extraction and normalization. Currency values were converted to USD, dates were standardized, and locations were geocoded to enhance analysis. The final dataset includes columns for fundraising entity, amount raised, fundraising date, description, sector classification, location, and links to original announcements.

**Data Fields**

- **Fundraising Entity**: The organization or company raising funds.
- **Amount Raised**: Amount of funds raised, normalized to USD.
- **Date of Funding Reported**: Date when the funding event was published or reported.
- **Description**: Brief description of the fundraiser or the organization.
- **Sector**: Climate technology sector (e.g., Energy and Grid, Transportation and Mobility, etc.).
- **Location**: Headquarters or main address of the fundraising entity.
- **Country**: Country of the fundraising entity.
- **Continent**: Continent of the fundraising entity.
- **Links**: Links to the announcement and source newsletters.

**Usage**

This dataset is ideal for analysis in the fields of climate technology investment, environmental sustainability, startup funding, and economic analysis related to green technologies.

**License**

The dataset is available under the Apache License 2.0.
