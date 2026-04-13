# **AI-Enabled Monitoring and Decision Support for Climate-Resilient Cover Cropping Systems in the Maldives**

The agricultural landscape of the Republic of Maldives is entering a period of forced transformation driven by the existential threats of the twenty-first century. As an archipelago of 1,190 coral islands, the nation is defined by its geographic fragmentation and an average elevation of merely 1.5 meters above sea level.1 This unique topography places the Maldives at the forefront of climate vulnerability, where the interplay of rising sea levels, coastal erosion, and saltwater intrusion directly threatens the narrow margins of its food security.3 In response, the implementation of climate-resilient cover cropping systems has been identified as a vital strategy to stabilize the fragile topsoil, enhance organic matter, and manage the limited freshwater lens that sits precariously beneath the island surfaces.4 However, the success and reliability of these biological interventions depend on a sophisticated technological framework. The integration of artificial intelligence (AI) and machine learning (ML) provides a mechanism to move beyond traditional, reactive agricultural practices toward a proactive, data-driven system capable of real-time monitoring and precise decision support.6

## **Ecological Vulnerability and the Role of Cover Cropping**

The fundamental challenge of Maldivian agriculture is rooted in the composition of its soil and its proximity to the ocean. The soil is young and largely composed of unweathered coral material, characterized by a coarse texture, high alkalinity (pH 8.0 to 8.8), and exceptional porosity.9 These properties result in poor water-holding capacity and significant deficiencies in essential nutrients such as nitrogen, potassium, and iron.9 Furthermore, the soil profile is remarkably shallow, typically consisting of a brown organic layer only 15 to 40 cm deep, which is frequently washed away during the heavy rainfall events of the southwest monsoon.1

Cover cropping, the practice of planting non-harvested "green manure" between primary cash-crop cycles, offers a biological buffer against these environmental stressors. By maintaining a continuous vegetative cover, these systems reduce physical soil erosion, suppress weed growth, and harbor beneficial insects.5 Leguminous cover crops, such as soybeans (*Glycine max*) and certain peanut relatives (*Arachis spp.*), are particularly effective in the Maldivian context because they fix atmospheric nitrogen, thereby mitigating the need for imported chemical fertilizers.5 The reliability of these systems, however, is often undermined by the rapid onset of climate shocks. Artificial intelligence provides the necessary tools to monitor crop health, predict irrigation needs, and optimize the timing of cover crop termination, ensuring that the ecological benefits are maximized without depleting the resources required for the subsequent cash crop.6

| Environmental Variable | Maldivian Agricultural Impact | AI-Enabled Mitigation Strategy |
| :---- | :---- | :---- |
| **Soil Porosity** | High leaching of nutrients and rapid dehydration 9 | Regression models for real-time soil moisture monitoring 15 |
| **High Alkalinity** | Micronutrient lockout (Fe, Zn, Mn) 9 | Image-based nutrient deficiency detection using CNNs 16 |
| **Monsoon Variability** | Intense erosion and unpredictable planting windows 1 | Predictive rainfall analytics and early warning systems 17 |
| **Small Land Area** | High fragmentation and limited scalability 2 | Object-based segmentation for field-level monitoring 18 |

## **Exploratory Analysis and Unsupervised Learning for Environmental Zoning**

The first step in a comprehensive AI-driven agricultural strategy is the use of unsupervised learning to characterize the diverse environments of the archipelago. Given that the Maldives is split into 26 natural atolls and 19 administrative divisions, a "one-size-fits-all" approach to cover cropping is inefficient.2 Unsupervised algorithms are capable of identifying natural groupings within unlabeled environmental data, allowing for the creation of site-specific management zones.

### **K-Means Clustering for Soil and Climate Categorization**

K-Means clustering is a fundamental technique for grouping data points based on their similarity across various features, such as soil pH, organic matter content, and historic rainfall patterns.19 In the Maldives, this technique can be used to segment farmlands into clusters that share similar constraints. For instance, islands in the northern atolls, which receive significantly less rainfall (1520 mm/year) compared to the south (3050 mm/year), may be clustered separately to receive different cover crop recommendations, such as drought-tolerant Amaranth or specific varieties of soybean.2

The clustering process involves the minimization of the squared distance between data points and their respective cluster centroids. For a set of environmental observations ![][image1], the objective is to find the set of clusters ![][image2] that minimizes the within-cluster sum of squares:

![][image3]  
where ![][image4] is the mean of the points in cluster ![][image5]. By applying this algorithm to the 2,201 soil samples typically found in regional datasets, agronomists can uncover patterns linking soil chemistry to crop suitability, ensuring that the selected cover crops are naturally aligned with the local environment.19

### **Fuzzy C-Means for Transitional Ecosystems**

A limitation of standard K-Means is its "hard" assignment of data points to a single cluster. In the Maldives, where ecosystems often transition gradually—such as the change from shoreline sandy soils to inland muddy soils—Fuzzy C-Means (FCM) clustering provides a more nuanced alternative.9 FCM allows a data point to belong to multiple clusters with varying degrees of membership, which is represented by a membership matrix ![][image6]. This is particularly valuable for mapping complex soil textures across the 98 inhabited islands where agriculture is practiced, enabling the identification of "mixed" zones where multiple cover crop species might be used in a "cocktail" mixture.22

### **Principal Component Analysis for Dimensionality Reduction**

Agricultural datasets often contain a high number of features, from cation exchange capacity to solar radiation.15 To improve the efficiency of clustering and subsequent predictive models, Principal Component Analysis (PCA) is employed to reduce the dimensionality of the data while preserving its variance. PCA identifies the directions (principal components) along which the variation in the data is maximal.15 This technique is essential for filtering out noise in satellite-derived climate data, such as the discontinuities often found between hindcast and forecast streams in seasonal models like SEAS5.25 By isolating the primary environmental drivers, agronomists can focus their monitoring efforts on the factors that most directly influence cover crop reliability, such as root-zone soil moisture.15

## **Supervised Learning for Predictive Analytics and Risk Management**

Once the agricultural landscape has been categorized, supervised learning models can be built to predict specific outcomes based on historical and real-time inputs. These models are central to the "Decision Support" aspect of the system, providing early warnings and optimizing resource use.7

### **Classification for Crop Health and Stress Detection**

Supervised classification algorithms are used to identify discrete classes, such as "healthy," "drought-stressed," or "pest-infested".16 Random Forest (RF) is a popular ensemble method that builds multiple decision trees and merges them to obtain a more accurate and stable prediction.14 In the Maldives, RF models can be trained on multispectral satellite imagery—specifically the bands provided by the Sentinel-2 constellation—to detect early signs of vegetation stress before they are visible to the human eye.6

Another powerful classification algorithm is Extreme Gradient Boosting (XGBoost), which is optimized for speed and performance in large datasets. XGBoost is particularly effective for modeling the residuals of previous trees to minimize error, making it a robust choice for predicting yield shortfalls and drought impact in rain-fed agricultural systems.14

### **Regression for Continuous Parameter Prediction**

While classification predicts categories, regression analysis is required for continuous values, such as the exact percentage of soil moisture or the expected nitrogen fixation rate of a legume crop.15 Random Forest Regression, as implemented in the SMRFR framework, utilizes remote sensing and reanalysis data to provide daily estimates of soil moisture across multiple layers, from the surface (0-5 cm) down to the root zone (50-100 cm).15 This is critical for the Maldives, where the root zone is often constrained by a shallow hardpan layer.4 By predicting volumetric soil moisture with high precision (e.g., an RMSE of 0.0339 ![][image7]), the system can provide irrigation recommendations that conserve the nation's limited freshwater resources.6

