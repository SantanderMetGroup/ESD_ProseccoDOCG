[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/SantanderMetGroup/ESD_ProseccoDOCG/HEAD)

# ESD_ProseccoDOCG

## Overview

This repository supports the reproducibility of empirical-statistical downscaling (ESD) experiments developed in the project **"Provision of statistically downscaled climate change scenarios for risk assessment in the Conegliano Valdobbiadene Prosecco DOCG production area"**.

The project applies statistical downscaling techniques to Global Climate Model (GCM) simulations from CMIP5 to generate high-resolution climate projections for the Prosecco DOCG wine-producing region in northeastern Italy. The downscaled scenarios are evaluated using observational data and used to calculate viticulture-relevant climate indices under future climate conditions (RCP4.5 and RCP8.5 scenarios).

## Key Features

- **Statistical Downscaling**: Implementation of analog methods using the [`climate4R` framework](https://github.com/SantanderMetGroup/climate4R).
- **Cross-validation**: Rigorous evaluation of downscaling methods with ERA5 reanalysis data.
- **Climate Projections**: Application to multiple CMIP5 GCMs for RCP4.5 and RCP8.5 scenarios (1991-2100).
- **Climate Indices**: Calculation of viticulture-relevant indices (heat waves, temperature extremes, precipitation patterns).
- **Reproducibility**: Complete workflow from data retrieval to final projections.

## Repository Structure

The `notebooks/` directory contains the following Jupyter notebooks organized by workflow step:

| Notebook | Main Purpose |
|----------|--------------|
| [script01_retrieve_GCMdata.ipynb](notebooks/script01_retrieve_GCMdata.ipynb) | Demonstrates how to retrieve Global Climate Model (GCM) data from CMIP5 via the Santander Climate Data Service THREDDS server. Shows inventory of available models and data retrieval for historical and scenario simulations (RCP4.5, RCP8.5). |
| [script02_downcalingCV.ipynb](notebooks/script02_downcalingCV.ipynb) | Provides an example of statistical downscaling using reanalysis predictors in a cross-validation approach. Tests different predictor sets and evaluates downscaling performance for local meteorological variables. |
| [script03_downscaling_GCM.ipynb](notebooks/script03_downscaling_GCM.ipynb) | Applies the calibrated statistical downscaling methods to GCM data to produce local climate projections. Uses the best-performing predictor configuration identified in cross-validation. |
| [script04_indices_calculation.ipynb](notebooks/script04_indices_calculation.ipynb) | Calculates viticulture-relevant climate indices from observations and downscaled projections. Computes indices such as heat wave events, temperature extremes, and precipitation patterns for April-September period. |

## Installation and Setup

### Prerequisites

The scripts and notebooks require R (≥4.3) with the `climate4R` framework. We recommend using `conda`, `mamba`, or `micromamba` for environment management.

### Environment Setup

1. **Create the environment:**

```bash
micromamba create -n downscaling_training -c conda-forge "r-base==4.3.*" r-climate4r
```

2. **Activate the environment:**

```bash
micromamba activate downscaling_training
```

3. **Install Jupyter dependencies:**

```bash
micromamba install -c conda-forge jupyterlab notebook
```

4. **Configure R kernel for Jupyter:**

Launch R and run:

```r
install.packages('IRkernel') 
IRkernel::installspec(user = TRUE)
```

### Alternative: Using environment.yml

You can also create the environment using the provided configuration file:

```bash
micromamba env create -f environment.yml
micromamba activate ESDProseccoDOCG
```

## Usage

The notebooks can be run interactively in Jupyter Lab/Notebook or via Binder (see badge at top). 

**Note:** Some scripts require local data paths to be updated according to your system configuration.

## Data Sources

- **Observations**: Daily meteorological data from stations in the Prosecco DOCG region (1991-2020).
- **Reanalysis**: ERA5 data at multiple vertical levels (1991-2020).
- **GCMs**: CMIP5 models accessed via [Santander Climate Data Service](https://scds.es/en) THREDDS server.

## Climate Indices

The project calculates several viticulture-relevant climate indices for April-September:

| Variable | Description | Index |
|----------|-------------|-------|
| Daily mean temperature | Daily mean temperature | Tmean (°C) |
| Daily maximum temperature | Days with Tmax > 30°C | TX30 (days) |
| Daily maximum temperature | Days with Tmax > 35°C | TX35 (days) |
| Daily maximum temperature | Heat wave events (≥5 consecutive days Tmax > 30°C) | HW30 (# events) |
| Daily maximum temperature | Heat wave events (≥3 consecutive days Tmax > 35°C) | HW35 (# events) |
| Daily minimum temperature | Days with Tmin > 18°C | TN18 (days) |
| Daily minimum temperature | Days with Tmin > 20°C | TN20 (days) |
| Daily precipitation | Days with Precip > 5mm | PR5 (days) |

## Authors

**Ana Casanueva** (University of Cantabria), **Rodrigo Manzanas** (University of Cantabria), **Ezequiel Cimadevilla** (Instituto de Física de Cantabria, CSIC-UC), **Riccardo Soldan** (Food and Agriculture Organization of the United Nations).

## License

This project is licensed under the **GNU General Public License v3.0** - see the [LICENSE](LICENSE) file for details.

## Citation

If you use this code or data in your research, please cite:

```
Casanueva, A. et al. (2026). ESD_ProseccoDOCG: Statistical downscaling for climate 
change risk assessment in the Prosecco DOCG production area. 
GitHub repository: https://github.com/SantanderMetGroup/ESD_ProseccoDOCG
```

Additionally, please cite the `climate4R` framework:

```
Iturbide et al. (2019): The R-based climate4R open framework for 
reproducible climate data access and post-processing. 
Environmental Modelling & Software, 111, 42-54.
DOI: 10.1016/j.envsoft.2018.09.009
```

## Acknowledgments

This project uses the [`climate4R` framework](https://github.com/SantanderMetGroup/climate4R) developed by the [Santander Meteorology Group](https://meteo.unican.es/) (University of Cantabria - CSIC). Climate data access is provided through the [Santander Climate Data Service](https://scds.es/en).

## Contact

For questions or issues, please open an issue on the GitHub repository.
