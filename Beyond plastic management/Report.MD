Date: 2025-03-15
Author: Rena Mizuno 


# 1. Introduction
## 1.1 Background

Plastic mismanagement has been recognised as a dominant issue that needs to be solved for global protection. Since the rapid increase in plastic production since 1950 and its waste, this planet is highly likely to be polluted with plastic. Annual plastic production was more than 40 billion in 2020(Figure 1), and the prediction indicates that approximately 120 billion plastic will be produced in 2060(Figure 2). Most disposal plastics, such as plastic bags and packages, have been classified as landfilled, as the data shows; the landfill rate is the highest globally among the plastic waste categories of landfill, recycling, incineration and mismanagement. Besides recycling, plastics likely transform into microplastics or toxic chemicals in various ways and pollute the environment. For example, incineration pollutes the air, mismanagement damages marine life, and landfills intoxicate the soil, which destroys the ecosystem. 
Plastic materials are used not only in plastic bags and bottles of water but also in clothes and electronic devices. As the prevailing lifestyle is an overreliance on plastic, it is pivotal to reduce mismanagement and minimise plastic consumption by proper recycling or refraining from disposing of plastic items. 

![Figure 1](https://github.com/RenaMizuno/REPORT/blob/main/Beyond%20plastic%20management/figures/Figure%201.png?raw=true)
![Figure 2](https://github.com/RenaMizuno/REPORT/blob/main/Beyond%20plastic%20management/figures/Figure%202.png?raw=true)

## 1.2 Objectives

Post-research about correlations between education and economic growth revealed significance [[1](#references)]. The richer the countries become, the more money the government dedicates to education. When people are educated and skilled, the chance of obtaining an occupation with a higher salary is raised. Subsequently, more money was used to promote economic growth.  This trend could be observed not only at the societal level but also at the individual level. The higher GDP per capita countries showed this tendency for more citizens to spend on education for postsecondary school in developing countries like Luxemburg [[2](#references)].
However, economic growth does not always correlate to significant practical plastic waste management changes. Despite the fact that GDP growth is upward in all region and their considerable growth,  some regions show distinctive trends, notably the world-leading country, the USA. Its GDP score was 10 to 21 trillion between 2000 and 2020, the highest economic growth(Figure 3). Yet, no significant improvement in plastic waste management was observed, although the quality of education(goal 4 in SDG) was maintained at over 90%(Figure 4). In contrast, China ranked 2nd largest economic growth country, experienced rapid growth from 1.2 to 14 trillion with a constant quality education rate of 97%, dramatically improving plastic waste management in mismanagement. India, the country with the third highest GDP, followed this trend in plastic waste mismanagement on a smaller scale in terms of GDP from 0.4 to 2 trillion and a gradual increase in quality education from 60 to 80%. These two Asian countries showed similar plastic management trends with different GDP scores. Conversely, Europe reflected a constant education rate and stable economic growth upon improvements in landfill management, although the GDP level is much lower than in India.
This correlational study aims to reveal how much education and economic growth influence plastic management change by category and which regions are significant. Since each continent and country has different features, it is noteworthy to detect the discrepancy between them from heterogeneous perspectives so that the thriving region can be a model of the countries that suffer ongoing stagnation with improvement in SDG goals [[3](#references)]. 

![Figure 3](https://github.com/RenaMizuno/REPORT/blob/main/Beyond%20plastic%20management/figures/Figure%203.png?raw=true)
![Figure 4](https://github.com/RenaMizuno/REPORT/blob/main/Beyond%20plastic%20management/figures/Figure%204.png?raw=true)

## 1.3 Research Question

The research question is: "How do different parts of society influence plastic waste management, and where can we see correlations in plastic management improvement by comparing the education and economic growth rate?". To explore which countries or continents have unique characteristics contributing to plastic management, this correlational research was done by using the score of Quality education (Goal 4) and Decent work and economic growth (Goal 8) from the dataset of SDGs from the United Nations. Classifying the world by continent and world-leading countries in GDP - USA, China and India. Also, potential causalities, such as education curricula, the regulation of garbage collection, and policy, will be discussed accordingly. 


# 2.Theoretical Framework
Previous research on the correlations between economic growth and quality education revealed positive results, which seems true as the linear regression line rises upwards (Figure 5). Regarding sustainability study,“ (...) 1% increase in individual environmental knowledge leads to a 0.4% increase in environmental behaviour among university students through model estimation.”[[4](#references)].  Based on this perspective, the correlation between Goal 4 and Goal 8 in SDGS correlates theoretically positively with plastic management improvement. However, as Makarenko.I. et al., 2021 indicated, “(...)there is no “correct” way to assess the level of achievement of sustainable development goals”, and integrating higher education is needed for SDG 4 implementation [[5](#references)]. Nevertheless, they also concluded that education is the basis of economic growth as it provides a “knowledge-based economy”[[6](#references)]. Based on this research result, the strong correlation between education and economic growth is regarded as a knowledge-based economy that results in sustainable economic and education development.
 This research employed Spearman’s Correlation Coefficient (ρ)  mainly because of the previous research about the SDG score conducted by Pakkan. S. et al. 2022 stated that “Spearman’s Correlation Coefficient (ρ) provides a measure to evaluate the strength of an association between two variables” and “can capture the nonlinear correlation between the variables and is less sensitive to outliers. Spearman’s analysis is widely used to identify general relations beyond the linear correlation between two variables in various disciplines (Spearman 1987) ”[[7](#references)].

![Figure 5](https://github.com/RenaMizuno/REPORT/blob/main/Beyond%20plastic%20management/figures/Figure%205.png?raw=true)

# 3. Methodology

## 3.1 Data Collection

The primary dataset of SDGs and plastic management was cited from Kaggle. The SDG database is the same as the prototype on the United Nations’ website. The number of datasets used was minimised to avoid measurement error. Therefore, based on these two datasets, this research was conducted to observe three correlations of education, economic growth, and plastic management. In addition, the other CSV files stemming from the same plastic management datasets were used to predict plastic production and detect countries matching the plastic management dataset by region used as the primary dataset in this research. In addition, a GDP dataset in US dollars was used to visualise the overview of respective trends (matplotlib and seaborn were used for most data visualisation). 
Preprocessing was executed by modifying the names of columns in one dataset to match another so that these datasets could be merged(pandas). Then, data cleaning was processed by detecting the empty values; however, no missing values were detected. Subsequently, sampling size was extracted by extracting matching countries by their name and country codes. The sample size of countries extracted was approximately 70 % of those listed in the SDG data (N = 195, n = 140). For this research, Spearman correlation was mainly employed, as mentioned in the theoretical framework section. In the process of data analysis, Fisher’s z standardisation was applied to the result of Spearman correlation so that all the data could be appropriate for correlational research.  Data was mainly visualised in line graphs and heat maps. When all the data was combined for a holistic correlation approach, standardising all the data above was applied and they were visualised individually in a biplot to visualise the tendencies in one place.

## 3.2 Data Analysis Methods

  Firstly, SDG and plastic management datasets were tested to clarify their distribution. The data from Goal 4 and Goal 8, plastic waste management skewness and kurtosis analysis, and Shapiro-Wilk and KS tests(scipy.stats). Also, the value in the column named year was converted in string type”.astype(str)” to display the year in a discrete-continuous number. Both values for Goal 4 and Goal 8 are skewed, although Goal 4 is significantly negatively skewed, while Goal 8 is almost normally distributed but still skewed. Also, plastic management data in 4 categories are skewed considerably. As all the distribution is skewed, the Spearman correlation is mainly employed in this research. Due to the outliers and smaller continents in a sample size such as Oceania(n = 12),  Kendall Tau is also applied for the regional research. Moreover,  Fischer's z-transformation was applied to the Spearman correlation of Goal 4 and plastic managers and Goal 8 and plastic management. 
Subsequently, the SDG and plastic waste management datasets were visualised: By calculating the median of correlations between Goal 4, Goal 8, and plastic waste rate by category, the respective distribution by region of correlation scores were clarified. After that, the p-value of the correlation between Goal 4 and plastic management Goal 8 and plastic management were calculated at the global and continent levels to determine the statistical significance. Then, Spearman correlations were calculated and visualised in heat maps to assess the regional tendency of plastic waste management by category. Fisher’s Z test was also employed to check if these correlations were statistically different across datasets or groups. Lastly, unsupervised machine learning of Principal Component Analysis (PCA) was used to uncover hidden patterns visually. The value was standardised to merge all the values in one place (sklearn.decomposition for PCA, sklearn.preprocessing to import StandardScaler).

## 3.3 Limitations
The limitations of this research are measurement inconsistency and accuracy. As different measurements were used to collect the data on plastic management rates and SDGs, it would be controversial to confirm the statistical accuracy, although the relatively larger sample size extracted via matching countries proceeded. Also, the SDG data collection may have different measurements before and after 2015, when the SDG goals were settled. 
The dataset on quality of education might also include people who have completed post-secondary and higher education, especially in developed countries. Considering this, some countries and continents do not accurately reflect the education level. For example, European citizens may have completed higher education, such as a bachelor's degree. On the other hand, other countries are not this case.  
Moreover, ceiling limitation is another issue when data analysis is conducted, as all the data are converted into percentages. For future study, the data with absolute numbers - the population, the number of competition of higher education in detail and GSP in US dollars will be needed.

# 4.Findings

This research uncovered distinctive features in the relationship between education and plastic waste management, as well as economic growth and plastic waste management. As the Spearman correlation coefficient of education and economic growth revealed that the hypothesised correlation between education and economic growth is recognised as true, as most regions showed a positive correlation (p-value< 0.05). However, the United States and China showed statistical insignificance (Spearman r / Spearman rho respectively 0.210593/ 3.728144e-01, 0.354379/1.252668e-01). (Figure 6) Regarding the correlation between Goal 4, Goal 8 and plastic management at the global level, it is remarkable that Goal 4 and Goal 8 each contribute to improving plastic management (Figure 7), especially littering. These two showed a similar trend. However, quality of education showed a slightly stronger correlation than GDP in all categories with statistical significance (all p-values except USA < 0.05).  However, this trend mainly reflects China and India, and MENA and Sub-Saharan Africa follow the trend; the littering rate decreased significantly while the scores in the other categories rose considerably(Figure 8). Countries like Europe, Oceania, Asia excluding India and China showed a more significant decrease in landfilled and littered scores while the other scores rose moderately. 
The USA, however, shows the opposite tendency in that the negative correlation between recycling and incineration is significant for Goal 8 and plastics management but not for Goal 4 (p <0.05).  Besides, the USA showed a stronger correlation between Goal 8 and plastics management than the one between Goal 4 and plastics management. Consequently, the regional trend can be categorised into three distinct groups: the USA as a distinct entity, China, India, MENA, and the African region and others.

![Figure 6](https://github.com/RenaMizuno/REPORT/blob/main/Beyond%20plastic%20management/figures/Figure%206.png?raw=true)
![Figure 7](https://github.com/RenaMizuno/REPORT/blob/main/Beyond%20plastic%20management/figures/Figure%207.png?raw=true)
![Figure 8](https://github.com/RenaMizuno/REPORT/blob/main/Beyond%20plastic%20management/figures/Figure%208.png?raw=true)

The PCA biplot visualised the correlation between 3 factors, and different correlations and regional features were detected(Figure 9). Firstly, recycling & incineration are positioned close together, which could be interpreted to positively correlate with better education & economic growth, such as in Europe. Littering & Landfilling are positioned in the opposite direction, indicating that they are more common in regions where education & employment might be lower, such as Sub-saharan Africa and India. Middle East, North Africa, and the Americas show a mix of different waste management practices. However, it shows a moderate increase in recycling and landfilling. China is somewhere between this trend. Therefore, the country is in transition of improvement. However, the USA described a strong association with landfilling. This could derive from a weak link between education and plastic waste management but a stronger connection with economic growth.
Considering the findings above, regions with higher SDG Goal 4 and 8 scores (education & employment) tend to have better plastic waste management (more recycling/incineration). In contrast, countries with lower SDG scores show higher reliance on landfilling & littering. However, education & economic development at lower levels still encourage recycling & incineration instead of landfilling & littering. The USA is an exception as only economic growth related to plastic management does not influence plastic waste management efficiency and reliance on landfills, despite the constant high education rate and economic strength. In other words, recycling & incineration are driven by higher SDG scores (Goal 4 and 8), and countries with strong education and economies manage plastic waste more effectively.  Europe is recognised as a model for achieving Goal 4 and Goal 8 effectively, as it is the world-leading continent in sustainable waste management. Assumably, it has better education, economic growth, and advanced plastic waste management strategies.

![Figure 9](https://github.com/RenaMizuno/REPORT/blob/main/Beyond%20plastic%20management/figures/Figure%209.png?raw=true)

# 5.Discussion
 Compared to the prior research, it concluded the general trend of GDP and education. Therefore, the USA’s trend of a stronger correlation between economic growth and landfills was an unexpected finding. Considering this point, it is noteworthy to discuss the potential casualties of this trend in order not to follow this trend for further development. This could be derived from their business model or culture of prioritising pursuing profit rather than sustainability or the lack of a strong recycling culture in the US, which may be a contributing factor. Besides,  high plastic waste generation without efficient recycling solutions could be the factor. It might be because the USA does not have a great infrastructure for plastic waste management, unlike Europe[[8](#references)]. The other aspect would be that the majority of citizens have only completed up to secondary school, not university or college, due to financial difficulties. Since tuition fees for public universities are reasonable, while the USA may represent the value of up to secondary school completion due to the higher tuition fee(the annual tuition fee of In-Public in the USA costs  $9,740 in 4 year In-State and $3598 2-year In-District at least [[9](#references)]).


# 6.Conclusions
The correlation between education and economic growth is positive. However, GDP alone does not improve plastic waste management, as the case of the USA shows. A further factor that can enhance environmental behaviour would be constant high SDG scores and higher education completion, such as university, to apply the knowledge gained from sustainability education. This requires government financial support. As a matter of fact,  students in the USA likely struggle with the cost of living during their studies due to the high tuition fees for post-secondary education, while European countries have excellent educational services at affordable prices for citizens,
As some countries experienced stagnation in the improvement of the score and a high rate of littering, the European model may offer a viable solution, albeit Europe itself may need further improvement in decreasing the incarceration rate.  Not only education funded by governments but also the ecosystem and selling plastic-free products encourage the consumer to be eco-friendly, such as German vending machines recycling cans and plastic bottles with a refund of credit for materials.  Therefore, practical social frameworks should be introduced to the prevailing society so that recycling becomes a habit.

## References

[1] Bah. I. A., “The relationship between education and economic growth: A cross-country analysis”, Research Society and Development 12(5):e19312540522,
2023. May,
https://www.researchgate.net/publication/370993206_The_relationship_between_education_and_economic_growth_A_cross-country_analysis

[2] “Education Expenditures by Country”, National Centre for Education Statistic, Figure 4. Expenditures per full-time-equivalent (FTE) student for postsecondary education in selected Organization for Economic Cooperation and Development (OECD) countries, by gross domestic product (GDP) per capita: 2019 2023.08, https://nces.ed.gov/programs/coe/indicator/cmd/education-expenditures-by-country

[3] UNESCO Institute for Statistics, Global Education Monitoring Report Team, ”Meeting commitments: are countries on track to achieve SDG 4?”, UNESCO UIS, p.14, 2019, https://uis.unesco.org/sites/default/files/documents/meeting-commitments-are-countries-on-track-achieve-sdg4.pdf

[4] Liu. J, Hu. Z,  Du. F, Tang. W, Zheng. S, Lu. S, An. A, Ding .J, “Environment education: A first step in solving plastic pollution”, 2023, https://www.frontiersin.org/journals/environmental-science/articles/10.3389/fenvs.2023.1130463/full, frontiers

[5] Makarenko.I., Plastun.A, Petrushenko.Y.,Vorontsova. A., Alwasiak. S., “SDG 4 and SDG 8 in the knowledge economy: A meta-analysis in the context of post-COVID-19 recovery”
, p.60, 2021, https://www.businessperspectives.org/images/pdf/applications/publishing/templates/article/assets/15921/KPM_2021_01_%20Makarenko.pdf

[6] Makarenko.I., Plastun.A, Petrushenko.Y.,Vorontsova. A., Alwasiak. S., “SDG 4 and SDG 8 in the knowledge economy: A meta-analysis in the context of post-COVID-19 recovery”
, p.63, 2021, https://www.businessperspectives.org/images/pdf/applications/publishing/templates/article/assets/15921/KPM_2021_01_%20Makarenko.pdf

[7] Pakkan. S., Sudhakar. C., Shubham Tripathi. S., Rao. M., “A correlation study of sustainable development goal (SDG) interactions”, Springer Nature Link, 2022
https://link.springer.com/article/10.1007/s11135-022-01443-4

[8] Turner.K., Kim.Y.,”Problems of the US Recycling Programs: What Experienced Recycling Program Managers Tell”, Sustainability 2024, 16(9), 2024, ;https://www.mdpi.com/2071-1050/16/9/3539


[9] Hanson. M., (2025.03.08)“Average Cost of College & Tuition”, Education Data Initiative,
https://educationdata.org/average-cost-of-college#:~:text=The%20average%20cost%20of%20attendance,or%20%24234%2C512%20over%204%20years.

Other references:

Hanson. M., (2025.03.08)“Average Cost of College & Tuition”, Education Data Initiative,
https://educationdata.org/average-cost-of-college#:~:text=The%20average%20cost%20of%20attendance,or%20%24234%2C512%20over%204%20years.

Kibria. M, Masuk. N, Safayet. R, Nguyen. H, Mourshed. M, “Plastic Waste: Challenges and Opportunities to Mitigate Pollution and Effective Management”, National Library of Medicine, 2023
https://pmc.ncbi.nlm.nih.gov/articles/PMC9857911/
Rojec. M, Knell. M, “WHY IS THERE A LACK OF EVIDENCE ON KNOWLEDGE SPILLOVERS FROM FOREIGN DIRECT INVESTMENT?”,2017, https://onlinelibrary.wiley.com/doi/full/10.1111/joes.12207 

Suárez-Perales. I. , Valero-Gil. J , Hiz. D., Rivera-Torres. P., Garcés-Ayerbe. C.,“Educating for the future: How higher education in environmental management affects pro-environmental behaviour”, ScienceDirect, 2021
https://www.sciencedirect.com/science/article/pii/S0959652621031632
Tan. J, Yu. X,  Chen. Q, Liang. R(01.2022), “Education Inequality in the United States”, ATLANTIS PRESS, ResearchGate, https://www.researchgate.net/publication/360013963_Education_Inequality_in_the_United_States

Wojnowska-Baryła. I., Katarzyna Bernat. K., Zaborowska. M. (2022.10.14) ” Plastic Waste Degradation in Landfill Conditions: The Problem with Microplastics, and Their Direct and Indirect Environmental Effects”, National Library of Medicine
https://pmc.ncbi.nlm.nih.gov/articles/PMC9602440/

“Education”, United Nations, (n.d.),
https://sdgs.un.org/topics/education , 
“GOAL 4: QUALITY EDUCATION” UNICEF, (n.d.), https://data.unicef.org/sdgs/goal-4-quality-education/ ,

“ENVIRONMENTAL AND HEALTH IMPACTS OF OPEN BURNING”, Wisconsin Department of Natural Resources,(n.d.)
https://dnr.wisconsin.gov/topic/OpenBurning/Impacts.html#:~:text=Impacts%20of%20Smoke%20from%20Burning%20Trash%20and%20Plastic&text=Burning%20plastic%20and%20treated%20wood,been%20shown%20to%20cause%20cancer.

“SDG 4 and SDG 8 in the knowledge economy: A meta-analysis in the context of post-COVID-19 recovery”
https://www.businessperspectives.org/index.php/journals/knowledge-and-performance-management-2/issue-390/sdg-4-and-sdg-8-in-the-knowledge-economy-a-meta-analysis-in-the-context-of-post-covid-19-recovery

“The Sustainable Development Goals Report 2024”, United Nations, 2024, https://unstats.un.org/sdgs/report/2024/The-Sustainable-Development-Goals-Report-2024.pdf

# Appendix

Momeni, M., “Plastic pollution”, Kaggle, 2023  https://www.kaggle.com/datasets/imtkaggleteam/plastic-pollution?resource=download 

Tas, O. C. “World GDP”, Kaggle, 2021 https://www.kaggle.com/datasets/zgrcemta/world-gdpgdp-gdp-per-capita-and-annual-growths?resource=download

Islam, S., “Sustainable Development Data” Kaggle, 2023, https://www.kaggle.com/datasets/sazidthe1/sustainable-development-report?select=sdg_index_2000-2022.csv 