| AI Technique | Algorithm | Application in Maldives Agriculture | Expected Outcome |
| :---- | :---- | :---- | :---- |
| **Classification** | Random Forest | Identifying crop types from Sentinel-2 data 27 | Spatially explicit land-use maps 30 |
| **Classification** | XGBoost | Early detection of drought and heat stress 14 | 30% reduction in water usage 6 |
| **Regression** | RF Regression | Estimating multilayer soil moisture 15 | Optimized irrigation scheduling 7 |
| **Regression** | Support Vector Machines | Predicting soil nutrient concentrations (N, P, K) 31 | Reduced fertilizer runoff and waste 32 |

## **Deep Learning Architectures for Spatio-Temporal Monitoring**

The reliability of monitoring systems is significantly enhanced by deep learning, which can autonomously learn features from complex, high-dimensional data such as satellite imagery and video feeds from agricultural drones.16

### **Convolutional Neural Networks for Disease Identification**

Convolutional Neural Networks (CNNs) are the state-of-the-art for image analysis. By utilizing convolutional layers that apply filters to detect spatial patterns, CNNs can identify crop diseases and pests with high accuracy.7 In the Maldives, mobile-based CNN applications allow farmers to capture images of cover crops—such as small red onions or green chilis—and receive instant diagnostics.7 This is particularly important for managing pests like rodents, which are a major concern for Maldivian agriculture.34

### **Recurrent and Temporal Networks for Phenological Tracking**

Crop monitoring is inherently a temporal task. The sequence of growth stages—from sowing to peak biomass and termination—must be tracked to ensure the cover crop does not compete with the primary crop for nutrients.13 Recurrent Neural Networks (RNNs), specifically those using Long Short-Term Memory (LSTM) cells, are designed to model these time-series dependencies.27 A hybrid architecture, such as a Recurrent-CNN (R-CNN), combines the spatial feature extraction of a CNN with the temporal modeling of an RNN, achieving accuracies of over 90% in agricultural land cover mapping.27

### **Transformer-Based Models for Cloud-Agnostic Sensing**

A persistent limitation in tropical regions like the Maldives is the high frequency of cloud cover, which renders optical satellite data (like Sentinel-2) unusable for large parts of the year.35 Transformer-based models, which use "attention mechanisms" to weigh the importance of different data points, have been developed to fuse optical data with cloud-penetrating Synthetic Aperture Radar (SAR) data from Sentinel-1.36 This fusion allows the system to retrieve biophysical variables, such as the Green Area Index (GAI), even in near real-time during the peak of the monsoon season.36 By interpreting the radar signal directly rather than reconstructing optical reflectance, these models provide a more reliable and resilient monitoring solution for tropical island environments.36

## **Remote Sensing and Geospatial Intelligence**

The deployment of AI-enabled systems relies on a steady stream of high-resolution Earth Observation (EO) data. The Maldives, due to its geographic dispersion, is a primary candidate for satellite-based monitoring.13

### **The Sentinel Constellation and Vegetation Indices**

The Sentinel-2 mission, part of the Copernicus program, is the most valuable source of multispectral data for agriculture, offering 10-meter spatial resolution and a 5-day revisit cycle.27 These satellites provide the bands necessary to calculate several key indices:

* **Normalized Difference Vegetation Index (NDVI):** A proxy for vegetation greenness and vigor, calculated as ![][image8]. It is the standard for detecting live green vegetation.38  
* **Normalized Difference Water Index (NDWI):** Sensitive to the water content of the vegetation canopy, providing a crucial indicator of irrigation needs in the arid northern atolls.25  
* **Normalized Difference Infrared Index (NDII):** Useful for distinguishing between different cover crop species based on their leaf moisture and structure.38

Studies in other tropical regions have shown that while optical sensors are highly accurate, combining them with Sentinel-1 SAR data significantly improves the delineation of agricultural land from surrounding secondary vegetation and forest.40 This is vital for the Maldives, where land reclamation and built-up area growth are increasingly encroaching on agricultural space.30

### **The AI2 Maldives Ecosystem Project**

A pioneering example of geospatial intelligence in the region is the AI2 Maldives Ecosystem Project. This initiative uses high-resolution satellite imagery and expert field data to create reliable AI models that classify diverse ecosystems across the archipelago.41 The project features enterprise-grade scalability, capable of processing high volumes of imagery through dynamic tiling and multispectral visualization.41 This framework allows stakeholders to toggle between visual, NIR, and thermal bands, providing a comprehensive view of crop health and water resources that supports sustainability tracking and yield prediction at scale.41

## **Implementation Framework and Decision Support Systems**

The goal of AI in Maldivian agriculture is not merely monitoring but the provision of actionable insights through Decision Support Systems (DSS). These systems bridge the gap between complex algorithms and the practical needs of the farming community.7

### **AI-Powered Advisory and Chatbots**

AI-powered chatbots represent a significant advancement in precision agriculture. By utilizing machine learning and real-time data analytics, these systems provide personalized advice on best farming methods, pest control, and nutrient management.7 Farmers can interact with these bots through smartphones—a technology already widely used for image-based disease diagnosis—to receive customized guidance in their local languages.7 This is particularly important for overcoming the "expertise gap" and the low levels of formal agricultural training often found in rural island communities.41

### **Digital Twins and Adaptive Resource Management**

The integration of AI with Internet of Things (IoT) sensors and satellite data enables the creation of "digital twins"—virtual replicas of farmlands used for simulation and optimization.8 These models allow for "what-if" scenario testing, such as predicting the impact of a specific cover crop on the groundwater salinity levels under different monsoon intensities.1 Adaptive algorithms can then model these weather patterns and early signs of drought stress to optimize the allocation of water and fertilizers, reducing environmental impact while maximizing productivity.8

| Component | Technical Implementation | Practical Benefit to Farmers |
| :---- | :---- | :---- |
| **Early Warning** | Integration of CHIRPS rainfall forecasts 17 | 100-day faster detection of climate-induced crop loss 35 |
| **Pest Control** | Computer vision on drone/smartphone images 16 | Swift response to outbreaks, reducing yield loss 7 |
| **Nutrient Management** | Multitemporal spectral analysis 27 | Targeted fertilization, saving costs and protecting reefs 32 |
| **Resource Mapping** | AI-driven water resource classification 41 | Identification of viable areas for new agricultural development 41 |

## **Strategic Roadmap and Workflow for Development**

To implement a reliable AI-enabled cover cropping system in the Maldives, a structured developmental workflow is required, aligning with the objectives of an Advanced AI engineering project.

### **Phase 1: Data Collection and Preprocessing**

The foundation of any AI system is high-quality data. In the Maldives, this involves synthesizing three primary data sources:

1. **Remote Sensing Data:** Downloading and preprocessing Sentinel-1 and Sentinel-2 imagery via the Copernicus Open Access Hub or Google Earth Engine.18 Atmospheric and radiometric corrections must be performed to overcome sun angle variations and haze.47  
2. **Climate and Weather Data:** Utilizing the CHIRPS-GEFS short-term rainfall forecasts and the Climate Hazards Group InfraRed Precipitation datasets for subnational rainfall indicators.17  
3. **In-Situ Soil and Crop Data:** Leveraging the results of the Maldives' first nationwide agricultural data collection exercise, conducted by the Ministry of Agriculture and Animal Welfare in collaboration with the FAO.48 This includes data on crop varieties, farming methods, and the specific needs of the 7,000+ people currently engaged in the sector.49

