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
Preprocessing was executed by modifying the names of columns in one dataset to match another so that these datasets could be merged(pandas).
Then, data cleaning was processed by detecting the empty values; however, no missing values were detected. Subsequently, sampling size was extracted by extracting matching countries by their name and country codes. The sample size of countries extracted was approximately 70 % of those listed in the SDG data (N = 195, n = 140). For this research, Spearman correlation was mainly employed, as mentioned in the theoretical framework section. In the process of data analysis, Fisher’s z standardisation was applied to the result of Spearman correlation so that all the data could be appropriate for correlational research.  Data was mainly visualised in line graphs and heat maps. When all the data was combined for a holistic correlation approach, standardising all the data above was applied and they were visualised individually in a biplot to visualise the tendencies in one place.
'''
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
import textwrap
import statsmodels.api as sm
from scipy.stats import pearsonr, ttest_ind, skew, kurtosis, shapiro, kstest ,spearmanr, kendalltau, fisher_exact
from sklearn.linear_model import LinearRegression
from sklearn.preprocessing import StandardScaler
from sklearn.decomposition import PCA

#Dataset from kaggle:
#df3 and df4 are same datasets, therefore, matching countries among 3 different datasets
#were extracted as'country_groups' and 'continent_mapping' shows. 
df3 = pd.read_csv("3- share-plastic-fate.csv")
df4 = pd.read_csv("4- mismanaged-plastic-waste-per-capita.csv")
df_sdg= pd.read_csv('sdg_index_2000-2022.csv')
dfgdp = pd.read_csv('gdp.csv')

df_sdg["year"] = df_sdg["year"].round().astype(int)  # Rounds and converts to int
df_filtered = df_sdg[(df_sdg["year"] >= 2000) & (df_sdg["year"] <= 2020)].copy()
df_sdg = df_sdg[df_sdg["year"] % 1 == 0]  


columns_to_keep = ['Country Name', 'Code'] + [str(year) for year in range(2000, 2021)]
filtered_dfgdp = dfgdp[columns_to_keep]
output_file_path = 'filtered_dfgdp_2000_2020.csv' 
filtered_dfgdp.to_csv(output_file_path, index=False)
gdp = pd.read_csv('filtered_dfgdp_2000_2020.csv')

#Making the list of countries by continent

country_groups = {
    "China": ["China"],
    "India": ["India"],
    "Asia (excl. China and India)": [
        'Bangladesh', 'Brunei', 'Cambodia', 'Hong Kong', 'Indonesia', 'Japan', 
        'Kazakhstan', 'Korea, Rep.', 'Malaysia', 'Maldives', 'Myanmar', 'Pakistan', 
        'Philippines', 'Singapore', 'Sri Lanka', 'Thailand', 'Vietnam'
    ],
    "Oceania": [
        'Australia', 'Fiji', 'Kiribati', 'Marshall Islands', 'New Zealand', 'Palau', 
        'Papua New Guinea', 'Samoa', 'Solomon Islands', 'Tonga', 'Timor-Leste'
    ],
    "United States": ["United States"],
    "Americas (excl. USA)": [
        'Antigua and Barbuda', 'Argentina', 'Barbados', 'Belize', 'Brazil', 'Canada', 
        'Chile', 'Colombia', 'Costa Rica', 'Dominica', 'Dominican Republic', 'Ecuador', 
        'El Salvador', 'Grenada', 'Guatemala', 'Guyana', 'Honduras', 'Jamaica', 
        'Mexico', 'Panama', 'Peru', 'Puerto Rico', 'Suriname', 'Trinidad and Tobago', 
        'Uruguay', 'Venezuela', 'Bahamas', 'Haiti', 'Nicaragua', 'Saint Kitts and Nevis', 
        'Saint Lucia', 'Saint Vincent and the Grenadines', 'Sao Tome and Principe'
    ],
    "Middle East & North Africa": [
        'Algeria', 'Bahrain', 'Cyprus', 'Egypt', 'Iran', 'Iraq', 'Israel', 'Jordan', 
        'Kuwait', 'Lebanon', 'Libya', 'Morocco', 'Oman', 'Palestine', 'Qatar', 
        'Saudi Arabia', 'Sudan', 'Syria', 'Tunisia', 'Turkey', 'United Arab Emirates', 'Yemen'
    ],
    "Sub-Saharan Africa": [
        'Benin', 'Burkina Faso', 'Cameroon', 'Gabon', 'Ghana', 'Kenya', 'Lesotho', 
        'Liberia', 'Madagascar', 'Mauritania', 'Nigeria', 'Senegal', 'Seychelles', 
        'Sierra Leone', 'Somalia', 'South Africa', 'Togo', 'Zimbabwe', 'Angola', 'Comoros', 
        'Congo', 'Ivory Coast', 'Democratic Republic of the Congo', 'Djibouti', 
        'Equatorial Guinea', 'Eritrea', 'Gambia', 'Guinea', 'Guinea-Bissau', 
        'Mozambique', 'Namibia', 'Tanzania'
    ],
    "Europe": [
        'Albania', 'Belgium', 'Bosnia and Herzegovina', 'Bulgaria', 'Croatia', 'Denmark', 
        'Estonia', 'Finland', 'France', 'Georgia', 'Germany', 'Greece', 'Iceland', 'Ireland', 
        'Italy', 'Latvia', 'Lithuania', 'Malta', 'Monaco', 'Netherlands', 'Norway', 'Poland', 
        'Portugal', 'Romania', 'Russia', 'Slovakia', 'Slovenia', 'Spain', 'Sweden', 
        'Ukraine', 'United Kingdom', 'Montenegro'
    ]
}


continent_mapping = {
    'CHN': 'China',
    'IND': 'India',
    'USA': 'United States',
    **{code: 'Asia (excl. China and India)' for code in ['BGD', 'BRN', 'KHM', 'HKG', 'IDN', 'JPN', 'KAZ', 'MYS',
        'MDV', 'MMR', 'PRK', 'PAK', 'PHL', 'SGP', 'KOR', 'LKA', 'THA', 'VNM']},
    **{code: 'Oceania' for code in ['AUS', 'FJI', 'KIR', 'MHL', 'NZL', 'PLW', 'PNG', 'WSM', 'SLB', 'TON', 'TLS']},
    **{code: 'Americas (excl. USA)' for code in ['ATG', 'ARG', 'BRB', 'BLZ', 'BRA', 'CAN', 'CHL', 'COL', 'CRI', 'DMA',
        'DOM', 'ECU', 'SLV', 'GRD', 'GTM', 'GUY', 'HND', 'JAM', 'MEX', 'PAN', 'PER', 'PRI', 'SUR', 'TTO', 'URY', 'VEN',
        'BHS', 'HTI', 'NIC', 'KNA', 'LCA', 'VCT', 'STP']},
    **{code: 'Middle East & North Africa' for code in ['DZA', 'BHR', 'CYP', 'EGY', 'IRN', 'IRQ', 'ISR', 'JOR', 'KWT',
        'LBN', 'LBY', 'MAR', 'OMN', 'PSE', 'QAT', 'SAU', 'SDN', 'SYR', 'TUN', 'TUR', 'ARE', 'YEM']},
    **{code: 'Sub-Saharan Africa' for code in ['BEN', 'BFA', 'CMR', 'GAB', 'GHA', 'KEN', 'LSO', 'LBR', 'MDG', 'MRT',
        'NGA', 'SEN', 'SYC', 'SLE', 'SOM', 'ZAF', 'TGO', 'ZWE', 'AGO', 'COM', 'COG', 'CIV', 'COD', 'DJI', 'GNQ', 'ERI',
        'GMB', 'GIN', 'GNB', 'MOZ', 'NAM', 'TZA']},
    **{code: 'Europe' for code in ['ALB', 'BEL', 'BIH', 'BGR', 'HRV', 'DNK', 'EST', 'FIN', 'FRA', 'GEO', 'DEU', 'GRC',
        'ISL', 'IRL', 'ITA', 'LVA', 'LTU', 'MLT', 'MCO', 'NLD', 'NOR', 'POL', 'PRT', 'ROU', 'RUS', 'SVK', 'SVN', 'ESP',
        'SWE', 'UKR', 'GBR', 'MNE']}
}

# The empty value in country is filled with 'Others '
df_sdg['continent'] = df_sdg['country_code'].map(continent_mapping).fillna('Others')
df_sdg.to_csv("sdgupdated_file.csv", index=False)

df_sdg["year"] = df_sdg["year"].astype(int)
df_sdg["country_code"] = df_sdg["country_code"].astype(str)

#Changing the name of the column to merge df3 to df_sdg 
plastic_df = df3.rename(columns={
    'Code':'country_code',
    'Year': 'year',
    'Entity':'continent',
    'Share of waste recycled from total regional waste': 'recycled', 
    'Share of waste incinerated from total regional waste': 'incinerated',
    'Share of littered and mismanaged from total regional waste': 'littered', 
    'Share of waste landfilled from total regional waste': 'landfilled'}) 


waste_categories = ['recycled', 'incinerated', 'littered', 'landfilled']

plastic_df["year"] = plastic_df["year"].astype(int)
plastic_df["country_code"] = plastic_df["country_code"].astype(str)
merged_df = pd.merge(df_sdg, plastic_df, on=['continent',"year"], how="inner")


#Checking distribution of goal 4 and goal 8
sns.histplot(merged_df["goal_4_score"], kde=True, bins=20)
plt.title("Distribution of Goal 4 Score")
plt.show()

sns.histplot(merged_df["goal_8_score"], kde=True, bins=20)
plt.title("Distribution of Goal 8 Score")
plt.show()

# Calculate skewness & kurtosis 
goal4_skew = skew(merged_df["goal_4_score"])
goal8_skew = skew(merged_df["goal_8_score"])
goal4_kurt = kurtosis(merged_df["goal_4_score"])
goal8_kurt = kurtosis(merged_df["goal_8_score"])

print(f"Goal 4 Skewness: {goal4_skew}, Kurtosis: {goal4_kurt}")
print(f"Goal 8 Skewness: {goal8_skew}, Kurtosis: {goal8_kurt}")

#Normality Tests (Shapiro-Wilk & KS Test)
shapiro_test_goal4 = shapiro(merged_df["goal_4_score"])
shapiro_test_goal8 = shapiro(merged_df["goal_8_score"])

print(f"Shapiro-Wilk Test for Goal 4: Statistic={shapiro_test_goal4.statistic}, p-value={shapiro_test_goal4.pvalue}")
print(f"Shapiro-Wilk Test for Goal 8: Statistic={shapiro_test_goal8.statistic}, p-value={shapiro_test_goal8.pvalue}")

ks_test_goal4 = kstest(merged_df["goal_4_score"], 'norm')
ks_test_goal8 = kstest(merged_df["goal_8_score"], 'norm')

print(f"KS Test for Goal 4: Statistic={ks_test_goal4.statistic}, p-value={ks_test_goal4.pvalue}")
print(f"KS Test for Goal 8: Statistic={ks_test_goal8.statistic}, p-value={ks_test_goal8.pvalue}")

#df3 skewness
for category in waste_categories:
    skewness = skew(merged_df[category])
    kurt = kurtosis(merged_df[category])
    shapiro_test = shapiro(merged_df[category])

    print(f"Plastic Waste Category: {category}")
    print(f"Skewness: {skewness}, Kurtosis: {kurt}")
    print(f"Shapiro-Wilk Test: Statistic={shapiro_test.statistic}, p-value={shapiro_test.pvalue}")
    print("-" * 50)
    
for i, category in enumerate(waste_categories, 1):
    plt.subplot(2, 2, i)
    sns.histplot(merged_df[category], kde=True, bins=30, color="blue")
    plt.axvline(merged_df[category].mean(), color='red', linestyle='dashed', linewidth=1)  # Mean line
    plt.title(f"Distribution: {category} ")
    plt.xlabel("Percentage")
    plt.ylabel("Frequency")

plt.tight_layout()
'''

## 3.2 Data Analysis Methods

  Firstly, SDG and plastic management datasets were tested to clarify their distribution. The data from Goal 4 and Goal 8, plastic waste management skewness and kurtosis analysis, and Shapiro-Wilk and KS tests(scipy.stats). Also, the value in the column named year was converted in string type”.astype(str)” to display the year in a discrete-continuous number. Both values for Goal 4 and Goal 8 are skewed, although Goal 4 is significantly negatively skewed, while Goal 8 is almost normally distributed but still skewed. Also, plastic management data in 4 categories are skewed considerably. As all the distribution is skewed, the Spearman correlation is mainly employed in this research. Due to the outliers and smaller continents in a sample size such as Oceania(n = 12),  Kendall Tau is also applied for the regional research. Moreover,  Fischer's z-transformation was applied to the Spearman correlation of Goal 4 and plastic managers and Goal 8 and plastic management. 
Subsequently, the SDG and plastic waste management datasets were visualised: By calculating the median of correlations between Goal 4, Goal 8, and plastic waste rate by category, the respective distribution by region of correlation scores were clarified. After that, the p-value of the correlation between Goal 4 and plastic management Goal 8 and plastic management were calculated at the global and continent levels to determine the statistical significance. Then, Spearman correlations were calculated and visualised in heat maps to assess the regional tendency of plastic waste management by category. Fisher’s Z test was also employed to check if these correlations were statistically different across datasets or groups. Lastly, unsupervised machine learning of Principal Component Analysis (PCA) was used to uncover hidden patterns visually. The value was standardised to merge all the values in one place (sklearn.decomposition for PCA, sklearn.preprocessing to import StandardScaler).
'''
#Calculating spearman and kendall correlation and visualisation in heat maps
def compute_correlations_by_continent(df, goal, waste_categories):
    correlation_results = []
    
    for continent, sub_df in df.groupby("continent"): 
        for category in waste_categories:
            spearman_corr, spearman_p = spearmanr(sub_df[goal], sub_df[category], nan_policy="omit")
            kendall_corr, kendall_p = kendalltau(sub_df[goal], sub_df[category], nan_policy="omit")
            
            correlation_results.append({
                "continent": continent,
                "goal": goal,  
                "plastic_category": category,
                "spearman_r": spearman_corr,
                "spearman_p": spearman_p,
                "kendall_tau": kendall_corr,
                "kendall_p": kendall_p
            })
    
    return pd.DataFrame(correlation_results)


# Compute correlations for Goal 4 & Goal 8
corr_goal_4 = compute_correlations_by_continent(merged_df, "goal_4_score", waste_categories)
corr_goal_8 = compute_correlations_by_continent(merged_df, "goal_8_score", waste_categories)

# Create subplots
fig, axes = plt.subplots(nrows=2, ncols=2, figsize=(16, 12))

# Function to format correlation & p-value in the heatmap
def format_value(corr, p_val):
    if np.isnan(corr):
        return "NaN"
    return f"{corr:.2f}\n(p={p_val:.2g})"

# Apply formatting
corr_goal_4["spearman_text"] = corr_goal_4.apply(lambda row: format_value(row["spearman_r"], row["spearman_p"]), axis=1)
corr_goal_8["spearman_text"] = corr_goal_8.apply(lambda row: format_value(row["spearman_r"], row["spearman_p"]), axis=1)
corr_goal_4["kendall_text"] = corr_goal_4.apply(lambda row: format_value(row["kendall_tau"], row["kendall_p"]), axis=1)
corr_goal_8["kendall_text"] = corr_goal_8.apply(lambda row: format_value(row["kendall_tau"], row["kendall_p"]), axis=1)

# Heatmaps with correlation & p-values


fig.suptitle('Figure 8: Spearman and Kendall Correlation, Goal 4, Goal 8 and plastic waste management by Region', fontsize=16)
sns.heatmap(
    corr_goal_4.pivot(index="continent", columns="plastic_category", values="spearman_r"),
    annot=corr_goal_4.pivot(index="continent", columns="plastic_category", values="spearman_text"),
    cmap="coolwarm", fmt="", linewidths=0.5, ax=axes[0, 0]
)
axes[0, 0].set_title("Spearman Correlation (Goal 4 vs Plastic Management)")

sns.heatmap(
    corr_goal_8.pivot(index="continent", columns="plastic_category", values="spearman_r"),
    annot=corr_goal_8.pivot(index="continent", columns="plastic_category", values="spearman_text"),
    cmap="coolwarm", fmt="", linewidths=0.5, ax=axes[0, 1]
)
axes[0, 1].set_title("Spearman Correlation (Goal 8 vs Plastic Management)")

sns.heatmap(
    corr_goal_4.pivot(index="continent", columns="plastic_category", values="kendall_tau"),
    annot=corr_goal_4.pivot(index="continent", columns="plastic_category", values="kendall_text"),
    cmap="coolwarm", fmt="", linewidths=0.5, ax=axes[1, 0]
)
axes[1, 0].set_title("Kendall Correlation (Goal 4 vs Plastic Management)")

sns.heatmap(
    corr_goal_8.pivot(index="continent", columns="plastic_category", values="kendall_tau"),
    annot=corr_goal_8.pivot(index="continent", columns="plastic_category", values="kendall_text"),
    cmap="coolwarm", fmt="", linewidths=0.5, ax=axes[1, 1]
)
axes[1, 1].set_title("Kendall Correlation (Goal 8 vs Plastic Management)")

plt.tight_layout()
plt.show()


'''
'''
# Fisher's Z-test for correlation comparison

correlation_results = []
for category in waste_categories:
    spearman_corr_4, spearman_p_4 = spearmanr(merged_df["goal_4_score"], merged_df[category])
    spearman_corr_8, spearman_p_8 = spearmanr(merged_df["goal_8_score"], merged_df[category])
    
   
    if spearman_corr_4 is not None and spearman_corr_8 is not None:
        z_4 = np.arctanh(spearman_corr_4)
        z_8 = np.arctanh(spearman_corr_8)
        n = len(merged_df)
        se_diff = np.sqrt((1/(n-3)) + (1/(n-3)))
        fisher_z = (z_4 - z_8) / se_diff
    else:
        fisher_z = np.nan
    
    correlation_results.append({
        "plastic_category": category,
        "goal_4_spearman_r": spearman_corr_4,
        "goal_4_p_value": spearman_p_4,
        "goal_8_spearman_r": spearman_corr_8,
        "goal_8_p_value": spearman_p_8,
        "fisher_z": fisher_z
    })

correlation_df = pd.DataFrame(correlation_results)
print(correlation_df)

'''
'''
#Visualisation in PCA

# ===== Features for PCA =====
features = ["goal_4_score", "goal_8_score", "recycled", "incinerated", "littered", "landfilled"]
df_numeric = merged_df[features].dropna()

# ===== Standardize Data (PCA Requires Normalized Data) =====
scaler = StandardScaler()
scaled_data = scaler.fit_transform(df_numeric)


pca = PCA(n_components=2) 
pca_result = pca.fit_transform(scaled_data)

pca_df = pd.DataFrame(pca_result, columns=["PC1", "PC2"])
pca_df["continent"] = merged_df["continent"].values  # Add continent info back

# ===== Explained Variance =====
explained_variance = pca.explained_variance_ratio_

# ===== Biplot Function with Better Text Positioning =====
def biplot(pca, features, ax):
    loadings = pca.components_.T
    text_offsets = {  # Adjust offsets for readability
        "recycled": (1.0, 2.0),
        "incinerated": (3.0, 1.2),
        "littered": (2.0, -2.5),
        "landfilled": (1.8, 1.5),
        "goal_4_score": (3.3, 2.6),
        "goal_8_score": (3.3, -0.6),
    }
    
    for i, feature in enumerate(features):
        ax.arrow(0, 0, loadings[i, 0], loadings[i, 1], 
                 color="green", alpha=0.7, head_width=0.15)
        
        offset_x, offset_y = text_offsets.get(feature, (1.5, 1.5))  # Default offset if not specified
        ax.text(loadings[i, 0] * offset_x, loadings[i, 1] * offset_y, feature, 
                color="black", ha='center', va='center', fontsize=12, weight='bold')

# ===== Plot PCA Biplot =====
plt.figure(figsize=(10, 6))
ax = plt.gca()

sns.scatterplot(data=pca_df, x="PC1", y="PC2", hue="continent", alpha=0.6, ax=ax)

biplot(pca, features, ax)  # Add arrows and text labels

plt.title("Figure 9: PCA Biplot: Influence of SDGs & Plastic Waste Categories", fontsize=14)
plt.xlabel(f"Principal Component 1 ({explained_variance[0]*100:.2f}% Variance)")
plt.ylabel(f"Principal Component 2 ({explained_variance[1]*100:.2f}% Variance)")
plt.legend(title="Continent", bbox_to_anchor=(1, 1), loc='upper left')
plt.grid(False)
'''


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

