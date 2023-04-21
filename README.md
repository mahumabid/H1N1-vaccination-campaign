# Lessons Learned: H1N1 2009 Vaccination Campaign
Author: MAHUM ABID

# Overview & Business Problem

Our task is to build a model that can use the patient health and demographics data collected following the 2009 H1N1 virus outbreak to predict which patients are likely to get the vaccine. Our focus will be the precision score. We wanted to use precision since it helps measure the true positives. In this case, maximizing the true positives and minimizing the false positives is paramount.

For this project, our stakeholder is NYC Health. In the spring of 2009, a novel influenza A (H1N1) virus emerged. This new H1N1 virus contained a unique combination of influenza genes not previously identified in animals or people. Few young people had any existing immunity (as detected by antibody response) to the H1N1 virus, but nearly one-third of people over 60 years old had antibodies against this virus, likely from exposure to an older H1N1 virus earlier in their lives. We want to analyze this data in order to give future insights to predict vaccine rates in case something similar to another COVID outbreak happens.

# The Bottom Line
From the data, these four attributes contributed most to being able to predict whether or not the respondent received the vaccine:

1. Opinion of H1N1 Vaccine Effectiveness

2. Doctor Recommendation of H1N1 Vaccine

3. Opinion of H1N1 Risk Without Vaccine

4. Ethnicity
# Data Understanding
To build the model, we used data from the National 2009 H1N1 Flu Survey, a government-sponsored telephone survey designed to monitor vaccination rates for both flu and H1N1 during the 2009-10 season. The data was originally provided from the National Center for Health Statistics (https://www.cdc.gov/nchs/index.htm). Specifically, we used the data as curated by DrivenData for its Flu Shot Learning competition.

Features column descriptions from DrivenData:

-respondent_id: A unique and random identifier.

-h1n1_concern: Level of concern of h1n1 virus.

-h1n1_knowledge: Level of H1N1 virus knowledge. behavioral_antiviral_meds: Behavioral Indicator- Taking anti-viral medication. behavioral_avoidance: Behavioral Indicator- Avoid close contact with others with flulike symptoms. behavioral_face_mask: Behavioral Indicator- Bought a face mask. behavioral_wash_hands: Behavioral Indicator- Washing hands. behavioral_large_gatherings: Behavioral Indicator- Reduced time at large gatherings. behavioral_outside_home: Behavioral Indicator- Reduced contact outside the home. behavioral_touch_face: Behavioral Indicator- Avoid touching eyes, nose, or mouth. doctor_recc_h1n1: H1N1 flu vaccine was recommended by doctor. (binary) doctor_recc_seasonal: Seasonal flu vaccine was recommended by doctor. (binary) chronic_med_condition: Has any of the following chronic medical conditions: asthma or an other lung condition, diabetes, a heart condition, a kidney condition, sickle cell anemia or other anemia, a neurological or neuromuscular condition, a liver condition, or a weakened immune system caused by a chronic illness or by medicines taken for a chronic illness. (binary) child_under_6_months: Close contact with child under 6 months of age. health_worker: Is a healthcare worker. (binary) health_insurance: Has health insurance. (binary) opinion_h1n1_vacc_effective: Opinion- Effectiveness of H1N1 vaccine. opinion_h1n1_risk: Opinion- Risk of getting sick with H1N1 flu without vaccine. opinion_h1n1_sick_from_vacc: Opinion- Worry about getting sick from the H1N1 vaccine. opinion_seas_vacc_effective: Opinion- Effectiveness of seasonal vaccine. opinion_seas_risk: Opinion- Risk of getting sick with the seasonal flu without vaccine. opinion_seas_sick_from_vacc: Opinion- Worry about getting sick from the seasonal vaccine. age_group: Age group of respondent. education: Adult self-reported education level. race: Race of respondent. sex: Sex of respondent. income_poverty: Poverty status of household. marital_status: Marital status of respondent. employment_status: Employment status of respondent. hhs_geo_region: Respondent's residence using a 10-region geographic classification defined by the U.S. Dept. of Health and Human Services. Values are represented as short random character strings. census_msa: Respondent's residence within metropolitan statistical areas (MSA) as defined by the U.S. Census. household_adults: Number of adults in the houshold (other than respondent). household_children: Number of children in the houshold. employment_industry: Type of industry respondent is employed in. (values are represented as short random character strings) employment_occupation: Type of occupation of respondent. Values are represented as short random character strings.

# Data Cleaning

We started by merging the target .csv file with our training data in order to match respondent h1n1 and seasonal flu vaccine responses.

We then focused on employment_industry, employment_occupation, and hhs_geo_region. These attributes were converted to randomized strings, which did not help give us any insights for our analysis. As such we dropped them.

Then, we wanted to focus on health_insurance as we believed that this attribute would have had an impact on our model. We noted that there were a number of null values for this category and as such we also dropped the null values.

The remaining categories had a few nulls that could not be iterated, and were dropped as well. This resulted in a dataset of 11,794 data points that we used for our model creation.
