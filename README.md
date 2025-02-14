# Health Disparities in Taiwan: Trends in the Incidence of STIs and Implications for SDG 3
## Introduction
### Background
The United Nations Sustainable Development Goal 3 (SDG3) focuses on promoting
wellbeing and ensuring healthy lives for people of all ages. Despite Taiwan's advanced
healthcare system, disparities persist in healthcare access and outcomes, particularly
regarding the incidence of sexually transmitted infections (STIs) and the equitable
distribution of healthcare resources. With the use of national-level data for 1952–2022 and
county-level data for 2023, this study aims to analyze and identify patterns in health
disparities related with STIs and healthcare access in Taiwan from 1952 to 2023.
### Problem Statement
STIs remain a significant public health challenge in Taiwan, reflecting broader issues of healthcare accessibility and socioeconomic inequality. Despite Taiwan's significant advancements in healthcare, disparities in STI incidence and the distribution of healthcare resources continue to exist over time and regions. Understanding these disparities is essential to designing targeted interventions to address STI prevention and improve equitable healthcare access.
### Research Objectives
The objective of this study is to examine the multifaceted relationships between population density, socioeconomic status, healthcare access, and STI incidence rates in Taiwan. Specifically, the research aims to:
- Assess the influence of population density on STI transmission and evaluate how healthcare access moderates this relationship.
- Investigate how socioeconomic status shapes regional variations in STI incidence.
- Analyze national longitudinal trends to assess whether healthcare access improvements correspond with reductions in STI rates over time
## Literature Review
Existing literature highlights key findings on STI incidence, healthcare access, and socioeconomic disparities.<br>
STI Incidence:
- A more rapid increase in the number of cases of gonorrhea since 2013 could also be due to the more widespread use of molecular tests for the laboratory diagnosis of gonorrhea in the last 10 years (Chen et al., 2023).
- Several factors have been identified as significantly associated with late HIV diagnosis, including older age, having non-fixed sexual partners, and being diagnosed due to symptoms rather than through routine screening. These findings emphasize the importance of information and education delivered to the general population and health care providers, regular risk assessment, routine provision of HIV testing during medical encounters, and improving accessibility to voluntary HIV testing (Lin et al., 2021).<br>
Healthcare Access:
- Despite ongoing efforts to improve healthcare accessibility, our findings also underscore the persistence of health disparities between individuals residing in urban and resource-deprived areas over time (Hsieh et al., 2023).<br>
Socioeconomic:
- The higher the degree of socioeconomic development, the lower the standardized mortality rate regardless of the county or township level, and that education was the most important factor (Liu, 2021).
## Theoretical Framework and Hypotheses
### Theoretical Framework
Ecological Systems Theory: Health outcomes are shaped by multiple levels of influence, including individual, interpersonal, community, and societal factors (Reifsnider, et al., 2005).
- Macro-Level
  - Population Density: High population density can increase the frequency and intensity of social interactions, facilitating the transmission of STIs (Qiu, et al., 2019).
  - Social Disorganization Theory: In densely populated areas, social control mechanisms may weaken, leading to increased social disorganization and higher rates of risky behaviors, including those that contribute to STI transmission (Trepka, et al., 2022).
- Meso-level
  - Community Characteristics: Factors such as poverty, inequality, and access to community resources can influence STI transmission dynamics (Gonzalez, et al., 2008).
- Micro-level
  - Socioeconomic Status: Lower socioeconomic status is associated with increased risk of STI acquisition (Leval, et al., 2011).
  - Knowledge and Attitudes: Knowledge about STIs, perceived risk, and attitudes towards sexual health can influence preventive behaviors (Scheidell, et al., 2018).
### Hypotheses
The study employs a social determinants of health framework, which posits that health outcomes are influenced by the interplay of socioeconomic and healthcare factors. The hypotheses include:<br>

**H1** : While increased healthcare access will partially reduce the positive association between population density and STI incidence rates, high population density will remain a significant driver of STI transmission.<br>
**H2** : Regions with lower socioeconomic status and less healthcare access will experience higher STI incidence rates.<br>
**H3** : National improvements in healthcare access over time will correlate with a declining trend in STI incidence rates.
## Data Source
### Data Collection
| Topic | Information |
|--------|-------------|
| Source | Statistical Yearbook of the Republic of China 2023 |
| Data Format | XLS |
| Categories | Number of confirmed cases of notifiable diseases, General situation of medical institutions and registered medical personnel, Unemployment rates by educational attainment and age, and General situation of population. |

