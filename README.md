Donor Analysis Dashboard – Power BI Project
This project presents a comprehensive donor analysis using Power BI. The dataset contains 10,000 donation records, and the goal is to derive key insights to help the charity organization target the right donors and optimize fundraising strategies.

Page 1 – Overview Dashboard
Key Features:
EDA (Exploratory Data Analysis) performed to understand donation trends.

Visual Insights:

- Sum of Donation Amount by Campaign

- Count of Payment Methods

- Monthly Donation Trends

KPIs:

- Donor Count

- Average Donation

- Total Donations

Slicers: Year and Quarter filters for dynamic data exploration.

Page 2 – Problem Statement: "Whom Should We Target for Fundraising?"
Objective:
To identify the ideal donor profile for effective fundraising campaigns.

Insights:
-Sum of Donation Amount by Sector
→ Identifies sectors with the highest donations.

-Sum of Donation Amount by Country
→ USA contributes the highest donation amount.

-Sum of Donation Amount by Referral Channel
→ Highest donations are from Word of Mouth referrals.

-Sum of Donation Amount by Age Group
→ Most generous donors are aged 50–65.

-Target Audience:
  -Country: USA

  -Age Group: 50–65

  -Referral Strategy: Personal outreach (Word of Mouth)

Page 3 – RFM Analysis (Recency, Frequency, Monetary)
What is RFM?
Recency: How recently a donor has contributed.

Frequency: How often they donate.

Monetary: Total amount donated.

Step 1: Calculate R, F, M
DAX Example – Recency:

DAX Query

Recency = 
DATEDIFF(
    CALCULATE(
        MAX(animal_charity_donation_records[donation_date]), 
        ALLEXCEPT(animal_charity_donation_records, animal_charity_donation_records[donor_id])
    ),
    TODAY(),
    DAY
)
 
– Recency Score:

Recency_Score = 
SWITCH(
    TRUE(),
    [Recency] <= 30, 5,
    [Recency] <= 90, 4,
    [Recency] <= 180, 3,
    [Recency] <= 365, 2,
    1
)
(Repeat similar scoring logic for Frequency and Monetary)

Step 2: Calculate Combined RFM Score
-DAX Query
RFM_Score = 
[Recency_Score] * 100 + [Frequency_Score] * 10 + [Monetary_Score]
Step 3: Segment Donors Based on RFM Score
RFM Score Range	Segment Name	Strategy
444 – 555	High Value Donors	Reward, prioritize
333 – 443	Loyal or Potential	Engage, build relationships
222 – 332	Needs Attention	Re-engage with targeted asks
Below 222	At Risk / Lapsed	Win-back campaigns

- Conclusion
With these dashboards and insights:

We can focus fundraising on high-potential donors.

Segment-wise strategies help tailor communication.

RFM analysis provides a data-driven roadmap for donor engagement.
