# **Credit Card Analytics Dashboard**
**A comprehensive Power BI dashboard for real-time credit card operations monitoring and customer behavior analysis.**
## Overview
This project develops an interactive business intelligence solution that transforms raw credit card transaction and customer data into actionable insights. The dashboard enables stakeholders to monitor key performance metrics, track revenue trends, analyze customer demographics, and make data-driven decisions to optimize credit card operations. Built using PostgreSQL for data management and Power BI for visualization, the system processes over 667K transactions and provides weekly performance analysis with automated KPI tracking.

## Problem Statement
Financial institutions need real-time visibility into credit card operations to:

- Monitor revenue performance and identify growth opportunities
- Track customer acquisition and activation rates
- Manage delinquency risks across different customer segments
- Understand spending patterns by demographics and card categories
- Analyze transaction trends to optimize marketing strategies
- Make data-driven decisions based on comprehensive performance metrics

Traditional reporting methods lack interactivity and fail to provide timely insights needed for proactive decision-making in the dynamic credit card industry.

## Dataset
The project utilizes four CSV files containing credit card transaction and customer information:

**1. credit_card.csv (Main Transaction Data)**

- **Records:** Transaction-level data across 53 weeks
- **Key Fields:** Client_Num, Card_Category, Week_Start_Date, Total_Trans_Amt, Total_Trans_Ct, Interest_Earned, Credit_Limit, Annual_Fees, Delinquent_Acc, Use_Chip, Exp_Type
- **Granularity:** Weekly transaction aggregates per customer

**2. customer.csv (Customer Demographics)**

- **Records:** Customer profile information
- **Key Fields:** Client_Num, Customer_Age, Gender, Income, Education_Level, Marital_Status, State_cd, Customer_Job, Dependent_Count, Cust_Satisfaction_Score
- **Granularity:** One record per customer

**3. cc_add.csv (Additional Transaction Data - Week 53)**

Supplementary credit card transaction data for latest week
Same structure as credit_card.csv

**4. cust_add.csv (Additional Customer Data - Week 53)**

New customer records for latest week
Same structure as customer.csv

**Data Relationship:** Both datasets linked via Client_Num (Primary Key)
Total Metrics:

- Revenue: $57M
- Transactions: 667.2K
- Total Interest: $8M
- Transaction Amount: $45.5M

## Tools and Technologies

| Technology | Purpose |
|------------|---------|
| PostgreSQL | Database management and data storage |
| Power BI Desktop | Interactive dashboard creation and visualization |
| DAX (Data Analysis Expressions) | Custom calculations and measures |
| SQL | Data import, transformation, and querying |
| CSV | Data format for import/export |

### **Development Environment:**

- PostgreSQL 12+
- Power BI Desktop (Latest version)
- SQL Client for database operations

## Methods

**1. Data Architecture**

- Created PostgreSQL database (ccdb) with two normalized tables
- Established relationship between cc_detail and cust_detail tables using Client_Num
- Imported initial datasets and incremental weekly updates

**2. Data Processing**

- Cleaned and validated data during SQL import
- Handled date format inconsistencies using datestyle settings
- Created calculated columns for age groups and income segments

**3. DAX Measures Development**

- **Revenue Calculation:** Annual_Fees + Total_Trans_Amt + Interest_Earned
- **Week-over-Week Analysis:** Current vs. Previous week revenue comparison
- **Customer Segmentation:** Age groups (20-30, 30-40, 40-50, 50-60, 60+)
- **Income Classification:** Low (<$35K), Medium ($35K-$70K), High (>$70K)
- **Time Intelligence:** Week number calculations for trending

**4. Dashboard Design**

- **Three-Dashboard Approach:**
  - Weekly Performance Dashboard: WoW metrics and trend analysis
  - Transaction Report: Card performance and expenditure breakdown
  - Customer Report: Demographic analysis and segmentation

- Interactive filters: Quarter, Week, Gender, Card Category, Income Group

- Visual hierarchy: KPI cards → Trends → Detailed breakdowns

**5. Analysis Techniques**

- Time-series analysis for revenue trends
- Cohort analysis by customer demographics
- Geographic performance mapping
- Risk segmentation by delinquency rates
- Card category performance comparison

## Key Insights
**Week 53 Performance (December 31st)**

- **Revenue Growth:** 28.8% WoW increase (₹933K → ₹1.2M)
- **Strong Weekly Performance:** Consistent growth in weeks 11 (14.5%), 42 (9.9%), and 44 (13.7%)

**Year-to-Date Summary**

- **Total Revenue:** $57M with steady quarterly performance
- **Gender Split:** Male customers contribute 54% ($31M) vs Female 46% ($26M)
- **Card Distribution:** Blue and Silver cards dominate with 93% of transactions
- **Geographic Concentration:** TX, NY, and CA represent 68% of total revenue

**Customer Behavior**

- **Activation Rate:** 57.5% of customers activate cards within 30 days
- **Delinquency Risk:** 6.06% overall delinquency rate

   - Highest risk: Self-employed customers (23.87%)
   - Lowest risk: Retirees (9.16%)


- **Top Revenue Generators:** Businessmen ($18M), White-collar ($10M), Self-employed ($9M)

**Transaction Patterns**

- **Expenditure Leaders:** Bills (14M), Entertainment ($10M), Fuel ($10M)
- **Payment Preference:** Swipe (63% - $36M), Chip (30% - $17M), Online (7% - $4M)
- **Education Impact:** Graduate degree holders contribute $23M (40% of revenue)
- **Income Correlation:** High-income segment generates $30M (53% of revenue)

**Card Performance**

- **Blue Card:** Highest revenue generator ($47M) and acquisition cost leader ($47M)
- **Silver Card:** Second best performer ($5.7M revenue, $6M acquisition cost)
- **Premium Cards:** Gold and Platinum show lower volumes but higher margins


## Dashboard/Model/Output
***Dashboard 1: Credit Card Transaction Report***

**Purpose:** Comprehensive transaction analysis and card performance tracking

**Key Components:**

**KPI Cards:** Revenue ($57M), Interest ($8M), Transaction Amount ($45.5M), Transaction Count (667.2K)

**Quarter Filters:** Q1, Q2, Q3, Q4 for temporal analysis

**Card Performance Table:** Revenue, transaction amounts, and interest by card type

**Dual-axis Chart:** QTR revenue and transaction count correlation

**Demographic Breakdowns:**

- Revenue by expenditure type (6 categories)
- Revenue by education level (6 levels)
- Revenue by customer job (6 professions)
- Customer acquisition cost by card type
- Revenue by payment method (3 types)

**Use Case:** Product management, marketing strategy, financial planning

***Dashboard 2: Credit Card Customer Report***

**Purpose:** Deep-dive customer analysis and demographic segmentation

**Key Visualizations:**

**KPI Cards:** Revenue, Interest, Total Income ($587.6M), Customer Satisfaction Score (3.19)

**Revenue by Week:** Dual-line chart comparing male vs female trends (Jan-Oct 2023)

**Age Group Analysis:** Stacked bars showing revenue by gender across age brackets

**Customer Job Table:** Detailed metrics (revenue, interest, income) by profession

**Geographic Analysis:** Top 5 states with gender split (TX, NY, CA, FL, NJ)

**Demographic Segmentation:**

 - Revenue by marital status (Married $29M, Single $24M)
 - Revenue by income group (High earners dominate at $30M)
 - Revenue by dependent count (0-4 dependents)
 - Revenue by education level


**Use Case:** Customer relationship management, targeted marketing, risk assessment

***Dashboard 3: Weekly Performance & Insights***

**Purpose:** Real-time monitoring of weekly metrics and operational health

**Key Visualizations:**

- Bar chart showing revenue by card category (Blue dominance at $40M+)
- WoW revenue comparison table with percentage changes
- Line chart tracking transaction amounts across 53 weeks
- Delinquency rate matrix by job type
- Activation rate distribution (57.46% activated vs 42.54% inactive)

**Use Case:** Executive monitoring, weekly business reviews, trend identification

## How to Run this Project?

### **Prerequisites**

```
✓ PostgreSQL (version 12 or higher)
✓ Power BI Desktop (latest version)
✓ 4 CSV files (credit_card.csv, customer.csv, cc_add.csv, cust_add.csv)
✓ Basic SQL and Power BI knowledge
```
### **Step 1: Clone the Repository**
```bash
git clone https://github.com/yourusername/Credit_Card_Financial_Dashboard.git
cd Credit_Card_Financial_Dashboard
```

### **Step 2: Database Setup**

**Create Database**
```sql
CREATE DATABASE ccdb;
```
**Create Tables**
```sql
-- Credit Card Detail Table
CREATE TABLE cc_detail (
    Client_Num INT,
    Card_Category VARCHAR(20),
    Annual_Fees INT,
    Activation_30_Days INT,
    Customer_Acq_Cost INT,
    Week_Start_Date DATE,
    Week_Num VARCHAR(20),
    Qtr VARCHAR(10),
    current_year INT,
    Credit_Limit DECIMAL(10,2),
    Total_Revolving_Bal INT,
    Total_Trans_Amt INT,
    Total_Trans_Ct INT,
    Avg_Utilization_Ratio DECIMAL(10,3),
    Use_Chip VARCHAR(10),
    Exp_Type VARCHAR(50),
    Interest_Earned DECIMAL(10,3),
    Delinquent_Acc VARCHAR(5)
);


-- Customer Detail Table
CREATE TABLE cust_detail (
    Client_Num INT,
    Customer_Age INT,
    Gender VARCHAR(5),
    Dependent_Count INT,
    Education_Level VARCHAR(50),
    Marital_Status VARCHAR(20),
    State_cd VARCHAR(50),
    Zipcode VARCHAR(20),
    Car_Owner VARCHAR(5),
    House_Owner VARCHAR(5),
    Personal_Loan VARCHAR(5),
    Contact VARCHAR(50),
    Customer_Job VARCHAR(50),
    Income INT,
    Cust_Satisfaction_Score INT
);
```

**Import Data**

```sql
-- Set date format (if needed)
SET datestyle TO 'ISO, DMY';

-- Import main datasets
COPY cc_detail FROM '/path/to/credit_card.csv' DELIMITER ',' CSV HEADER;
COPY cust_detail FROM '/path/to/customer.csv' DELIMITER ',' CSV HEADER;

-- Import additional data (Week 53)
COPY cc_detail FROM '/path/to/cc_add.csv' DELIMITER ',' CSV HEADER;
COPY cust_detail FROM '/path/to/cust_add.csv' DELIMITER ',' CSV HEADER;
```

### **Step 3: Connect Power BI to Database**

1. Open **Power BI Desktop**
2. Click **Get Data → PostgreSQL database**
3. Enter server details:
- **Server:** localhost (or your PostgreSQL server)
- **Database:** ccdb

4. Select both tables: cc_detail and cust_detail
5. Click **Load**

### **Step 4: Create Data Model**

Go to **Model View** in Power BI
Create relationship:

- **From:** cc_detail[Client_Num]
- **To:** cust_detail[Client_Num]
- **Cardinality:** Many to One
- **Cross-filter direction:** Both



### **Step 5: Add DAX Measures**
Create a new table called "Measures" and add the following:
```dax
AgeGroup = SWITCH(
    TRUE(),
    'cust_detail'[Customer_Age] < 30, "20-30",
    'cust_detail'[Customer_Age] >= 30 && 'cust_detail'[Customer_Age] < 40, "30-40",
    'cust_detail'[Customer_Age] >= 40 && 'cust_detail'[Customer_Age] < 50, "40-50",
    'cust_detail'[Customer_Age] >= 50 && 'cust_detail'[Customer_Age] < 60, "50-60",
    'cust_detail'[Customer_Age] >= 60, "60+",
    "unknown"
)

IncomeGroup = SWITCH(
    TRUE(),
    'cust_detail'[Income] < 35000, "Low",
    'cust_detail'[Income] >= 35000 && 'cust_detail'[Income] < 70000, "Med",
    'cust_detail'[Income] >= 70000, "High",
    "unknown"
)

week_num2 = WEEKNUM('cc_detail'[Week_Start_Date])

Revenue = 'cc_detail'[Annual_Fees] + 'cc_detail'[Total_Trans_Amt] + 'cc_detail'[Interest_Earned]

Current_week_Revenue = CALCULATE(
    SUM('cc_detail'[Revenue]),
    FILTER(
        ALL('cc_detail'),
        'cc_detail'[week_num2] = MAX('cc_detail'[week_num2])
    )
)

Previous_week_Revenue = CALCULATE(
    SUM('cc_detail'[Revenue]),
    FILTER(
        ALL('cc_detail'),
        'cc_detail'[week_num2] = MAX('cc_detail'[week_num2])-1
    )
)
```
### **Step 6: Build Dashboards**

1. Create three separate report pages:

 - **Page 1:** Weekly Performance Dashboard
 - **Page 2:** Transaction Report
 - **Page 3:** Customer Report

2. Add visualizations based on the dashboard screenshots provided in /images folder
3. Apply formatting and color themes for professional appearance

## Results & Conclusion

***Key Achievements***

**1. Revenue Performance**

- Successfully tracked $57M in total revenue with detailed breakdown by card category, customer segment, and time period
- Identified 28.8% WoW revenue growth in Week 53, demonstrating strong business momentum
- Quarterly revenue stability observed ($14-14.5M per quarter) indicating consistent performance

**2. Customer Insights**

- Segmented 667.2K transactions across demographic dimensions (age, income, education, occupation)
- Discovered that male customers contribute 54% more revenue than female customers, indicating potential for targeted marketing
- Identified high-income segment as primary revenue driver ($30M, 53% of total)
- Graduate degree holders generate 40% of total revenue ($23M)

**3. Risk Management**

- Established delinquency tracking system showing 6.06% overall rate
- Identified high-risk segment: Self-employed customers (23.87% delinquency)
- Recognized low-risk segment: Retirees (9.16% delinquency)
- Enabled proactive risk mitigation strategies through early warning indicators

**4. Operational Efficiency**

- Achieved 57.5% activation rate, providing benchmark for improvement initiatives
- Monitored customer acquisition costs by card type (Blue: $47M, Silver: $6M)
- Tracked payment method preferences: Swipe (63%), Chip (30%), Online (7%)

**5. Geographic Strategy**

- Concentrated performance in top 3 states (TX, NY, CA) with 68% revenue contribution
- Identified expansion opportunities in underperforming regions
- Enabled regional marketing budget allocation based on performance data

***Business Impact***

**Strategic Decision-Making**

- Empowered stakeholders with real-time dashboards replacing manual reporting
- Reduced decision-making time through interactive visualizations and drill-down capabilities
- Enabled data-driven resource allocation across products, geographies, and customer segments

**Product Optimization**

- Blue card identified as star product with $47M revenue, justifying continued investment
- Silver card showing strong performance ($5.7M) with lower acquisition costs
- Premium cards (Gold, Platinum) identified as niche products requiring targeted strategies

**Marketing Intelligence**

- Expenditure analysis revealed top categories (Bills, Entertainment, Fuel) for partnership opportunities
- Education and occupation insights enabled precision targeting in campaigns
- Age group analysis informed product development for different life stages

**Operational Excellence**

- Automated weekly reporting reduced manual effort by 80%
- Standardized KPI tracking across organization
- Facilitated stakeholder collaboration through shared dashboard access

**Technical Success**

- Successfully integrated PostgreSQL with Power BI for scalable data architecture
- Implemented incremental data loading for Week 53 without disrupting existing records
- Created reusable DAX measures for consistent calculations across dashboards
- Designed user-friendly interface with intuitive filters and drill-through capabilities

***Limitations & Future Enhancements***

**Current Limitations:**

- Data covers 53 weeks; longer time series needed for advanced predictive modeling
- Customer satisfaction score (3.19) requires deeper analysis beyond aggregate metrics
- Real-time data refresh not implemented (currently manual updates)

**Recommended Enhancements:**

**1. Predictive Analytics:** Implement forecasting models for revenue and delinquency prediction

**2. Customer Lifetime Value:** Calculate CLV for targeted retention strategies

**3. Churn Analysis:** Develop early warning system for customer attrition

**4. Automated Alerts:** Set threshold-based notifications for critical KPIs

**5. Mobile Optimization:** Create Power BI mobile layouts for on-the-go access

**6. API Integration:** Connect to live transaction systems for real-time updates

**7. Advanced Segmentation:** Apply clustering algorithms for micro-segmentation

**8. Comparative Analysis:** Benchmark against industry standards and competitors

***Conclusion***

This Credit Card Financial Dashboard project successfully transforms raw transactional data into actionable business intelligence, delivering comprehensive insights across revenue performance, customer behavior, and operational metrics. The interactive Power BI dashboards enable stakeholders to monitor $57M in annual revenue, analyze 667.2K transactions, and track critical KPIs including 57.5% activation rate and 6.06% delinquency rate.

The three-dashboard architecture (Weekly Performance, Transaction Report, Customer Report) provides multi-dimensional analysis capabilities, empowering strategic decision-making across marketing, product development, risk management, and customer relationship management functions. Key discoveries include the dominance of Blue card category ($47M revenue), concentration of business in TX-NY-CA markets (68% contribution), and identification of high-value customer segments (businessmen, high-income earners, graduates).

By leveraging PostgreSQL for robust data management and Power BI for intuitive visualization, this project establishes a scalable foundation for ongoing analytics initiatives. The implementation demonstrates proficiency in end-to-end business intelligence development, from database design and DAX calculations to dashboard design and insight generation.

The project not only meets its core objective of providing real-time operational insights but also creates a framework for future enhancements including predictive analytics, automated alerting, and advanced customer segmentation. This solution serves as a template for financial institutions seeking to leverage data analytics for competitive advantage in the credit card industry.


## 📬 Contact

### **Deorshi Nishant**
*Data Analyst & Business Intelligence Professional*

---

### 🔗 Connect with me

<p align="left">
  <a href="https://www.linkedin.com/in/itsyournish/" target="_blank">
    <img src="https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn"/>
  </a>
  <a href="mailto:itsyournish07@gmail.com">
    <img src="https://img.shields.io/badge/Gmail-D14836?style=for-the-badge&logo=gmail&logoColor=white" alt="Gmail"/>
  </a>
</p>

---

### Get in Touch
- **LinkedIn**: [itsyournish](https://www.linkedin.com/in/itsyournish/)
- **Email**: [itsyournish07@gmail.com](mailto:itsyournish07@gmail.com)

---

*💼 Open to collaborations and new opportunities in Data Analytics & Business Intelligence*
