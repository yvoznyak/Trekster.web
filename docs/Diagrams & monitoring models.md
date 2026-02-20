# Trekster

## Data Model

### ER Diagram

<p align="center">
	<img src="https://github.com/yvoznyak/Trekster.web/blob/main/docs/img/Db/er.jpg" alt="ER Diagram"/>
</p>

### Entity Description

<p align="center">
	<img src="https://github.com/yvoznyak/Trekster.web/blob/main/docs/img/Db/Db%20scheme.jpg" alt="Db scheme"/>
</p>

### Data Classification by Data Retention Policy

#### Confidentiality Level

##### Public Data:
- `Currencies.name`: Currency names do not contain sensitive information.
- `Categories.name`: Category names are general and non-confidential.

##### Internal Data:
- `Accounts.name`: Account names may be internal information for the organization/user.
- `Transactions.note`: Transaction notes may contain internal operational information.

##### Confidential Data:
- `Transactions.sum`: Transaction amounts are considered financial information requiring protection.
- `StartBalances.sum`: Initial account balances are sensitive confidential data.

#### Data Type

##### Personal Data: None.

##### Financial Data:
- `StartBalances.sum`
- `Transactions.sum`

##### Operational Data:
- `Transactions.date`
- `Transactions.idAccount`
- `Transactions.idCurrency`
- `Transactions.idCategory`
- `Transactions.note`

##### Reference Data:
- `Currencies`
- `Categories`
- `Accounts`

#### Retention Period

##### Short-term Storage (6-12 months):
- `Transactions.note`: Notes can be deleted after a short period if they are not used for analytics.

##### Medium-term Storage (3-5 years):
- `Transactions.date`
- `Transactions.sum`
- `StartBalances.sum`
- `Accounts.name`

##### Long-term Storage (5+ years):
- `Currencies.name`
- `Categories.name`
- `Transactions.idAccount`
- `Transactions.idCurrency`
- `Transactions.idCategory`

#### Legal Requirements
- **Transactions**: According to financial or tax requirements, transaction information must be stored for at least 5 years.
- **Initial Balances (StartBalances)**: May be stored according to legal requirements, for example, 5-7 years.
- **Categories and Currencies**: Data on categories and currencies are usually not regulated by law but can be stored long-term to support historical reporting.

#### Business Value

##### Critical Data:
- `StartBalances.sum`: Essential for ensuring the accuracy of financial statements.
- `Transactions.sum`: Necessary for analyzing income, expenses, and profitability.

##### Archival Data:
- `Currencies.name`: Archived to ensure the connectivity of historical data.
- `Categories.name`: Used for historical reporting.

#### Retention Policy Implementation Recommendations

##### Cleanup Automation:
- Use triggers or cron jobs to remove old notes or transaction data that have exceeded their retention period.

##### Archiving:
- Data from `Currencies` and `Categories` tables can be moved to an archive after their active use.

##### Confidential Data Encryption:
- Ensure encryption of columns containing financial data, such as `Transactions.sum` and `StartBalances.sum`.

##### Deletion Logging:
- Create a data deletion log to ensure transparency in accordance with regulatory requirements.

## Resiliency Model

### Cause-Influence Analysis

#### Problem — Incorrect Account Balance

Description of root cause categories:
- **People**: Errors due to insufficient knowledge or incorrect user actions (e.g., wrong data entry).
- **Process**: Incorrectly executed operations or calculation errors, which may be caused by issues with transactions or categories.
- **Equipment**: Problems with the server or other infrastructure components that may affect the database.
- **Materials**: Incorrectly entered information about currency or transactions, leading to an incorrect balance.

#### Root Cause Analysis

##### Analysis and Resolution Steps:

###### Causes:
- Transactions may be entered with errors.
- Incorrectly entered data can lead to calculation errors.

###### Root Causes:
- Incorrectly entered data regarding categories and exchange rates.
- Lack of proper validation checks in the system.

###### Solutions:
- Add a data validation mechanism for categories and exchange rates.
- Verify the correctness of calculations during transaction insertion or updates.
- Implement automated tests to verify data integrity.

## Analytics Model

Main functional metrics table for the personal finance management application:

| **Metric** | **Dimensions** | **Relationship with Functional Requirements** | **Comments** |
|-------------------------------------------|------------------------------------------------------------|----------------------------------------------------------|--------------------------------------------------------|
| **Number of Active Users** | Time (day, week, month), geography, device type | Tracking overall user activity | Determines engagement and retention |
| **Number of New Registrations** | Time, traffic source, campaign | Effectiveness of registration process and marketing efforts | Helps evaluate user base growth |
| **Number of System Logins** | Time, device type, geography | Convenience and reliability of authorization | Reflects regularity of app usage |
| **Number of Added Transactions** | Time, expense category, transaction type | Core functionality of financial data entry | Shows how actively users keep records |
| **Number of Generated/Viewed Reports** | Time, report type | Analytics and reporting functionality | Shows how users analyze their finances |
| **Average Session Duration** | Time, device type | User engagement level | Reflects interest in the application |
| **Number of Exported Files** | Time, data type, user | Export functionality and usability | Reflects user need for data portability |
| **Churn Rate** | Time | User retention and app quality | Helps identify retention issues |
| **Number of Added Accounts** | Time, account type | Account management functionality | Reflects usage of account management features |
| **Feature Usage Percentage** | Feature, time | Popularity and utility of various features | Helps in prioritizing feature development |