Level and period of data:
- National level from 1952 to 2023.
- County level only in 2023 data covers 22 cities and counties in Taiwan, specifically: New Taipei City, Taipei City, Taoyuan City, Taichung City, Tainan City, Kaohsiung City, Yilan County, Hsinchu County, Miaoli County, Changhua County, Nantou County, Yunlin County, Chiayi County, Pingtung County, Taitung County, Hualien County, Penghu County, Keelung City, Hsinchu City, Chiayi City, Kinmen County, and Lienchiang County.
### Variables
Dependent Variables:
- STI incidence rate (aggregate of Gonorrhea, Syphilis, HIV, and AIDS per 10,000 population).

Independent Variables:
- Healthcare Access
  - Registered medical personnel per km2 (RMP).
  - Healthcare facility (per 10,000 population including hospital and clinic).
- Socioeconomic
  - Unemployment rates.
- Population density (people per square kilometer).

Control Variables:
- Gender distribution (Male to Female ratio).
- Age distribution (percentage of population aged 15-64).
### Calculation
![Alt text](https://github.com/Sydnayy17/Health_Disparities/blob/main/Screenshot%202025-02-14%20194310.png)

### Data Cleaning and preparation
To reduce potential bias caused by geographical outliers, this study focuses on Taiwan's main island, excluding Kinmen and Lienchiang counties. Time series data at the national level has missing values due to historical record gaps, which is most likely a Missing Not at Random (MNAR) pattern. To improve prediction precision, this study uses ARIMA models to input missing data. The data will then be evaluated using time-series methods, and trends will be observed through statistical modeling and visualization. On the other hand, county-level data will be evaluated for spatial disparities using statistical tools.
## Methodology
### H1
A moderated regression model implemented where an interaction term between population density and healthcare access is included. This will show if health access moderated the association between population density and STI incidence. The model is specified as STI_Incidence ~ pop_dens * Healthcare_Access and implemented using the lm() function in R. The interaction term pop_dens * Healthcare_Access captures the extent to which healthcare access influences the effect of population density on STI rates. If the interaction term is significant, it implies that healthcare access alters the impact of population density on STI incidence. Meanwhile, the main effect of population density will show whether it remains a significant driver of STI transmission, even after accounting for healthcare access.
### H2
To identify the independent contributions of socioeconomic status (SES) and healthcare access to STI rates, a multivariable regression model is used to examine the simultaneous effects of SES and healthcare access on STI incidence rates. The model is specified as STI ~ Socioeconomic_Status + Healthcare_Access and is implemented using the lm() function in R. A negative coefficient for SES would reflect that the regions with lower SES have higher incidence of STIs, while a positive association for healthcare access would show that the avenue for reduction in STI rates is by increasing access to health resources.
### H3
In H3, using a time-series regression model to analyze trends in STI incidence rates over multiple years. The model is specified as STI_Incidence ~ Year + Healthcare_Access and implemented in R using the lm() function. By including the year variable, this model captures long-term trends in STI rates, while healthcare access serves as a key predictor of changes over time. A negative coefficient of the year variable indicates incidence rates of STI Incidence falling over time, while a significant and negative coefficient for the healthcare access proxy variable would reflect lower incidence rates, given better availability of healthcare services.
### Evaluate Model Assumptions
To ensure the results are reliable and valid regression models for hypothesis testing. First, verify the linearity between the dependent and independent variables by analyzing residual vs fitted plots. Check for homoscedasticity by using Scale-Location plots, and any violation should be addressed by using robust standard errors or variable transformation. The normality of residuals will be checked through QQ plots and the Shapiro-Wilk test; apply transformations if necessary. Check for multicollinearity using VIF, ensuring that the values are below 5. In cases of high multicollinearity, drop highly correlated variables or combine them using dimensionality reduction techniques. For time-series models, confirm stationarity with the Augmented Dickey-Fuller test  and evaluate autocorrelation with the Durbin-Watson test, incorporating lagged variables or ARIMA models if required.
### Visualization
Utilize trend lines and scatter plots to illustrate the relationships between significant variables.  Interaction plots for H1 will show how the relationship between STI incidence and population density is moderated by healthcare access, while bar charts and boxplots will compare STI rates across regions with different socioeconomic status and healthcare access levels in H2. Time-series line plots will show national trends over time in H3, overlaid with healthcare access levels to demonstrate their correlation.
## Intended Results and Implications
The study aims to confirm that high population density is still a major factor in STI transmission, even when it is resolved by higher access to healthcare, that STI incidence rates are higher in areas with lower socioeconomic status and less access to healthcare, and that declining STI trends are correlated with national improvements in healthcare access over time. These results would suggest that targeted public health interventions are necessary in areas that are densely populated and socioeconomically disadvantaged, with a focus on access to comprehensive and affordable healthcare prices. The findings may also encourage policymakers to give long-term investments in healthcare infrastructure and education top priority in order to gradually reduce STI rates, advance health equity, and lessen the burden of disease on a national level. 
