# Personalized Recommender System for Climate Investment Opportunities

This project aims to create a recommender system that suggests climate-related investment opportunities to potential investors. The recommendations are based on historical investment behaviors, macroeconomic indicators, and climate data. The goal is to help investors discover suitable fundraising projects in the clean energy sector that align with their preferences and the socio-economic and environmental profiles of different countries.

## Table of Contents

- [Project Overview](#project-overview)
- [Datasets Used](#datasets-used)
- [Installation and Setup](#installation-and-setup)
- [Execution Instructions](#execution-instructions)
- [Project Structure](#project-structure)
- [License](#license)

## Project Overview

The recommender system leverages multiple datasets to provide personalized investment recommendations:

- **Investor Data:** Historical investment behaviors, including the amount raised, technology sector, and country.
- **Macroeconomic Indicators:** Data such as Gross National Income per capita, GDP, and happiness index to represent the economic and social environment of each country.
- **Climate Data:** Information on greenhouse gas emissions, renewable energy consumption, and CO₂ emissions per capita to assess the environmental impact and focus of each country.

By integrating these datasets, the system employs collaborative filtering and content-based filtering techniques to recommend investment opportunities that match investors' preferences and align with favorable macroeconomic and environmental conditions.

## Datasets Used

The project uses the following datasets:

1. **Climate Fundraisers Data (`climate_codex`):**
   - **Source:** [Climate Codex on Hugging Face](https://huggingface.co/datasets/Xcissa/climate-codex)
   - **Description:** Compiles climate technology fundraiser data from March 2020 to February 5, 2024.
   - **Usage:** Provides core data on fundraising events and investor behaviors.

2. **Additional Macroeconomic and Climate Datasets:**
   - Gross National Income per Capita
   - Happiness Index
   - Renewable Energy Share
   - Greenhouse Gas Emissions per Capita
   - Monthly Temperature Anomalies
   - Primary Energy Consumption
   - Public Opinion on Climate Change
   - Global GDP
   - **Note:** These datasets should be placed in the `data/` directory.

## Installation and Setup

### Prerequisites

- Python 3.8 or higher
- Git (to clone the repository)

### Step 1: Clone the Repository

```bash
git clone https://github.com/your_username/climate-investment-recommender.git
cd climate-investment-recommender
```

### Step 2: Create a Virtual Environment

It is recommended to use a virtual environment to manage dependencies.

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

1. **Download Climate Codex Dataset:**

   - Visit [Climate Codex on Hugging Face](https://huggingface.co/datasets/Xcissa/climate-codex).
   - Download the dataset files.
   - Place the main fundraisers dataset (`climate-tech-fundraisers-keep-cool-ctvc-01-25-2024.parquet`) in the `data/` directory.

2. **Download Additional Datasets:**

   - Obtain the additional datasets listed in the [Datasets Used](#datasets-used) section.
   - Ensure all datasets are placed in the `data/` directory.

   **Note:** Ensure the filenames match those referenced in the code.

## Execution Instructions

1. **Ensure the Virtual Environment is Active:**

   Before running the code, make sure the virtual environment is activated.

2. **Run the Python Script:**

   Execute the main script:

   ```bash
   python main.py
   ```

   **Note:** Replace `main.py` with the actual filename containing the provided code.

3. **Output:**

   - Visualizations will be saved in the `visualizations/` directory with a timestamped subdirectory.
   - The recommender system will output recommendations and forecasts as per the code logic.

## Project Structure

```
climate-investment-recommender/
├── data/
│   ├── climate-tech-fundraisers-keep-cool-ctvc-01-25-2024.parquet
│   ├── gross-national-income-per-capita-undp.csv
│   ├── happiness-cantril-ladder.csv
│   ├── renewable-share-energy.csv
│   ├── total-greenhouse-gas-emissions-per-capita.csv
│   ├── monthly-temperature-anomalies.csv
│   ├── primary-energy-cons.csv
│   ├── support-policies-climate.csv
│   ├── share-believe-climate.csv
│   ├── support-public-action-climate.csv
│   └── API_NY.GDP.MKTP.CD_DS2_en_csv_v2_26.csv
├── visualizations/
├── main.py
├── requirements.txt
└── README.md
```

- **data/**: Directory containing all datasets.
- **visualizations/**: Directory where all generated visualizations will be saved.
- **main.py**: The main script containing the provided code.
- **requirements.txt**: Contains all required Python packages.
- **README.md**: Instructions and information about the project.

## License

This project is licensed under the Apache License 2.0. Please see the [LICENSE](LICENSE) file for details.

---

**Dataset Information**

**Climate Codex: Climate Technology Fundraisers Dataset**

Climate Codex is a dataset that compiles climate technology fundraiser data from March 2020 to February 5, 2024. The data has been collected from various newsletters and blogs, including CTVC by Sightline Climate and Keep Cool. This dataset captures key investments, innovative startups, and significant fundraising events that aim to address pressing environmental challenges.

**Sources**

- CTVC by Sightline Climate
- Keep Cool

**Methodology**

The dataset was prepared by scraping and cleaning data from the sources listed above, using tools such as Selenium and GPT-4 for data extraction and normalization. Currency values were converted to USD, dates were standardized, and locations were geocoded to enhance analysis. The final dataset includes columns for fundraising entity, amount raised, fundraising date, description, sector classification, location, and links to original announcements.

**Data Fields**

- **Fundraising Entity**: The organization or company raising funds.
- **Amount Raised**: Amount of funds raised, normalized to USD.
- **Date of Funding Reported**: Date when the funding event was published or reported.
- **Description**: Brief description of the fundraiser or the organization.
- **Sector**: Climate technology sector (e.g., Built Environment, Carbon Technology, Energy, etc.).
- **Location**: Headquarters or main address of the fundraising entity.
- **Links**: Links to the announcement and source newsletters.

**Usage**

This dataset is ideal for analysis in the fields of climate technology investment, environmental sustainability, startup funding, and economic analysis related to green technologies.

**License**

The dataset is available under the Apache License 2.0.

**How to Cite**

If you use this dataset in your research, please cite it as follows:
