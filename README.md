# wind.power.potential-BG-HU-RO
Results of the GIS-based analysis of the wind power potential in Bulgaria, Hungary and Romania (funded by European Climate Foundation, ECF)

## Brief overview on the approach taken

As central element of this study, a thorough technical analysis of the future potential for wind power at the countryside (onshore) as well as, where available, in marine areas (offshore) is undertaken for the whole study region.

![Figure](https://github.com/ait-energy/wind.power.potential-BG-HU-RO/assets/74415146/0207b0fd-cde2-4773-b83f-603abddc2928)

Figure 1: Overview on the approach taken for the assessment of wind potentials in the study region
 (exemplified for onshore wind)

As illustrated by Figure 1, we conduct a GIS-based analysis of the potential for wind power development that includes the following steps:

- A comprehensive meteorological dataset on time-series of wind speeds is processed under a detailed geographical resolution for past weather years, serving as a basis for identifying unconstrained resource potentials across the whole study region, including adjacent marine areas. The underlying weather reanalysis open-source dataset is COSMO-REA6. It provides pre-calculated hourly wind speeds at 100 m and 150 m height and at a geographical resolution of 6 km times 6 km. For our analysis, wind speed data for the years 1995 to 2018 is taken into consideration.
- As the next step within the GIS-based assessment, spatial constraints are incorporated that stem from competing land use, such as nature protection (e.g., by excluding Natura 2000 protected areas), urban, agriculture, military use or other purposes that limit the suitability for wind power production and related grid deployment. Offshore wind is according to past experiences less relevant for the Black Sea region but recently gaining key policy attention at the European as well as the national level. Specifically, for offshore wind, competing uses of the sea (e.g., main shipping routes, nature protection areas and specifically tourism) are taken into consideration (i.e., by excluding related areas from the applicable resource base as a simplification).
- Sensitivity analyses are performed for key parameter affecting the applicable wind power potential, including – in the case of Bulgaria – the impact of excluding vs including nature protection areas and, specifically for offshore wind power, details on the applied wind turbine design (i.e., rotor area in relation to generator size). For Bulgaria these aspects, appear of relevance as identified in stakeholder consultations undertaken in prior. Apart from Bulgarian specifics we also illustrate the impact of further land use restrictions on those areas classified as being feasible for wind power development. That aims to increase social acceptance of wind power and may allow for a more rapid uptake in future years, once other barriers are removed. In this context, two different variants are assessed:
  - Balanced allocation: Balanced allocation of wind sites by using average suitability factors as listed in Table 1 below.
  - Least-cost allocation: Preference to best sites within a region, implying higher suitability factors as shown in Table 1 and, in turn, lower ones for less windy areas within a region.

Table 1: Average suitability factors applied for the identification of wind power potentials with (consideration of further) land use restrictions

| Land use category | Average suitability factor |
| --- | --- |
| **Built environment, Inland waters, wetlands** | 0% |
| **Agricultural areas** | 40% |
| **Forestry areas** | 10% |

- A mapping exercise is finally conducted to indicate how identified promising areas for wind power development match with the transmission grid infrastructure.

The outcome of this assessment are detailed maps showing available areas for wind power development as well as corresponding site qualities (in terms of capacity factors / full load hours) in dependence of sensitivity parameter, and a comprehensive dataset that lists the identified wind power potential at regional level within a country (i.e., by NUTS-3 region), incl. information on wind site qualities. Complementary to the country reports prepared, a more comprehensive background report will inform interested actors on further technical details concerning methodology and results, cf. Resch et al. (2023).

## Background information and technical details

For the interested reader we subsequently provide further details on the approach taken for estimating and reporting on wind potentials.

Software tools: For the GIS analysis a set of software tools are used, including CDO (Climate Data Observer, cf. Schulzweida et al. (2019)), Python and GDAL (Geospatial Data Abstraction Library, cf. Rouault E., 2022). Complementary to the above, QGIS, an open-source software tool, is used for map generation.

Details on approach and assumptions:

- As first step, to derive estimates on the electricity generation potential, **wind speed data** taken from COSMO-REA6, representing a global reanalysis of meteorological data combined with a large set of observations (cf. Bollmeyer et al., 2014) is **matched with a wind turbine power curve.** The result is an hourly time-series for all COSMO-REA6 pixels with theoretical load factors. The average load factor over all hours, ranging from 1995 to 2018, is calculated and serves as base for further calculations. The load factor is thereby expressed as full load hours, describing the virtual hours within a calendar year that a power plant operates at its rated power. Full load hours are derived by multiplying the load factor with 8760, representing on average the number of hours within a calendar year. In reality, a wind power plant is generally during more hours in operation than indicated by the full load hours since during many hours the plant operates at partial load. The following turbine characteristics are thereby applied:
  - As default our onshore wind turbine is the Nordex N163, characterised by a hub height of 150 m and a rotor diameter of 163 m. That turbine is equipped with a 4.95 MW electric generator.
  - For offshore the standard turbine is the VESTAS V164/8000, at hub height of 150m and a rotor diameter of 164 m, equipped with an 8 MW electric generator.
- Next, processed wind data is **matched with land use information** taken from the CORINE land use database (as of 2021). Land use data comes at a detailed geographical resolution (100 m x 100 m), requiring a retransformation of the wind data.
- Retransformed data is subsequently masked, and an **efficiency factor of 0.85** is applied to account for losses due to wind shading effects within a wind farm as well as maintenance, etc.
- **Exclusion of certain areas:** The process of masking comprises also the exclusion of areas not suitable for wind power development due to different constraints and aspects:
  - Techno-economic constraints: We exclude areas above an altitude of 2000 m and above a slope of 20° to account for possible technical challenges and/or high cost related to grid connection.
  - Nature protection: As default, we also exclude nature protection areas from our identification of wind development potentials. Information on protected areas is thereby taken from the UN World Database of Protected Areas (WDPA), cf. IUCN and UNEP-WCMC (2020). According to the provided information on the respective website ([https://www.protectedplanet.net/en/thematic-areas/wdpa?tab=WDPA](https://www.protectedplanet.net/en/thematic-areas/wdpa?tab=WDPA)), the WDPA is the most comprehensive global database of marine and terrestrial protected areas. It is a joint project between UN Environment Programme and the International Union for Conservation of Nature (IUCN) and is In our GIS modelling, all nature protection areas are buffered with 1200 m (to reflect a sufficient distance of possible wind power developments) and then excluded.

Upon request by some stakeholder, for sensitivity purposes we also illustrate the impact of including nature protection areas in our classification of go-to areas for onshore wind power development. That dataset is clearly as "Including Nature Protection Areas". Please note further that for onshore wind we generally excluded also inland waters and wetlands to account for nature protection as well as trade-offs with other purposes like shipping. For those areas a buffering with 600 m is applied, representing a further distance restriction for possible wind power development.

  - Social acceptance and avoidance of use conflicts: Built-up areas (incl. artificial surfaces like urban fabrics, industrial or commercial units, port areas, airports, construction sites, green urban areas, sport and leisure facilities) and infrastructure areas (incl. road and rail networks and associated land, mineral extraction sites, dump sites) are generally excluded. For the built-up areas a buffering of 1200 m is applied, respecting that wind power development should not harm the local community via noise or shading, etc.
  - Economic constraints: We exclude areas of low wind speeds to account for the economic viability of wind power development. That implies to exclude areas below 1,700 effective full load hours (i.e., considering the efficiency factor of 0.85 as discussed above) in the case of onshore wind, and below 2,000 effective full load hours for offshore wind.

Please note that for the calculation of offshore wind potentials, the same principles apply concerning nature protection. There are no land cover restrictions considered but shipping routes in the Black Sea are excluded instead. Starting with raster data from global shipping traffic densities ([https://datacatalog.worldbank.org/search/dataset/0037580](https://datacatalog.worldbank.org/search/dataset/0037580) ), the mostly used shipping routes are manually drawn as lines with 10 km width and then excluded.

- **Classification by area:** For the further processing in database format, the values of the usable (i.e., not excluded) pixels are aggregated by administrative boundaries. For onshore wind this implied a breakdown by NUTS region and a distinction between wind power site qualities (i.e., 12 categories of different wind site qualities, represented by ranges of full load hours, predefined for the whole study region) and by land use type (i.e., into 14 land use categories according to the level two classification of the CORINE land use database). For offshore wind the breakdown into 12 categories respects differences in water depth and distance to the shore.

## Literature

- Bollmeyer C., J. D. Keller, C. Ohlwein, S. Wahl, S. Crewell, P. Friederichs, A. Hense, J. Keune, S. Kneifel, I. Pscheidt, S. Redl, S. Steinke, 2014: Towards a high-resolution regional reanalysis for the European CORDEX domain. Article published in: Quarterly Journal of the Royal Meteorolog-ical Society, first published: 28 October 2014. Accessible at https://doi.org/10.1002/qj.2486.
- IUCN and UNEP-WCMC, 2020: The World Database on Protected Areas (WDPA) [https://www.protectedplanet.net/en/search-areas?filters%5Bdb_type%5D%5B%5D=wdpa&geo_type=region], [08/2020], Cambridge, UK: UNEP-WCMC. Accessible at: www.protectedplanet.net. 
- Rouault E., 2022: GDAL description and library. Remark: GDAL is an open source X/MIT licensed translator library for raster and vector geospatial data formats. Accessible at https://github.com/rouault/gdal. 
- Schulzweida U., 2019: CDO (Climate Data Observer) user guide. Software description, version 1.9.8, published October 31, 2019. Accessible at https://zenodo.org/records/3539275.

## Funding

This study on the wind power potential in Bulgaria, Hungary, and Romania has been conducted, on behalf of the European Climate Foundation (ECF), by AIT Austrian Institute of Technology GmbH, Center for Energy, Competence Unit Integrated Energy Systems (IES) in close collaboration with REKK – Regional Centre for Energy Policy Analysis as well as with local partners from the study region, including EFdeN – Sustainable and Green Homes from Romania and the Center for the Study of Democracy (CSD) from Bulgaria. The study team gratefully acknowledges the support provided by ECF.

## License

The entire repository is under the GNU public license 3.0

## Contact

´gustav.resch´ and ´lukas.liebmann´ both ´ait.ac.at´