**Funnels:**

1. **Registration and First Use Funnel:**
   - Visit registration page
   - Fill out and submit registration form
   - Confirm email address
   - First login to the system
   - Add first transaction

   *This funnel helps track the conversion from a potential user to an active user who has started using the main functionality.*

2. **Analytics Usage and Data Export Funnel:**
   - Log in to the system
   - Navigate to transaction history
   - Generate a report
   - Export data to a file (.csv)

   *This funnel allows for evaluating how users interact with analysis and export features and whether it helps them in financial management.*

## Monitoring & Alerting Model

### Monitoring

Operational metrics collected for the application:

| **Metric** | **Dimensions** | **Relation to Infrastructure Resources** | **Collection Method** |
|-------------|------------|--------------------------------------------|----------------------------|
| **1. CPU Usage** | % usage, core count | Virtual Machines, App Service | Azure Monitor, Application Insights |
| **2. Memory Usage** | Used/Available memory | Virtual Machines, App Service | Azure Monitor, Application Insights |
| **3. Disk I/O** | Read/Write speed in MB/s | Data storage, databases | Azure Monitor |
| **4. Network Traffic** | Inbound/Outbound traffic in MB/s | Virtual Networks, Load Balancers | Azure Network Watcher |
| **5. App Response Time** | Avg, Max, Min time in ms | Web App, API | Application Insights |
| **6. Request Count** | Requests per second | Web App, API | Application Insights |
| **7. Error Rate** | % of failed requests | Web App, API | Application Insights |
| **8. DB Query Performance** | Query execution time in ms | SQL Database, Cosmos DB | Azure SQL Analytics |
| **9. Active User Count** | Unique users per period | Application | Application Insights |
| **10. App Exceptions** | Error types, frequency | Application | Application Insights |
| **11. Network Latency** | Latency in ms (client to server) | CDN, Network | Azure Monitor |
| **12. HTTP Status Codes** | Distribution of 2xx, 3xx, 4xx, 5xx | Web App, API | Application Insights |
| **13. Azure Service Health** | Events, incidents, updates | All Azure resources | Azure Service Health |

### Alerting

Metrics with thresholds, alert types, and mitigation plans:

| **Metric** | **Threshold** | **Alert Type** | **Severity** | **Mitigation Plan** |
|-------------|------------------------|--------------------|-----------------|-------------------------------|
| **1. CPU Usage** | > 80% for 10 minutes | Warning | High | - Scale resources<br>- Optimize code<br>- Check load |
| **2. Memory Usage** | > 75% constantly | Warning | High | - Optimize memory usage<br>- Add memory or scale up |
| **3. Error Rate** | > 5% of failed requests | Warning | High | - Check logs<br>- Fix critical errors |
| **4. App Response Time** | > 2000 ms avg | Warning | Medium | - Optimize code<br>- Check database |
| **5. DB Query Performance** | > 1000 ms per query | Warning | Medium | - Optimize queries<br>- Check indexes |
| **6. Disk I/O** | > 85% usage | Info | Medium | - Expand disk space<br>- Optimize storage |
| **7. HTTP 5xx Status Codes** | > 1% of total requests | Warning | High | - Check server errors<br>- Fix underlying issues |
| **8. Network Latency** | > 150 ms constantly | Info | Low | - Check network connections<br>- Optimize routing |

### Mitigation Plan for Critical Metrics:

1. **CPU and Memory Usage:**
   - **Diagnosis:** Use Azure Monitor to identify processes with high resource consumption.
   - **Actions:** Scale VMs or App Service plans. Optimize application code/algorithms. Implement caching and asynchronous processing.

2. **Error Rate and HTTP 5xx Status Codes:**
   - **Diagnosis:** Analyze logs using Application Insights. Identify common error causes.
   - **Actions:** Fix code bugs and perform regression testing.

3. **App Response Time and DB Query Performance:**
   - **Diagnosis:** Use profiling in Application Insights. Analyze DB query duration.
   - **Actions:** Optimize complex or slow SQL queries. Add/optimize indexes. Consider using a CDN or additional cache layers.

**Severity Definitions:**
- **High:** Requires immediate attention to prevent serious failures or data loss.
- **Medium:** Issue should be resolved soon to avoid service degradation.
- **Low:** Monitoring and planned resolution without immediate action.