### **Phase 2: Feature Engineering and Model Selection**

AI engineers must extract relevant features from the preprocessed data, such as vegetation indices, soil pH values, and dekadal rainfall averages.17 The model selection process involves a comparative evaluation of different architectures:

* **Unsupervised Clustering:** Using K-Means to identify management zones.19  
* **Supervised Classification:** Comparing RF with Temporal CNNs for crop type identification.27  
* **Regression Analysis:** Using SVR or RF Regression to predict continuous environmental parameters like soil moisture.15  
* **Deep Learning:** Implementing R-CNNs or Transformers to handle the spatial and temporal complexities of the Maldivian monsoon cycle.27

### **Phase 3: Model Evaluation and Comparison**

Evaluation is performed using standard metrics such as overall accuracy, Root Mean Square Error (RMSE), and the Kappa coefficient.15 In the context of the Maldives, it is also essential to measure the "confidence" or uncertainty of the models, often using Shannon entropy, to ensure that the decision support provided to farmers is reliable.27 Comparison with baseline models (e.g., comparing a Neural Network with a simple RF classifier) is a critical step for justifying the deployment of more complex architectures.27

### **Phase 4: Integration and User Interface Development**

The final phase involves the development of a shareable interface, such as a Google Colab notebook for the core code and a web-based dashboard for stakeholders.45 This platform should integrate the predictive insights with the national early warning systems managed by the Maldives Meteorological Service.52

## **Datasets and Resource Repositories**

For researchers and AI engineers working on Maldivian agricultural systems, several key datasets are available:

1. **Maldives Rainfall Indicators (HDX):** Dekadal rainfall estimates derived from CHIRPS imagery and station data, covering the period from 1981 to 2026\.17  
2. **SMRFR (Soil Moisture via Random Forest Regression):** A global 9-km resolution dataset providing daily soil moisture at five layers (0-100 cm) for the period 2000-2023.15  
3. **EuroSAT and Sen-2 LULC:** Large-scale Sentinel-2 datasets for training deep learning models in land use and land cover classification, including agricultural and fallow land classes.46  
4. **SoilHealthDB:** A global database of 5,907 soil health measurements focused on cover crops and other conservation management methods.55  
5. **Climate Data Portal (Maldives):** A centralized digital platform developed by the Ministry of Tourism and Environment for climate-related datasets approved for public access.56

## **Economic and Societal Implications of AI Integration**

The implementation of AI-enabled cover cropping is not merely a technical endeavor but an economic and social imperative for the Maldives. While agriculture currently contributes only 1.2% to the national GDP, its role in providing food security to rural communities is immense.24 The current system is heavily dependent on imports for nearly all fresh produce, making it vulnerable to supply chain disruptions caused by extreme weather.12

By increasing yields (e.g., \+0.9-1 t/ha for rice in similar tropical contexts) and reducing input waste, AI tools can boost farmer incomes by an estimated $200-$600 per hectare.32 Furthermore, the introduction of resilient and high-nutrition crops, such as Amaranth and Soybean, through international collaborations like those with JIRCAS, can diversify the local diet and reduce dependence on imported goods.12 The Enhancing Climate Resilience and Food Security project, supported by a $21.95 million financing package from the Asian Development Bank, is currently upgrading the Hanimaadhoo Agriculture Center (HAC) to serve as a hub for this research and technology transfer.24

| Policy Objective | AI Mechanism | Societal Impact |
| :---- | :---- | :---- |
| **Food Sovereignty** | Precision mapping of all-weather crop types 36 | Reduced reliance on imported fresh produce 12 |
| **Environmental Protection** | Targeted pesticide/herbicide application 43 | Conservation of coral reefs from chemical runoff 45 |
| **Economic Resilience** | Predictive yield and market price modeling 20 | Stabilized markets and reduced financial risks for farmers 58 |
| **Climate Adaptation** | Early warning systems for floods and droughts 52 | Protected livelihoods during extreme weather events 53 |

## **Conclusion and Strategic Outlook**

The reliability of climate-resilient cover cropping systems in the Maldives is no longer a question of biological potential but of informational capacity. The transition to AI-enabled monitoring and decision support provides the only viable path for sustaining agriculture in an environment where the physical land itself is in flux. By utilizing unsupervised clustering for site-specific zoning, supervised classification for real-time health monitoring, and deep learning for cloud-agnostic temporal analysis, the Maldives can build a robust agricultural defense system.

The ongoing nationwide agricultural data collection and the development of the AI masterplan for 2025-2035 signify a national commitment to this digital transformation.49 For AI engineers and agronomists, the challenge lies in bridging the "stakeholder silos" and ensuring that these sophisticated models are translated into simple, accessible tools for the 7,000 farmers on the front lines of climate change.41 Through the integration of remote sensing, machine learning, and community-level advisory systems, the Maldives can transform its agricultural vulnerability into a model of intelligent, resilient, and sustainable island food production.

#### **Works cited**

1. CLIMATE CHANGE IMPACTS ON HEALTH AND LIVELIHOODS: MALDIVES ASSESSMENT, accessed April 7, 2026, [https://www.climatecentre.org/wp-content/uploads/RCRC\_IFRC-Country-assessments-MALDIVES\_final4.pdf](https://www.climatecentre.org/wp-content/uploads/RCRC_IFRC-Country-assessments-MALDIVES_final4.pdf)  
2. Introduction, accessed April 7, 2026, [https://www.fao.org/4/ai387e/ai387e03.htm](https://www.fao.org/4/ai387e/ai387e03.htm)  
3. MALDIVES \- Climate Change Knowledge Portal, accessed April 7, 2026, [https://climateknowledgeportal.worldbank.org/sites/default/files/country-profiles/15649-WB\_Maldives%20Country%20Profile-WEB.pdf](https://climateknowledgeportal.worldbank.org/sites/default/files/country-profiles/15649-WB_Maldives%20Country%20Profile-WEB.pdf)  
4. Production optimization for sustainable agriculture and efficient contract farming in the Republic of Maldives, accessed April 7, 2026, [https://www.agrojournal.org/28/04-03.pdf](https://www.agrojournal.org/28/04-03.pdf)  
5. Cover Crops for Climate Resilience, accessed April 7, 2026, [https://www.climatehubs.usda.gov/hubs/international/topic/cover-crops-climate-resilience](https://www.climatehubs.usda.gov/hubs/international/topic/cover-crops-climate-resilience)  
6. AI-Driven Crop Monitoring for Climate-Resilient Agriculture, accessed April 7, 2026, [https://www.springfieldresearchuniversity.net/\_files/ugd/6b1e99\_c5b3844c701549c48b8e92a8acd40b31.pdf?index=true](https://www.springfieldresearchuniversity.net/_files/ugd/6b1e99_c5b3844c701549c48b8e92a8acd40b31.pdf?index=true)  
7. (PDF) AI-Powered Decision Support Systems for Sustainable Agriculture using AI-Chatbot Solution \- ResearchGate, accessed April 7, 2026, [https://www.researchgate.net/publication/381912285\_AI-Powered\_Decision\_Support\_Systems\_for\_Sustainable\_Agriculture\_using\_AI-Chatbot\_Solution](https://www.researchgate.net/publication/381912285_AI-Powered_Decision_Support_Systems_for_Sustainable_Agriculture_using_AI-Chatbot_Solution)  
8. Assessing the Role of Artificial Intelligence in Transforming Decision- Making Across Modern Agricultural Systems. \- Everant Journals, accessed April 7, 2026, [https://everant.org/index.php/etj/article/download/2386/1731/6584](https://everant.org/index.php/etj/article/download/2386/1731/6584)  
9. Flora and Fauna Soil Assessment (1.37 MB) \- Ministry of Tourism and Environment, accessed April 7, 2026, [https://www.environment.gov.mv/v2/download/3683/](https://www.environment.gov.mv/v2/download/3683/)  
10. Cover Crops for Climate Change Adaptation and Mitigation | Article | EESI, accessed April 7, 2026, [https://www.eesi.org/articles/view/cover-crops-for-climate-change-adaptation-and-mitigation](https://www.eesi.org/articles/view/cover-crops-for-climate-change-adaptation-and-mitigation)  
11. Cover Crop Options for Hot and Humid Areas \- ATTRA – Sustainable Agriculture \- NCAT, accessed April 7, 2026, [https://attra.ncat.org/publication/cover-crop-options-for-hot-and-humid-areas/](https://attra.ncat.org/publication/cover-crop-options-for-hot-and-humid-areas/)  
12. Maldives Explores Resilient Crops with Japan to Boost Food Security \- MV+, accessed April 7, 2026, [https://www.plus.mv/english/maldives-explores-resilient-crops-with-japan-to-boost-food-security/](https://www.plus.mv/english/maldives-explores-resilient-crops-with-japan-to-boost-food-security/)  
13. Mapping cover crop species in southeastern Michigan using Sentinel-2 satellite data and Google Earth Engine \- Frontiers, accessed April 7, 2026, [https://www.frontiersin.org/journals/artificial-intelligence/articles/10.3389/frai.2023.1035502/full](https://www.frontiersin.org/journals/artificial-intelligence/articles/10.3389/frai.2023.1035502/full)  
14. Recent Methods for Evaluating Crop Water Stress Using AI Techniques: A Review \- MDPI, accessed April 7, 2026, [https://www.mdpi.com/1424-8220/24/19/6313](https://www.mdpi.com/1424-8220/24/19/6313)  
15. SMRFR: A global multilayer soil moisture dataset generated using Random Forest from multi-source data \- PMC, accessed April 7, 2026, [https://pmc.ncbi.nlm.nih.gov/articles/PMC12241553/](https://pmc.ncbi.nlm.nih.gov/articles/PMC12241553/)  
16. AI Algorithms in the Agrifood Industry: Application Potential in the Spanish Agrifood Context, accessed April 7, 2026, [https://observatorio-investigacion.unavarra.es/documentos/67ce7719e210502b2cf6e623/f/682588597285930ee74f7350.pdf](https://observatorio-investigacion.unavarra.es/documentos/67ce7719e210502b2cf6e623/f/682588597285930ee74f7350.pdf)  
17. Maldives: Rainfall Indicators at Subnational Level | Humanitarian Dataset | HDX, accessed April 7, 2026, [https://data.humdata.org/dataset/mdv-rainfall-subnational](https://data.humdata.org/dataset/mdv-rainfall-subnational)  
18. An Unsupervised Classification Algorithm for Multi-Temporal Irrigated Area Mapping in Central Asia \- MDPI, accessed April 7, 2026, [https://www.mdpi.com/2072-4292/10/11/1823](https://www.mdpi.com/2072-4292/10/11/1823)  
19. Unsupervised Learning for Crop Suitability Clustering Based on Soil Nutrients, accessed April 7, 2026, [https://mjfas.utm.my/index.php/mjfas/article/view/4715](https://mjfas.utm.my/index.php/mjfas/article/view/4715)  
20. Agricultural Yield Prediction Dataset \- Kaggle, accessed April 7, 2026, [https://www.kaggle.com/datasets/zoya77/agricultural-yield-prediction-dataset](https://www.kaggle.com/datasets/zoya77/agricultural-yield-prediction-dataset)  
21. Maldives Explores JIRCAS Expertise in Resilient, High-Nutrition Crops \- Archive MV \- Articles, accessed April 7, 2026, [https://archive.mv/en/articles/eEBjRq](https://archive.mv/en/articles/eEBjRq)  
22. Soil Classification Mapping Using a Combination of Semi-Supervised Classification and Stacking Learning (SSC-SL) \- MDPI, accessed April 7, 2026, [https://www.mdpi.com/2072-4292/16/2/405](https://www.mdpi.com/2072-4292/16/2/405)  
23. Cover Crop Cocktails: A Tool for Climate Resilience \- SARE, accessed April 7, 2026, [https://www.sare.org/publications/climate-risk-management-and-resilience-on-farms-and-ranches/understanding-climate-resilience/cover-crop-cocktails/](https://www.sare.org/publications/climate-risk-management-and-resilience-on-farms-and-ranches/understanding-climate-resilience/cover-crop-cocktails/)  
24. Ministry of Fisheries, Marine Resources, and Agriculture \- Googleapis.com, accessed April 7, 2026, [https://storage.googleapis.com/gazette.gov.mv/docs/iulaan/76426.pdf](https://storage.googleapis.com/gazette.gov.mv/docs/iulaan/76426.pdf)  
25. Estimating soil moisture and the relationship with crop yield using surface temperature and vegetation index | Request PDF \- ResearchGate, accessed April 7, 2026, [https://www.researchgate.net/publication/259513461\_Estimating\_soil\_moisture\_and\_the\_relationship\_with\_crop\_yield\_using\_surface\_temperature\_and\_vegetation\_index](https://www.researchgate.net/publication/259513461_Estimating_soil_moisture_and_the_relationship_with_crop_yield_using_surface_temperature_and_vegetation_index)  
26. Optimizing Agricultural Data Analysis Techniques through AI-Powered Decision-Making Processes \- MDPI, accessed April 7, 2026, [https://www.mdpi.com/2076-3417/14/17/8018](https://www.mdpi.com/2076-3417/14/17/8018)  
27. Agricultural Land Cover Mapping through Two Deep Learning ..., accessed April 7, 2026, [https://www.mdpi.com/2072-4292/15/19/4657](https://www.mdpi.com/2072-4292/15/19/4657)  
28. Use of Machine Learning Techniques in Soil Classification \- MDPI, accessed April 7, 2026, [https://www.mdpi.com/2071-1050/15/3/2374](https://www.mdpi.com/2071-1050/15/3/2374)  
29. Using Constrained K-Means Clustering for Soil Texture Mapping with Limited Soil Samples, accessed April 7, 2026, [https://www.mdpi.com/2073-4395/15/5/1220](https://www.mdpi.com/2073-4395/15/5/1220)  
30. Land use and land cover (LULC) of the Republic of the Maldives: first national map and LULC change analysis using remote-sensing data \- PubMed, accessed April 7, 2026, [https://pubmed.ncbi.nlm.nih.gov/28748428/](https://pubmed.ncbi.nlm.nih.gov/28748428/)  
31. Soil Health Monitoring System using AI \- JETIR.org, accessed April 7, 2026, [https://www.jetir.org/papers/JETIR1908649.pdf](https://www.jetir.org/papers/JETIR1908649.pdf)  
32. (PDF) AI-Enabled Climate-Smart Agriculture for Smallholder ..., accessed April 7, 2026, [https://www.researchgate.net/publication/400013693\_AI-Enabled\_Climate-Smart\_Agriculture\_for\_Smallholder\_Resilience\_in\_Sub\_-Saharan\_Africa\_A\_Systematic\_Review](https://www.researchgate.net/publication/400013693_AI-Enabled_Climate-Smart_Agriculture_for_Smallholder_Resilience_in_Sub_-Saharan_Africa_A_Systematic_Review)  
33. AI and Machine Learning in Remote Sensing for Tropical Forest Monitoring: Applications, Challenges, and Emerging Solutions \- Preprints.org, accessed April 7, 2026, [https://www.preprints.org/manuscript/202512.1554](https://www.preprints.org/manuscript/202512.1554)  
34. Plant Introductions in the Maldives: Achievements and Opportunities in South Asia, accessed April 7, 2026, [https://www.ispgr.in/index.php/ijpgr/article/download/1507/1332](https://www.ispgr.in/index.php/ijpgr/article/download/1507/1332)  
35. Faster Detection of Forest Loss \- NASA Science, accessed April 7, 2026, [https://science.nasa.gov/earth/earth-observatory/faster-detection-of-forest-loss/](https://science.nasa.gov/earth/earth-observatory/faster-detection-of-forest-loss/)  
36. AI for Near Real-Time Crop Monitoring—A New Method \- ESA Science Hub, accessed April 7, 2026, [https://sciencehub.esa.int/2025/11/27/ai-for-near-real-time-crop-monitoring-a-new-method/](https://sciencehub.esa.int/2025/11/27/ai-for-near-real-time-crop-monitoring-a-new-method/)  
37. Datasets tagged sentinel2-derived in Earth Engine \- Google for Developers, accessed April 7, 2026, [https://developers.google.com/earth-engine/datasets/tags/sentinel2-derived](https://developers.google.com/earth-engine/datasets/tags/sentinel2-derived)  
38. Using of Sentinel 2 Images for Tropical Economic Crops Growth Modeling, accessed April 7, 2026, [https://isprs-archives.copernicus.org/articles/XLVIII-M-6-2025/233/2025/isprs-archives-XLVIII-M-6-2025-233-2025.pdf](https://isprs-archives.copernicus.org/articles/XLVIII-M-6-2025/233/2025/isprs-archives-XLVIII-M-6-2025-233-2025.pdf)  
39. Using of Sentinel 2 Images for Tropical Economic Crops Growth Modeling, accessed April 7, 2026, [https://isprs-archives.copernicus.org/articles/XLVIII-M-6-2025/233/2025/](https://isprs-archives.copernicus.org/articles/XLVIII-M-6-2025/233/2025/)  
40. "An Evaluation of Sentinel-1 and Sentinel-2 for Land Cover Classificati" by Aaron Meneghini, accessed April 7, 2026, [https://commons.clarku.edu/idce\_masters\_papers/235/](https://commons.clarku.edu/idce_masters_papers/235/)  
41. Precision Agriculture with AI: Bridging the Data and Collaboration Gap \- Kili Technology, accessed April 7, 2026, [https://kili-technology.com/blog/higher-data-quality-in-agricultural-ai](https://kili-technology.com/blog/higher-data-quality-in-agricultural-ai)  
42. Artificial intelligence-based decision support systems in smart agriculture: Bibliometric analysis for operational insights and future directions \- Frontiers, accessed April 7, 2026, [https://www.frontiersin.org/journals/sustainable-food-systems/articles/10.3389/fsufs.2022.1053921/full](https://www.frontiersin.org/journals/sustainable-food-systems/articles/10.3389/fsufs.2022.1053921/full)  
43. AI in agriculture: Progress in Implementing the European Union Coordinated Plan on Artificial Intelligence (Volume 2\) | OECD, accessed April 7, 2026, [https://www.oecd.org/en/publications/progress-in-implementing-the-european-union-coordinated-plan-on-artificial-intelligence-volume-2\_3ac96d41-en/full-report/ai-in-agriculture\_c9ac6d24.html](https://www.oecd.org/en/publications/progress-in-implementing-the-european-union-coordinated-plan-on-artificial-intelligence-volume-2_3ac96d41-en/full-report/ai-in-agriculture_c9ac6d24.html)  
44. OBSERVER: Revealing hidden land patterns with AI and Copernicus, accessed April 7, 2026, [https://www.copernicus.eu/en/news/news/observer-revealing-hidden-land-patterns-ai-and-copernicus](https://www.copernicus.eu/en/news/news/observer-revealing-hidden-land-patterns-ai-and-copernicus)  
45. AI enabled, mobile soil pH classification with colorimetric paper sensors for sustainable agriculture \- PMC, accessed April 7, 2026, [https://pmc.ncbi.nlm.nih.gov/articles/PMC11753690/](https://pmc.ncbi.nlm.nih.gov/articles/PMC11753690/)  
46. Sen-2 LULC \- Mendeley Data, accessed April 7, 2026, [https://data.mendeley.com/datasets/f4ky6ks248/3](https://data.mendeley.com/datasets/f4ky6ks248/3)  
47. Deep Learning in the Mapping of Agricultural Land Use Using Sentinel-2 Satellite Data, accessed April 7, 2026, [https://www.mdpi.com/2673-7086/2/4/42](https://www.mdpi.com/2673-7086/2/4/42)  
48. Maldives to conduct first national agricultural data collection \- Archive MV \- Articles, accessed April 7, 2026, [https://archive.mv/en/articles/dEY1Ax](https://archive.mv/en/articles/dEY1Ax)  
49. Maldives to Conduct First Nationwide Agricultural Data Collection \- MV+, accessed April 7, 2026, [https://www.plus.mv/english/maldives-to-conduct-first-nationwide-agricultural-data-collection/](https://www.plus.mv/english/maldives-to-conduct-first-nationwide-agricultural-data-collection/)  
50. AgriYield: Predict Crop Yield from Soil, Weather | Kaggle, accessed April 7, 2026, [https://www.kaggle.com/competitions/agriyield-2025](https://www.kaggle.com/competitions/agriyield-2025)  
51. Assignment Brief Jan 2026 UFCFUR-15-3 (Dead line to submit on 26-4-2026 ).pdf  
52. Enhancing Climate Resilience and Food Security Project (ECRFS ..., accessed April 7, 2026, [https://www.environment.gov.mv/v2/en/project/33587](https://www.environment.gov.mv/v2/en/project/33587)  
53. ADB to Help Maldives Strengthen Climate Resilience, Food Security, accessed April 7, 2026, [https://www.adb.org/news/adb-help-maldives-strengthen-climate-resilience-food-security](https://www.adb.org/news/adb-help-maldives-strengthen-climate-resilience-food-security)  
54. Sentinel-2 Land Cover Dataset \- Kaggle, accessed April 7, 2026, [https://www.kaggle.com/datasets/salmaadell/eurosat-rgb](https://www.kaggle.com/datasets/salmaadell/eurosat-rgb)  
55. Data from: A database for global soil health assessment, accessed April 7, 2026, [https://agdatacommons.nal.usda.gov/articles/dataset/Data\_from\_A\_database\_for\_global\_soil\_health\_assessment/24853500](https://agdatacommons.nal.usda.gov/articles/dataset/Data_from_A_database_for_global_soil_health_assessment/24853500)  
56. Climate Data Portal: Dashboard, accessed April 7, 2026, [https://climatedataportalmv.online/](https://climatedataportalmv.online/)  
57. National Geospatial Database for Maldives to Mainstream Climate Change Adaptation in Development Planning (ADB Brief No. 117), accessed April 7, 2026, [https://rise.esmap.org/sites/default/files/library/maldives/Renewable%20Energy/Maldives\_National%20Geospatial%20Database.pdf](https://rise.esmap.org/sites/default/files/library/maldives/Renewable%20Energy/Maldives_National%20Geospatial%20Database.pdf)  
58. Climate-Resilient Crops: Integrating AI, Multi-Omics, and Advanced Phenotyping to Address Global Agricultural and Societal Challenges \- PubMed, accessed April 7, 2026, [https://pubmed.ncbi.nlm.nih.gov/40941864/](https://pubmed.ncbi.nlm.nih.gov/40941864/)  
59. Maldives: artificial intelligence readiness assessment report \- UNESCO Digital Library, accessed April 7, 2026, [https://unesdoc.unesco.org/ark:/48223/pf0000394928](https://unesdoc.unesco.org/ark:/48223/pf0000394928)

[image1]: <data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAKMAAAAYCAYAAACWYU02AAAFWklEQVR4Xu2aachtUxjH/zJdQ+FeQ6YMcWXIEKlr/HLJrNCNDIlQMgsZ6t6SMibuB8pwQ/eScJMhV+LwhZD4gDLkkhKFUmTI8PzeZy97nXX2PvvsM7/v3b/695591j577eG/nudZa79SQ0NDQ8PcZJ5pe9PmaUPDRFnPtMC0nWnDpG3OsYVppekX04OmA9ubGybMBqbjTI/Ln9HNqmHKfUxfmP6N9JvpyKx9edL2lWlh1jYJlpl+MO2ZfN8wfeAhvHRm2lDFItMfps/l6S+wsWm1aalps+j7SfGYqaUmPc8G8NHXphvShio2Mb1i+kceZoH8f10mPk8DjRlnD32bEQinpOIn5XkeE96VfZ4WGjPOHgYyIzOgT00/m26V14vTZESoMiPne1QmPq9vOth0RPZ5mIyzr3Gws+mk7C8wKz5e7WVbHQYyI9wmj45vyWeu00Y3M+4ir28vNt1vetP0kDzCrzHdk+86MOPsa9RQgl1lesB0nukT053yGfH18nnEXv/v3TsDm/EEed34jvoz41mmb2rofdMeM7+shvPhvDAB64wx1Lws9YRjEaF+lc++F8uvaYWGU/uOs69xcIzpFuXny4D/1rS36SX5tXGNdQnPi7KPJZ9a0Pnrps/UPpGZNBiPpZxV8lHLeaZgjKujbdILqwOkTFYBiGA7Re2wrTwSpMauom5fLJ8RPRGfp40rlC/Xcf6vmZ6RG+hw06nqv+w4xPSd6Xb5PenpOKSd5+U3Op7I1Hb0CKAm49wYJCeqt4hDubHWtGPyPZByXjC9qPKUX4dufR0kT4E8BB4s2QDTTiu7y83Td2pNIItw/awNY/DKNWrC6dOmQ7PteCKzX9ipR8Jrul5V57XRYaafTNemDQmYq6V8dJdxsgY3Y1VfPNQv5ddJO/s93LbHdHGK8ig/KFwvdShBJJQ0XcGIz8kjTswyeXTkbx2IsGfUEClg/swvqwkPs6VOA5ECnpLXP6TxH9U+ui8yHRttQzczbpmpiDp9bS0f5ERzBio1GOk6hv6ZuZZFfKLqruosJzA4v4vhee6g9mMx2ClJigY9+10gr4E5D85trfIoz+/uNW1q2sZ0n+ly0/7yQbVSneVPIExgbkobithNnv7i+ifAyPjL9K46L3iSUFy31Gmga+SD50LT+dlnzAYMkCfUeR1lZiSNfy8v4rlHKf30BUwCiJKk7gD7fSSPRoui72PoJy2bis6x7FjM7MsCC4bmnPgdx/xA+T3BqKwOnJ3te478FR+R7vSsnUFYltKDGcvaZzjX9Kfy981/yyNU4NLsu7h9jXqPYKOkzIwMHm4oI3WFfJ30Y9Mj8gFXNOkpMyMjnWMxiQsmi+mnLyLWKnUajr5flvfFgy+Cc/hdvswSIl44RyYbYdUjHAuzMCgC1Gwcn33TayVack+poXkDR9R7T56BnjXdmO0DTCKZ1L6q3Kxc/yVZe0pPZpzNlJkR0nSXbqeUmTFAumWmXER67HQ7BrPwJguTEtl4qCmLTZelXw4RyoXlKv7/AsoA0nEoA9LtGIzFhA2Iqi0VDz5Yp81Yl25mxDR3qzhN14GoslQeEXk41I+YPIWol0bNYcKx6WMQuCdMdJnkAH/Z5t/4loSdItYJM5JGtkobasDEhHWvt+ULurxpSP8vknR0h4ojXR1CvRfrtLY9pAPkkwGWQUYBg+1R075pQ02IhG8oH6CYkXuH2YpekFBKUNPOWTNyA5hYUacVpZxhQARgpBfd4FFAhC6bkQ4D0ujR6Zd9wMBM7zmz7KKFbEoWamrWLMvS+JyANSvqlg9VvebYMF42kk/keA14pYpXFRoaGhoaSvkPakgk7/vj9QcAAAAASUVORK5CYII=>

[image2]: <data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAJcAAAAYCAYAAAD3eW90AAAFRklEQVR4Xu2aeahvUxTHlwyZx5dZ3jMkJOSlzDdR/GEoszKniGTI48lw/xF/UIbyIvHeK1NEembKD4UoIiFDIZGEEjJk+H7e+u3rnPU7051+53dv51Pf7u/ufX77nrP22muvtc816+jo6OgYLptKW0lrx46OWWVDaZv+zynDl8ekE6XdpTX77RtI2/c/t8E+0kfSZ9ISaUG+u2OWwRdulL6Qnpe2zvXWsIf0hvSL9Ih0ubRSekHaU3pWOmLi6uGyifSm9IR1EatttpDekh6S1gp9AzBZ10p/SldL6+W77RDpZ+lray9yEY6/lK6KHR2tsELqWc0WiWMtk/6STgh9iXWlp/vicxt0zjVaNHKuC6R/paXSGqEvC4NdExuHSOdco0Wtc+0ifSN9Ku0Q+iL3Wnv5FjR1LiLxYul4q3+mqUKleox0qM3N/G8mbFTrXOPmUYsKoA4S6jYNWedcRN1TzCtJChE+U5ycnL1omlAdPWZeVJwqXW9e7GCbucBM2qjSuWjsSf/YzEWk66SvJqHnpM1Xf7OeA6TfpPNih7nRrpC+l/bvtzH5LJw70kXTZEfpA+ke80WWqtcfzEv0UWembTRuXuAtCu2rSZHgW2mn0DdKcGA6Jn0o3W9+1hbZT/rV/IETPBPOnj2L2VI60yZflFBukxZkjUnbueZbCxNHFc0OcJf5dlmVv7ZBExtdaL6Am+5kHE29Iu1twabJuRCfqyDpPzA2DgEm8BLpXelJaed89wSsPKrdg2NHn92kVdJTVhHKKyAyEaHYEovOdXCsG8yPcHaVPpFOz13RPnU2AhwEOx0bOwpg8YyZzw3iwH2CzaS3rd65ODC7z3zV15FeDzQVY6bT/yq4Zqn0o7Rv6Evb++fmiXYVJOE9m7xz8T22D/KUIujnHJAVDKz8l6w4yrZBUxuxSNjqm+xkOCCRkLytMErfap5zHRU7+vAlDFp2/hXZy9yDm+poGzywLYMHZguPCT0TyET2bNBpcMr1M79XORdtLKQiQ3GfOBffjzD+xtJB9n/BQ5SIZ4L0sZiqiiImnnvIwvazreXvizHIAbNj8ayMX7TlN7URuTcFCs/Dsz5o/mamiBXSa9JGsSPBDRLCX7XB90RMOtXQZVZs8GGTtvHoXEDbO5afGAx6t3RGpq3Mufjee9If5oVDhHKd45qzQ/vh0uOW/7tcS+IftxYWMg46HtoTbN3fWT6vK7uvorEodGgreyXTxEacY94knWT+VuZj84VVBM7Vs0Fb5lgovW6eyC2XzpJuN/dKjDcKjgVVzsXqfth8IqjmMPCLNphYlzkXvz9jHsWvDH0JjMzEP2r+N3rmE8EqTxBJbjOfnGi3S83HJ4LEvw9sSdw//eloI90XAYBAkGAsXtVldxSe7XfzrQ9bRepslN7CEGhI/mkjdSpLWxo5FzDQQvPKB5E4lw3aFlXOlaCy5LqyBy5zrgTbwsWxMQPOw9ZVlCvSx8pnQQKJfYwgC6Q7bfZyMRyE8avyqjIbbWceZEiRXrb6s6/GzjUXaOJcddQ51xIr3hbrYHFeZD4+98kWRwESoxdj8zdmi0XSLTbo1E1I+Ra2wcYsFKLa4uxFGealczU5g4mwWm82P42mwllp/r9hWaj0OMtqWmBkGZP+Ns95kpicLEwCVXdZgjxdiKQ41pGxoyEUbuP9z+eYJ/MskCJ7sGgesHnkXKzGZdJP5vlP3JamC1GHvGe24KzssNg4g7D4jrPBaNmUdSxffVIFFtmYa843z/n4OW/gYQnfy6X3zRPPjuFxmnkFScHHP5ZO1ZE7Ojo6Roz/AI1WB4OLICu3AAAAAElFTkSuQmCC>

[image3]: <data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAmwAAAA5CAYAAACLSXdIAAAE/UlEQVR4Xu3dX6hlUxwH8CV/IuRvg2bimvzJ0yh/QkPzMIr8SSEUUmqG8EBRBhkhf2oKaZJG8yBJptCkJA+HNzyI8uLPizSe5MU8IH/Wb/bZzj7r7n3nnHPnzD23+/nUt7Nn/c7suXOffq2191opAQAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAwERW5+zJWVsWAACYHc+WAwAAzI41ORtybsv5eLgEAMAs2JjzeM6ROccUNQAAZsDunNNyPsvZXNQAAJgBR/c/Dx8aBQAAAAAAAAAAAAAAVoxbcv7N+aMsFGJ7j7NzvkrV998eLu8zl6ra0zmHDJeGHJpzXc47qfr+mcPlZSk2Gd6eFv5/AwBM7ItUNU6vl4UOR+XsSO3NSTRrca/vykKHuEc0gacU49Eg1mbpTdX67dlwbKp+/mg+1/XHPhmUAQAOnItzfktVozWq41L7zFiMx30i0diN4uFUzfQ1RRNUu6BxvdTuaVw/k6pNhaOJq5vKDwdlAGAl+yvnlXJwkaLhiCYrNsqNpmsxovn6J2dvWRjDcmrYQvz+Xkrts44AwApzWM6vOeeVhQPgylQ1bX+XhQmsSoNl1kmWNJdTw1Yvi8bJEI826gDAChXPevXSdM73jMajXs48q6hNol5mvb0sjGChhi0awCtS9fJC1OJzseKezefTuprMtoZtQxr83rY06gDACvVQzvXlYN9HOT8tkFFEo7YnVc3HYpf36mXWyLjLrF0N22up+hljbGuqDqnf2ahPKt7yrF98uDrnokbt1jT4XbQ1bAAAQ3al6SyHNt2Yqibr8rIwgXhbNO4Vb4+Oo6the7D/GU3V+lTNiq0ZlPeJN0xjebItJzW+V4umq5eq5eYQzdvJ/1dT2tS41rABAK3mGtfxwkGXaEbKBqWZcXydupcFxxEzU9tyzigL+9HVsNV6adBgLVbMWNb70K3N+aV/Hc3gU2l4dlDDBgC0+rP/GU3Px83ClMQM27gNVpdo/OJ+4+pq2GK27u7+Z4ifs23WbBy9NGjSYh+1n1M1yxYbBV+Sc0K/FjRsAECrz3Nuzvk+59SidqBdk/NNOTihWKq8P032LFxXwxYN4FupWmJ9I+eDRm1S8dZtzFzGbNodqWreXuzXtvY/axo2AGBJxWzVJLNhbWI5ddSTE9p0NWzT8GOaf9JCiJm7mHFrPsunYQMAlkw8p7W1HFzAXGpvcsIjOZ+WgwuIxu6qYuxgNWzxf4gl1lFp2ACAJVHPho36ksFczpflYEMsW476DFwcXxVnmTafEwuXNa7PaVwvteaWKpvT8JmnAABTEc+X/ZBzaZr/VmkzsRdZPNcVpyDEA/+91O7bNP/vlrkp5/2c31N1r2nOoAEALHuPpWp2bZy8nIa3GqlFI1Z+d5QAAAAAAAAAHAT3lgMt7iwHAAA4eF4tBxrOzdmdul82AABgiuJN0Rtyzi8LLXrlQGFHzrU57/b/vCXNP6w+/r03c3YW4wAAdFiVc3rO+rLQolcONMR9Yl+y2Kus3lD2vTR4G/TJ/ngcfRVN24k5R6TqzE4AAPYj9mGL0w6i4Sr3TWueaNBrXLdZnbO28ecLG9e1XeUAAAD7ty3ngXKw4fic53P2pu6l07tytudsStX+bmFdzhP1F/pi1u2+nBdyNhY1AABmzHPJeZwAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAADMlv8AWpKz/o+99yIAAAAASUVORK5CYII=>

[image4]: <data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABEAAAAYCAYAAAAcYhYyAAABGklEQVR4Xu2Tr0tDURTHj6hBnEVBJwzGbIIGoyCYLZZFbSLra1sQixjEYlZMooLFbjCYbP4BZpOYDf74fL33Ps7evKJR2Ac+vLfv3j0779w7swED/k4dF0vZME6UsiwVvMUzHHL5Lj7glMuyzOETtl02jjfWXzjLOr7iistS4ZbLxChuY62U2xE+4ozLvisstPgYZ32Y5nGFIy7fs/7CWebxGbsu84V1f4DTFrq6xrXiyYja/rDwy4kmvlkovICHFjrajN9dWtj+As3jHV9wHy9wB0/wHs9xCSexiqe48bUyUm5bw9JVaFt1PtJn0cC7eC1I8/Dn4ye03epkGVdTmNvGHFsWXreDYylUB78+1hH9l3qGqvfuCf4vn5cNLPOClu4gAAAAAElFTkSuQmCC>

[image5]: <data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAA4AAAAYCAYAAADKx8xXAAAA80lEQVR4XmNgGAXDFYgDsS8Q2wExK5ocViABxGuAeD0QRwBxHRDvAmJ+ZEXoQB6IrwDxLAaILSDFJ4D4LRBrIqlDASxAPAeInwCxIpJYEhAHADEjVAxkWCaUBgOQiSCTQc4EacAF9IF4ChDzwARAAfEfiItgAsQCTwaIRpAB6ICLAeIKkJO3AbEBsqQsEN8G4gRkQSBwAuJ1QGzJADG8CogbkBWAAEgCFDirGSAhewCI24GYD4jFgFiOAWKjDVQ9CgBFAyjyQQqZ0eRAtu5mIBCn2MAkIC4HYi8g1kGTwwt6gXgyEOcyIOKVKABSzAulhxoAAFTTHk2RWKbqAAAAAElFTkSuQmCC>

[image6]: <data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAA8AAAAZCAYAAADuWXTMAAABAUlEQVR4XmNgGLmgE4h/AfF/JHwRiNWg8lZA/AVJ7i8QZ0HlwEAciO8C8XUoGx0wAvEiIM4FYmY0OQYbIP4NxEsZIArRAS8QrwJiJXQJEEhngDgJRGMDmkC8Goh50CVANoFs/ArExmhyMOAHxM3ogiAgAsRXoRjExgYmMEAMwACmQPwNiOczYPcvyKnLGcj0L0gTSDOGf0GAbM2wwAI5G+R8bABnYIFMO8AASSC4EkcfEDugiYMBNxDvAeLDDJCEgA7MgXg2ELOiS8BABhC/BWIdNHGQN7YAsTyaOAoAmdoDxO+BuAaIk4F4JwMkRUkgqcMLZIE4AIh9GbD7fxQMGAAA4Dkuapwn0scAAAAASUVORK5CYII=>

[image7]: <data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADsAAAAYCAYAAABEHYUrAAADEUlEQVR4Xu2WW6hMURjH/0KRe5TkFkUpRbmUKEd5oBDyoKTmyS08kJRbJ6Uj8UAkl8iTlPLgkiRNeSFPirwipUhKkUvi/+/by3yzZs/M3nvG6cT869c5e609a3/ru60FdJRb/cka0kP2kuHV072mXrFjC9lD+pESeURG+BfqSO8PiQdbUFE7cukAeQDz5ErylkyteiNdM8lhmHHtUFE7CklGnyZnyYBoLk37ybJ4sA3Ka0duLSSPyW0yNppLk9LrEhkTT7SovHa0JEXqGZkcT0RaSrrjwTYqqx25pJTRwnOT5znkM9n8541a6TfHyIJ4ogVltkMFvZxMTJ4Hwn602o1pselkXfI3NBWl4XNyMXmeRz7CIldPSq/LqO2U42B2jE6eB5EuWLMJYzpetBFvm5TJjqHkHDlEXpON5CbZBGsg78kKch7W7UrkJdkNkza9kxyFReoqOQ5zWD2tJ9uisQmwGlbEZXQJZscGcgr2zcXkOux7O2C2rYIpkx0KvUI9i3wi91HxuDz9irwj85Mx6QopwxwVpP/1/kg3liZ1xzOwY8dLNsgWRfYXzLnB0JCSvgb1vTLMFq+GdmyFbXQt+UGWuLkZ5APsNhIUPiIPF2nrOvcuwFI0SOschBm5D+bcaW5eqfgTlShK42HRPuLGMkupovTxR4EW/0YWubHggO1uLI8UQaVmmuQAHRnCO0POji8IcsB3FDinh5GHqI1WqBV5MUibVOHHaZhFg2ENZEo8kUh1+wbV0QoOKKNSNuHS8AIFztIQrV1uLC1dZezdBP2ve6iv5WZS7Z1E/ethSFfVbVBaumqD2qg2rLpWU5vk5hsq1GtaunoH6MhRB1Qqqu0rSr5JNVOz66HqNS1dYwd0ka/JnBx4Ajn6Rzd5ispZJmnxL6g++LWxO+QeuUVmu7lmUofX2Vov7XR+XiM3UF2vcrZS26e+0v0JzAZlnp4zS4vHEdLHR6E25TSuJtboHE2TskbndCPJBr9RSd+JLx+SxmWH7Olz6kF7r4d9VvWuh/+kwi3tv5AuEeruHXX0F/Qb+MyOHWtjs+0AAAAASUVORK5CYII=>

[image8]: <data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAE4AAAAZCAYAAACfIRhSAAADCklEQVR4Xu2YS8hNURTHlxh4v/PKhPKaoGTALRMDAxFGHhMTkVCSwkAfUiZSEiWllIEyMCMMrihCHuUVScnXV8wkZcT/39q7b9199z1n3bqD697zr19fZ519/2fftfda37lbpLW2g6fgK9hi4sfAu3BvU4iNAifBK/ARPAC1cG8auBHivF8HD8EtsDCMaUdev0XgNvgsOtd64LHoZ1eHcZPBtRCLfuQJ2AVGhnFtaRt4Ce6AMSE2AhwHM+Mgo/PgpmgiraaITn6jie0Eb8AME/PK67dENHErTYzzPwWWmVjObxK4B/aYmEt8wEGwHnwHq0KcD2Gc960miK787iROcZJcUX6RqB1gCMw3Ma+8fqyUt2B6uF4guqisptlxkOT9KHreB+OSeKH4sMOiO4077oJoslaI7sRUfOgn0fupOIE6GB+up4brQ9K8AB55/VgB10NsDjgS4lxkW4Kpn41zx+aqq6WYgLh1t4r2unkhlksO4yyVuLpWV8ALMADugkdgsR3Qpjx+sQI4b5bhL9FE5EQ/JjkVY23vOCYr9gE2ZD58Pzgq+eTY1bVK+we9nplrirv1IrjcgjXDQ11+VNrfNot+H+6qdXGQNPvZOH0HknihYn/jh6P2gS/gRLhvxcnUJd/fuDtZwrF/xAnlxnrk9Uv721jR8lwbiEr9ovj512BuEi9U7G9WLNNv0jxBKl1dq7R/cNV/gg2iz5kV4l55/XIVwF54TvQ/ZlTqR/F78JVquYmViluWvWFQGpPECZyWxv7G/1AHRPvMH9H3oaXhHt+PzoAPojuVCzFadAXfi5Y98a6o168GLoEf4LkMlzvf/X6LVg6V+sVxTNhZMDGM6yrxC/N1gH87oU77VarUxfpbUUqlSl0o/hCujpX+s2MlfqnUw8rrl3sx5/x79liJk01PKqy8funPrp4/VipLnNev746VyhLn8ev5YyWu/F5pPEZiA79qrvl7OPa8Mr+otL/1xbFS0Y7z+qX9rS+OlYoS5/XLVUDPHyvlEuf1q0kfHyvlElekMr+O6x9QzX+z3EDVYgAAAABJRU5ErkJggg==>