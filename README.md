# UK Digital PR Campaign-Analysis
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

### 

|campaign_name	media mentions|	conversions	referral_traffic|conversion_rate|
|----------------|----------------|-------------------------|
| Neo4j          | 185,000.00     |
| Elasticsearch  | 185,000.00     |
| Cassandra      | 175,000.00     |
| dplyr          | 167,500.00     |
| Unix           | 162,500.00     |
| Perl           | 157,000.00     |
| Twilio         | 150,000.00     |
| Spring         | 147,500.00     |
| C              | 146,500.00     |
| Angular        | 138,516.00     |
| GCP            | 135,293.75     |
| Kafka          | 135,000.00     |
| Pandas         | 133,169.36     |
| Scikit-learn   | 130,000.00     |
| Linux          | 127,500.00     |
| Shell          | 126,250.00     |
| Express        | 126,004.73     |
| Java           | 125,146.88     |
| NumPy          | 125,061.83     |
| C++            | 124,043.75     |
| Git            | 123,750.00     |
| Azure          | 122,692.31     |
| Plotly         | 122,500.00     |
| Airflow        | 122,500.00     |
| Qlik           | 120,762.50     |
| Snowflake      | 119,576.92     |
| GDPR           | 117,750.00     |
| SQL Server     | 114,327.13     |
| C#             | 111,570.83     |
| Looker         | 111,020.44     |
| Python         | 110,395.54     |
| PySpark        | 109,166.67     |
| Jupyter        | 107,561.83     |
| BigQuery       | 107,437.50     |
| Jira           | 107,001.45     |
| AWS            | 106,887.50     |
| Flow           | 106,687.74     |
| Spark          | 105,242.00     |
| SQL            | 104,757.08     |
| Databricks     | 103,500.00     |
| SAP            | 102,760.00     |
| GitHub         | 102,625.00     |
| PowerShell     | 101,250.00     |
| DB2            | 100,833.33     |
| NoSQL          | 100,766.21     |
| Confluence     | 100,586.00     |
| Tableau        | 100,029.62     |
| SSIS           | 100,026.00     |
| MongoDB        | 100,000.00     |
| MySQL          | 99,500.00      |

> 💡 **Insight:** Niche and backend-heavy skills like Neo4j, Cassandra, and GCP command the highest salaries, while foundational tools like SQL and Tableau remain essential but earn slightly lower on average.
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
### 💡 Insights:

- **SQL and Python** appear across nearly every high-paying listing.
- **Cloud platforms** (Azure, AWS, Snowflake) are major salary boosters.
- Tools like **Pandas, Jupyter, Tableau**, and **Power BI** are expected in modern analyst workflows.
- **R and Excel** still matter and are well-compensated when combined with modern tools.

### 🎯 Optimal Skills to Learn (Based on Demand and Salary):

| Skill        | Demand Count | Avg Salary ($) |
|--------------|---------------|----------------|
| SQL          | 398           | 97,237.16      |
| Excel        | 256           | 87,288.21      |
| Python       | 236           | 101,397.22     |
| Tableau      | 230           | 99,287.65      |
| R            | 148           | 100,498.77     |
| Power BI     | 110           | 97,431.30      |
| SAS          | 63            | 98,902.37      |
| PowerPoint   | 58            | 88,701.09      |
| Looker       | 49            | 103,795.30     |
| Word         | 48            | 82,576.04      |
| Snowflake    | 37            | 112,947.97     |
| Oracle       | 37            | 104,533.70     |
| SQL Server   | 35            | 97,785.73      |
| Azure        | 34            | 111,225.10     |
| Google Sheets| 32            | 86,087.79      |
| AWS          | 32            | 108,317.30     |
| Flow         | 28            | 97,200.00      |
| Go           | 27            | 115,319.89     |
| VBA          | 24            | 88,783.29      |
| SPSS         | 24            | 92,169.68      |
| Hadoop       | 22            | 113,192.57     |
| JavaScript   | 20            | 97,587.00      |
| Jira         | 20            | 104,917.90     |
| SharePoint   | 18            | 81,633.58      |

> 💡 **Tip:** Prioritize high-demand, high-salary tools like **SQL, Python, Tableau, Snowflake, and Azure** to boost both employability and earnings potential.
> *Excel salaries vary widely depending on role, company, and combination with other tools.

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
- **SQL + Python + Tableau + Excel** = the golden combo for job opportunities and competitive salaries.
- Cloud and big data skills (e.g., **Snowflake, Azure, AWS**) are in high demand for senior roles.
- **Director** and **Principal Analyst** roles commonly pay above **$200K** and require both technical depth and business communication.
### Conclusions
- The data makes it clear: success in data analytics hinges on both foundational skills and alignment with industry demand.
- **SQL, Python, Excel, and Tableau** continue to be the essentials of a strong data analytics toolkit, as they are highly demanded across entry-level to director-level roles.
- Cloud tools like **Snowflake, AWS, Azure**, and **BigQuery** are becoming essential, especially for mid-to-senior-level analysts.
-  **SmartAsset, AT&T, and Pinterest** are offering salaries exceeding **$200K** for analysts with a production-ready skill set.
- **Specialized tools** like R, Pandas, Jupyter, and Databricks retain value when paired with strong business acumen or statistical modeling.

