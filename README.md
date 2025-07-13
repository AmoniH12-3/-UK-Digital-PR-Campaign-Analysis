# UK Digital PR Campaign Analysis
## Introduction
- This project analyzes UK digital PR campaigns focused on measuring conversions, referral traffic, media mentions, and backlink efficiency across regions.
-🔝 The campaign types with the most conversions
-📈 The average referral traffic for each campaign by topic
-🔝 Which region had the best backlinks-to-conversion rate
-📈 Ranking the campaigns by the most media mentions
## Background
### Tools I used
- **BigQuery** — used for writing, testing, and managing SQL queries
- **Git + GitHub** — version control and project sharing
-  ## The Analysis
-  Each query was crafted to evaluate how effectively digital PR campaigns converted traffic into conversions, earned backlinks, and gained media visibility.
## 🗂️ Data Schema
- The project uses four key tables:
- `UK Campaigns by Conversions`: Main job data (location, salary, remote status)
- `By Referral Traffic`: Unique list of skills
- `By Media Mentions`: Many-to-many join table between jobs and skills
- `Region with the best backlink to conversion rate`: Company details

## 🔝 The campaign types with the most conversions

| Campaign Name                        | Conversions      | Referral Traffic|Conversion Rate|
|--------------------------------------|------------------|--------------|-------------------|
|AI Pet Translator                     |1200              |  5200        |      0.231        |
|Moonbag Survival Kit                  |960               |  4400        |      0.218        |
|Rent Prices Heat Map                  |760               |  3500        |      0.217        |
|Green Commuter Cities                 |540               |  2900        |      0.186        |
|CBD Myths Busted                      |400               |  1800        |      0.222        |
|Gen Z Workplace Trends                |210               |  1200        |      0.175        |

``` sql
SELECT campaign_name, Conversions
FROM `sylvan-shuttle-456019-r2.PR_dataset.PR Metrics Data`
ORDER BY Conversions DESC;
```
### 💡 Insights:

- Campaigns with educational or utility tools performed best in terms of conversions.

## 📈 The average referral traffic for each campaign by topic

|campaign_name|topic|avg_referral_traffic|
|-----------|--------------|-------------|
|AI Pet Translator|Tech|5200|
|Moonbag Survival Kit|Space|4400|
|Rent Prices Heat Map|Real Estate|3500|
|Green Commuter Cities|Sustainability|2900|
|CBD Myths Busted|Cannabis|1800|
|Gen Z Workplace Trends|Career|1200|

#### SQL Code: 
``` sql
SELECT 
  campaign_name,
  topic,
  AVG(referral_traffic) AS avg_referral_traffic
FROM `sylvan-shuttle-456019-r2.PR_dataset.PR Metrics Data`
GROUP BY campaign_name, topic
ORDER BY avg_referral_traffic DESC;
```

### 💡 Insights:

- Tech campaigns earn the most referral traffic out of any other type of campaign.

### 📈 Ranking the campaigns by the most media mentions

|campaign_name|media mentions|conversions|referral traffic
|----------------|----------------|-------------------------|-------------|
|AI Pet Translator|154|	1200|	5200|0.2307692308|
|Moonbag Survival Kit|127|	960	|4400|	0.2181818182|
|Rent Prices Heat Map|90|760	|3500	|0.2171428571|
|Green Commuter Cities|78|	540|	2900|	0.1862068966|
|CBD Myths Busted|	61|400	|1800	|0.2222222222|
|Gen Z Workplace Trends|	52	|210	|1200	|0.175|

> 💡 **Insight:** A higher number of meda mentions correlates to higher conversions but not the conversion rate for all campaigns.
``` sql
 SELECT 
  campaign_name,
  media_mentions,
  conversions,
  referral_traffic,
  SAFE_DIVIDE(conversions, referral_traffic) AS conversion_rate
FROM `sylvan-shuttle-456019-r2.PR_dataset.PR Metrics Data`
ORDER BY conversion_rate DESC;
```
### 🔝 Which region had the best backlinks-to-conversion rate
| Region     | Campaign Name             | Conversions | Backlinks | Backlink Conversion Rate (%) |
|------------|---------------------------|-------------|-----------|-------------------------------|
| London     | Green Commuter Cities     | 540         | 43        | 12.56%                        |
| London     | Rent Prices Heat Map      | 760         | 62        | 12.26%                        |
| UK-wide    | AI Pet Translator         | 1200        | 98        | 12.24%                        |
| UK-wide    | Moonbag Survival Kit      | 960         | 87        | 11.03%                        |
| Manchester | CBD Myths Busted          | 400         | 39        | 10.26%                        |
| Birmingham | Gen Z Workplace Trends    | 210         | 21        | 10.00%                        |

> 💡 **Insight:** Campaigns based in **London** performed the most efficiently in turning backlinks into conversions. This suggests that regionally relevant content may significantly improve campaign ROI.

## SQL Code
``` sql
SELECT
region, 
  campaign_name,
  conversions,
  backlinks,
  SAFE_DIVIDE(conversions, backlinks) AS backlink_conversion_rate
FROM `sylvan-shuttle-456019-r2.PR_dataset.PR Metrics Data`
ORDER BY backlink_conversion_rate;
```

## What I learned
- SQL can effectively uncover performance trends in marketing datasets like referral traffic, conversions, and backlink impact.
- Conversion rate analysis requires thoughtful use of SAFE_DIVIDE() to avoid errors in division by zero.
- Segmenting results by region and topic provided actionable insights into how audience location and campaign theme influence PR success.
- Metrics like media mentions don't always correlate with conversions — highlighting the importance of measuring multiple success KPIs.
- Cleaning inconsistent entries in columns (like campaign names or regions) before aggregation helped improve data quality and query results.
### Conclusions
- This project shows how data analysts can use SQL to analyze PR campaigns across multiple marketing KPIs. By ranking campaigns by conversion efficiency, media reach, and backlinks-to-conversion ratio, I was able to provide a clearer picture of which campaigns  were most effective. These insights could support future campaign ideations, budget allocation, and optimization strategies for future UK-based digital PR efforts.


