# brazilurbangrowth
## 30 Years of Horizontal and Vertical Growth in Brazilian Cities
A repository for code developed for WRI's Brazil horizontal and vertical urban growth paper.

![Data showcase](https://github.com/guilhermeiablo/brazilurbangrowth/blob/main/Figura%203.png?raw=true)


# Getting started with the code
In this repository you'll find three Jupyter Notebooks. They are meant to be used consecutively.

## Requirements
`conda create -n urban_growth python=3.11 earthengine-api geehydro pandas geopandas scikit-learn rasterio rasterstats glob pprint seaborn contextily palettable`

## Getting started
1. `conda activate urban_extent`
2. `jupyter notebook`
3. Run each Jupyter Notebook separately and make sure to point to the folders in which you save the data as you move forward.

# Resulting datasets

## Metadata
- **UC_NM_MN_ORIGINAL**: The original city name from the source.
- **UC_NM_MN**: A cleaned version of the city name. This column includes corrections for non-English characters and fills in missing values, providing a more standardized city name than the original.
- **ID_HDC_G0**: A unique city ID from the source, useful as a key for merging tables.
- **P15**: The population data for 2015 from the source.
- **B15**: The built-up area in 2015 from the source.
- **CENTER_SOURCE**: Source of the selected city centroid point - Source/COM/Overture/Google/Inspected/ToDo.
- **study_center_lat**: Selected city centroid point coordinate - latitude.
- **study_center_lon**: Selected city centroid point coordinate - longitude.
- **bu_city_center_lat**: Non NA start point coordinate - latitude.
- **bu_city_center_lon**:  Non NA start point coordinate - longitude.
- **study_area_scale_factor**: Scale factor - 20/40/80/160/320/640/1280/2560/5120/10240/20480
- **GRGN_L1 [region1]**: The continent from source.
- **GRGN_L2 [region2]**: More detailed regional information from the source, used for B15-P15 regression. 
- **[city_name_large]**: The name of the largest constituent city (based on population in 2015) within a unioned city.
- **[city_id_large]**: The ID of the largest constituent city (based on population in 2015) within a unioned city. Could be used as a key to merge tables.
- **[city_names]**: Names of the unioned cities, joined by '_'.
- **[city_ids]**: IDs of the unioned cities, joined by '_'.
