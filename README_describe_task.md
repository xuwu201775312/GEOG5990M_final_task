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


# Non-Spatial Data Clustering Results Visualization: Data Processing：

Import the lsoa-crime-london and lsoa-data CSV files.

Check the completeness and consistency of the data; no issues found.

Create New Variable: In lsoa-crime-london, sum different crime categories to create a new variable, crime_count.

Data Merge: Use LSOA code to merge lsoa-crime-london with LSOA data, creating a new dataset, merged_data.

Traffic Incident Variable Processing: In merged_data, sum traffic incident variables from 2010 to 2014 and calculate the average, creating ‘Average Road Casualties 2010-2014’.

Extract Relevant Variables: Extract all variables related to supermarket location selection, forming a list columns_to_analyze.

# Variable Selection:

Population Density (Persons per hectare; 2013): High population density indicates more potential customers and high demand (Ghorui et al., 2020).

Economic Activity (Employment Rate; 2011): Areas with high employment rates typically have a stable economic base and higher consumption capacity (Baviera-Puig et al., 2016).

Household Income (2011/12; Median Annual Household Income estimate): High-income residents have strong purchasing power, supporting high-end supermarket sales (Morrison and Abrahamse, 1996).

Health (Very good or Good health (%); 2011): Residents with good health tend to have a higher quality of life and demand for healthy products (Morrison and Abrahamse, 1996).

Public Transport Accessibility Levels (2014; Average Score): Good public transport accessibility increases supermarket foot traffic and indicates better regional transport conditions (Ghorui et al., 2020).

Average Road Casualties (2010-2014): Low traffic accident rates in safe areas help prevent loss of foot traffic (Baviera-Puig et al., 2016).

Total Crime Count: A safe environment is crucial for attracting customers (Baviera-Puig et al., 2016).

Exploring the correlation between these variables revealed low correlations, which helps avoid redundancy and improves the distinction in clustering results.

# Non-Spatial Clustering Analysis Visualization Results

Determining the Number of Clusters: Based on the elbow method, the optimal number of clusters is 5, indicated by a noticeable bend between 4 and 5 clusters.

K-means Clustering Analysis: Applied k-means clustering to the selected variables. Visualized the distribution of distances from each data point to its cluster center using box plots.

Cluster Results:

Cluster 0 (Prosperous Low Density Area): High income, low crime, inconvenient public transport, low population density.

Cluster 1 (Quiet Low Income Area): High population density and public transport accessibility, low income, slightly higher crime rate.

Cluster 2 (High Traffic and Crime Area): High public transport accessibility, very high traffic accident and crime rates.

Cluster 3 (Low Income No Access Area): Low traffic accident and crime rates, low public transport accessibility, population density, and income.

Cluster 4 (Affluent High Density Area): High public transport accessibility, high population density and income, average traffic accident and crime rates.

Box Plot Characteristics Summary:

Clusters 0, 1, 3, 4: Small box, data points close to the cluster center, well-clustered, good quality, some outliers but not far.

Cluster 2: Large box, data points far from the cluster center, dispersed, poor quality, many distant outliers.

Conclusion:
Cluster 4 is the best cluster for high-end supermarket location.


# Spatial Data Clustering Results Visualization: Data Processing

Import `boundary_London`, `LSOA_London`, and `UK_car_park` data.

Check the coordinate systems and unify them to EPSG:27700.

Merge Geographic and Non-Geographic Data: Use `LSOA code` to merge `merged data` with `LSOA London`, creating a complete dataset `london_cluster_gdf` with geographic information.

Clip Car Park Data: Clip `UK_car_park` point data to the London area.

# Spatial Clustering Analysis Visualization Results:

Use `cluster name` to visualize clusters with different colors. Overlay clipped `UK car park` data on the visualized clusters. Add `boundary_London` with bold lines at the top layer and include a map base layer for background.

Map Distribution Description:

Cluster 4 (Affluent High-Density Area): Yellow, concentrated in central London and surrounding areas.

High Traffic and Crime Area: Purple, mainly in a few central and two peripheral areas.

Low-Income Low-Access Area: Pink, largely in outer London, covering a large area but with fewer car parks.

Prosperous Low-Density Area: Orange, in the outermost regions, especially south and northwest, with fewer car parks, covering a large area.

Quiet Low-Income Community: Blue, mainly in central London, small coverage area with moderate car parks.

Further Analysis to Determine Optimal Supermarket Locations:

Focus on Cluster 4 (Affluent High-Density Area).

Calculate the number of car parks in each area within this cluster.

Filter areas with at least 2 car parks for better customer convenience and attraction.

The final analysis identifies these areas as optimal for a high-end supermarket location: 'E01000714', 'E01001519', 'E01001641', 'E01002826', 'E01002914', 'E01003887', 'E01003896', 'E01003939', 'E01032771', 'E01033568', 'E01033731', 'E01033734'.


# Reference: 

Baviera-Puig, A., Buitrago-Vera, J. and Escriba-Perez, C. 2016. Geomarketing models in supermarket location strategies. Journal of Business Economics and Management. 17(6), pp.1205–1221.

Ghorui, N., Ghosh, A., Algehyne, E.A., Mondal, S.P. and Saha, A.K. 2020. AHP-TOPSIS Inspired Shopping Mall Site Selection Problem with Fuzzy Data. Mathematics. 8(8), p.1380.

Kodinariya, T. and Makwana, P. 2013. Review on Determining of Cluster in K-means Clustering. International Journal of Advance Research in Computer Science and Management Studies. 1, pp.90–95.

Morrison, P.A. and Abrahamse, A.F. 1996. Applying demographic analysis to store site selection. Population Research and Policy Review. 15(5), pp.479–489.

