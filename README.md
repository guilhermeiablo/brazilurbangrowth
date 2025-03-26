# brazilurbangrowth
## 30 Years of Horizontal and Vertical Growth in Brazilian Cities
A repository for code developed for WRI's Brazil horizontal and vertical urban growth paper.
https://www.wribrasil.org.br/publicacoes/trinta-anos-expansao-vertical-horizontal-cidades-brasileiras

In this repo you'll find the code necessary to extract, process and visualize data pertaining to the urban form - horizontal an vertical - and populational expansion in Brazil's main urban concentrations, as defined by IBGE. You'll also find the resulting datasets at vector grid (~9km), urban concentration and national scales.

![Data showcase](https://github.com/guilhermeiablo/brazilurbangrowth/blob/main/Figura%203.png?raw=true)
![Data showcase](https://github.com/guilhermeiablo/brazilurbangrowth/blob/main/Figura%204.png?raw=true)


# Getting started with the code
In this repository you'll find three Jupyter Notebooks. They are meant to be used consecutively.
**1 Horizontal growth extraction.ipynb** is used to extract time series data from Mapbiomas rasters stored in Google Earth Engine, containing Land Use data for Brazil as a whole. These are accessed for each Brazilian state and stored in a local folder.
**2 Raster downscaling and compatibilization.ipynb** is used to put together the data from three separate backscatter sensors, as described by Frolking et al. (2022) in order to obtain the time series for urban vertical growth. The previously acquired horizontal growth time series is then spatially harmonized with this series through downscaling and zonal statistics.
**3 Data Visualization.ipynb** serves to showcase the creation of specific charts and graphs that went into producing the underlying paper.

## Requirements
`conda create -n urban_growth python=3.11 earthengine-api geehydro pandas geopandas scikit-learn rasterio rasterstats glob pprint seaborn contextily palettable`

## Getting started
1. `conda activate urban_growth`
2. `jupyter notebook`
3. Run each Jupyter Notebook separately and make sure to point to the folders in which you save the data as you move forward.

# Resulting datasets
The three datasets cover the same themes of population, vertical and horizontal expansion in different scales (national, urban concentration, and 9km vector grid). Below you'll find a dictionary for field names present in all of them.

## Metadata
### Expansion by urban pixel (.GPKG)
- **_cd_concur**: Urban concentration code, provided by IBGE.
- **_nm_concur**: Urban concentration name, provided by IBGE.
- **_cd_mun**: State, provided by IBGE.
- **urban_[year]**: Urban horizontal coverage by year. The proportion of the grid cell that is covered by urbanized areas, according to the Mapbiomas classification, in a given year.
- **h_[year]**: Urban vertical extent by year. The power-ratio backscatter from one of the three radar sensors, which is a proxy for average building height, in a given year.
- **pop_[year]**: Total population by year. The resident population in a cell, in a given year.
- **horz_change**: The total change in urbanized area coverage seen in the period (1993-2020). Logarithmic scale.
- **vert_change**: The total change in PR backscatter seen in the period (1993-2020). Logarithmic scale.
- **pop_change**: The total change in population seen in the period (1993-2020). Logarithmic scale.
- **Cluster**: The number of the cluster to which the grid cell belongs.
- **label**: The name of the cluster to which the grid cell belongs.

### Expansion by urban concentration (.XLSX)
Note that this resource can be spatialized by joining with the IBGE Urban Concentration data provided under the _raw_data folder.
- **cd_concurb**: Urban concentration code, provided by IBGE.
- **nm_concurb**: Urban concentration name, provided by IBGE.
- **estado**: State, provided by IBGE.
- **ICH**: Outward Growth Index (Índice de Crescimento Horizontal). The sum of change seem in urban horizontal coverage by year in all pixels pertaining to the urban concentration.
- **ICV**: Upward Growth Index (Índice de Crescimento Vetical). The sum of change seen in Urban vertical extent by year in all pixels pertaining to the urban concentration.
- **pixel_count**: The number of pixels within the urban concentration.
- **cluster[number]**: The number of pixels from that cluster in the urban concentration.
- **classe_expansao**: The class, or cluster, to which the urban concentration belongs.
