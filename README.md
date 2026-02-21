[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/SantanderMetGroup/ESD_ProseccoDOCG/HEAD)


# ESD_ProseccoDOCG
This repository supports the reproducibility of downscaling experiments developed in the project "Provision of statistically downscaled climate change scenarios for risk assessment in the Conegliano Valdobbiadene Prosecco DOCG production area".

### Preparing a working environment

All the scripts and notebooks are reproducible using the following configuration for a dedicated environment. Users are encouraged to install conda/mamba/micromamba and follow these instructions:

```
micromamba create -n downscaling_training -c conda-forge  "r-base==4.3.*" r-climate4r
```

Once succesfully installed, it can be activated:

```
micromamba activate downscaling_training
```

And more dependencies can be installed:

```
micromamba install -c conda-forge jupyterlab
micromamba install -c conda-forge notebook
```

In order to use R kerner for jupyter notebooks, runs these commands in R:

```
install.packages('IRkernel') 
IRkernel::installspec(user = TRUE)
```
