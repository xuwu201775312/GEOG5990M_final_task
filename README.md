# **Analysis Objectives**

My objective is to select a viable location in London for a high-end supermarket. I use clustering analysis to identify the target cluster and perform a visual analysis.

Supermarket site selection is crucial for a new supermarket. In a highly competitive market, finding the best location not only identifies the potential area with the highest sales but also effectively enhances the supermarket's competitiveness. Through detailed demographic and geographic analysis, businesses can identify the areas most suitable for high-end supermarkets. These areas have higher spending power and stable customer bases, providing a solid foundation for the supermarket's successful operation (Morrison and Abrahamse, 1996). Additionally, scientific site selection analysis supports marketing strategies and business development plans, ensuring the supermarket can achieve sustained profitability and growth in the future (Morrison and Abrahamse, 1996). Therefore, conducting supermarket site selection analysis is an essential step.

The conditions for supermarket location include: Convenient transportation but low accident rates. High population density and low crime rates. Medium to high household income. Proximity to car parks to ensure convenience, safety, and purchasing power for customers.

# Method Selection

Using K-means clustering can group areas with similar features, identifying regions with market value and different consumer groups. This method helps identify high-potential areas to support supermarket marketing strategies (Kodinariya and Makwana, 2013).

The elbow method determines the optimal number of clusters by calculating the sum of squared errors (SSE) for different K values and plotting the elbow graph to observe the inflection point (Kodinariya and Makwana, 2013).


# Datasets

boundary_london1& lsoa_london: These datasets provide geographic boundaries of London at different administrative levels, useful for mapping and analyzing demographic and socio-economic data. https://ukdataservice.ac.uk/learning-hub/census/other-information/census-boundary-data/

uk_car_park: This dataset contains point data for car parks across the UK. https://hub.arcgis.com/datasets/tfwm::department-for-transport-uk-car-parks/about

lsoa-crime-london: This dataset includes recorded crime data at the LSOA level in London, provided by the University of Glasgow.  Recorded Crime Summary Data for London: LSOA Level - Dataset - UBDC Data Catalogue , None (2023). Recorded Crime Summary Data for London: LSOA Level [Data set]. University of Glasgow. https://doi.org/10.20394/sjpbiv4u

lsoa-data: This dataset encompasses demographic information, including population density, household characteristics, health, housing, crime, and employment at the LSOA level. https://data.london.gov.uk/dataset/lsoa-atlas
