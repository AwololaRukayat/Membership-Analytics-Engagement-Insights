# Membership Analytics & Engagement Insights: A Retention and Revenue Analysis for RevUp Fitness

## Executive summary
This reports present an end-to-end analysis of RevUp’s Fitness membership data across its four branches in Nigeria for the period 2022-2025, using SQL(data cleaning and Analysis) and Excel for visualization.The goal was to understand what is actually driving member engagement, revenue and branch performance. 

At a recent strategy meeting, the founder asked a question that no one in the room could answer is RevUp Fitness genuinely growing. Total discount and members looked healthy on surface, but nobody could say which member type was staying engaged, whether the discounts being approved were earning them cost, or which branch had great engagement. Despite collecting membership data for years. RevUp Fitness had never connected it to answer these questions, leaving Sales, Operation and Finance to make pricing and engagement  decisions on instinct rather than evidence backed up by data.

The analysis revealed that RevUp retains 66% of its total members, generating ₦68.87M in total revenue performance broadly in line with the fitness industry's typical 60–70% retention range, but with clear room for improvement. Premium membership retains (41%) best in every branch, making it the most reliable lever for retention strategy, discounting accounts for 6% of revenue lost but concentrated inefficiently with Student discount being the biggest problem area responsible for the largest revenue loss (₦2.13M) and linked to the shortest average member tenure (515 days), indicating it is not building loyalty. Discount doesn’t drive growth as most members (42%) are non discounted members. Lagos accounts for 71% of total membership and 70% of total revenue, making it the network's dominant driver, while Port Harcourt recorded the lowest tenure (507) and Ibadan the least retention (61%) of all four branches, marking it as the one location requiring a dedicated operational review.

## Project overview 
The Global health club statistics picture is striking: the market is projected to nearly double by 2032. In Europe alone, 75.5 million people now hold fitness club memberships. The Nigeria Fitness Equipment Market reached USD 77.1 Million in 2025 and is estimated to attain USD 127.49 Million by 2034. This growth is not a post-pandemic bounce. Consumer attitudes have fundamentally shifted, fitness now sits alongside healthcare in the way people prioritize spending. Physical clubs are growing faster than at any point in the last decade, even as digital alternatives proliferate. The gym industry statistics 2026 confirm that the market is divided into two winning models: high-volume, low-price and premium, high-touch. The clubs caught in the middle — average pricing, average experience are under the most pressure. Two cohorts are driving the market in opposite directions. Gen Z and the 65+ cohort. Operators who design for both will outperform those who optimize for one.

This end-to-end project uses SQL (for data extraction, cleaning, and analysis) and Excel (for visualization) to evaluate whether pricing and discounting protect margins, examine customer engagement through attendance patterns.

## About the Data
This dataset captures 1,998 gym members' record across 4 branches in Nigeria, for the period 2022-2025, covering demographics, membership and pricing details, engagement patterns and add-ons like personal training, Group class. Columns in the table are: 

## Data Dictionary
| # | Field | Description | Data Type |
|---|-------|-------------|-----------|
| 1 | Age | Age of the member | Integer |
| 2 | Membership type | Category of membership, e.g. Basic, Premium | Text |
| 3 | Visit per week | Total number of visits per week | Integer |
| 4 | Days per week | Day of the week the member attends the gym | Text |
| 5 | Attend group lesson | Whether the member attends group classes | Boolean (Yes/No) |
| 6 | Avg time check in | Average time of day the member checks in | Time |
| 7 | Avg time check out | Average time of day the member checks out | Time |
| 8 | Duration in gym minutes | Average length of a gym session, in minutes | Integer |
| 9 | Personal training | Whether the member uses personal training services | Boolean (Yes/No) |
| 10 | Self identified gender | Member's self-identified gender | Text |
| 11 | Subscription price | Standard/list price of the member's subscription | Numeric |
| 12 | Subscription model | Billing structure, e.g. Monthly, Quarterly, Annual | Text |
| 13 | Adjusted price | Price after any base adjustments | Numeric |
| 14 | Discount type | Category of discount applied, if any | Text |
| 15 | Discount rate | Percentage or amount discounted | Numeric (%) |
| 16 | Final price | Actual price paid after all adjustments and discounts | Numeric |
| 17 | Access hours | Hours during which the member's plan permits gym access | Text |
| 18 | Join date | Date the member joined RevUp | Date |
| 19 | Personal training hours | Total hours of personal training used | Numeric |
| 20 | Last visit date | Date of the member's most recent gym visit | Date |
| 21 | Home gym location | City/area associated with the member's primary branch | Text |
| 22 | Branch | Specific branch name where the member is registered | Text |


## Tool & Methodology
### Tools Used:

Microsoft SQL Server was used for data cleaning, transformation, and analytical querying. This included creating views, a trigger, and stored procedures.

Microsoft Excel was used for visualization. PivotTable to summarize and charts to visualize the summarized data on a three page interactive dashboard, which includes branch and time period filtering for exploration.

### Methodology:
This project follows an end-to-end analytical workflow from raw data to a ready to use dashboard to make decisions structured in five stages: Data collection, Data Preparation, Exploratory Analysis, deep-dive Analysis, and Visualization.
- Data Collection:
The dataset used for this analysis contained gym member records for RevUp’s Fitness across its 4 branches, covering the period January 2022 through July 2025. 
- Data Preparation and Cleaning:
The raw data was loaded directly using microsf sql server via Tasks → Import Data.<br>
Row counts: 1998 records were found. <br>
Duplicates and Null values: The join_date column has one empty row. No duplicates. <br>
Data Standardization: Column data types were corrected to appropriate types to ensure further analysis is built on the right foundation.
Data Validation: Logical consistency checks were run across the dataset, including: date logic (`last_visit_date` should never precede `join_date`), price logic (`final_price` should not exceed `subscription_price`), and range checks on categorical and numeric fields (age, discount rate, session duration).<br>
Add new columns:
Customer ID- A unique member identifier was created using an auto-incrementing key. <br>
Age bracket : An age based generational grouping of members. Gen z (12-28), Millenials (29-44) and Gen x(45-49) <br>
Revenue lost to discount: This is the difference between  subscription price and final price i.e before discount was given.<br>
Membership status: A three-tier classification (Active / At Risk / Churned), based on days since last visit measured against the most recent date present in the dataset. Churned Members:  Inactive for more than 50 days. At Risk members: Members inactive between 31–50 days while all others are classified as Active.<br>
With clean data, the next stage answers foundational questions about the dataset itself: how many members exist per branch, what the distribution of membership types looks like, and how metrics like price, tenure, and engagement are spread.This step surfaces the shape of the data  before deeper questions are tackled.
- Deep-Dive Analysis 
Core business questions are answered with SQL queries: revenue and retention by membership type, the impact of pricing models and discount types, branch-level engagement and revenue, the influence of personal training and group classes, access-type impact on visit frequency, weekly usage patterns by segment. Each query connects back to the single underlying question the business is really asking: which members are worth keeping, and what does it take to keep them?
- Data Visualization
The query summarized outputs from SQL are exported into Excel. Pivot tables were used to summarize the data , and charts to visualize the summarized data. Four  KPI cards (Revenue, Members, Retention Rate and Avg Tenure days) and ten supporting charts with all charts filterable by branch and time period via a slicer connected across the full report..


## Dashboard 
### Overview Page
![Alt text](https://github.com/AwololaRukayat/Membership-Analytics-Engagement-Insights/blob/e31d2f2e710df667958a243c0bf10f9ad151a9c2/Image/Overview.png) <br>
- Revenue & Growth
RevUp Fitness generated a total of ₦68.87M in revenue between 2022 and 2025, growing sharply from ₦10.80M in 2022 to a peak of ₦23.96M in 2023, before declining slightly to ₦22.12M in 2024. This trajectory closely tracks membership acquisition, 2023 recorded the highest number of new sign-ups (692) against a low of 308 in 2022, explaining that year's revenue spike. However, member growth continued into 2024 without revenue scaling proportionally alongside it, meaning new members were not converting into long-term. This matters because it signals retention concern raised initially, acquisition alone will not sustain growth if the members being acquired don't stay.

## Engagement Page 
![Alt text](https://github.com/AwololaRukayat/Membership-Analytics-Engagement-Insights/blob/e31d2f2e710df667958a243c0bf10f9ad151a9c2/Image/Engagment.png) <br>

- Retention Rate
Across the full membership base of 1,998 members, an average of 1,323 members (66%) were retained at the end of each year. This falls within the fitness industry's typical historical range of 60–70% annual retention. This places RevUp Fitness within industry norms rather than in crisis but also confirms it is not outperforming its sector, meaning there is genuine, addressable room to improve. 
Retention by membership type reveals an important distinction: Premium members have the most members (812) and highest retention (41%) while Elite has (199) members with the least retention (10%). The retention for elite is likely due to its smaller base size not a loyalty gap, and highlights the importance of distinguishing retention rate from retention volume before making strategic decisions.

- Tenure by Membership Type
Average member tenure is (554 days) and varies by membership type: Standard members show the longest average tenure (609 days), with Basic the shortest (522 days) a notable finding since Standard, not a premium tier, is quietly the most loyal segment.

- Engagement by Generation
Gen Z leads both visit frequency (2,425 visits) and session duration (107 minutes), followed by Millennials (2,246 visits, 106 minutes). Gen X shows the lowest session duration (96 minutes). Gen Z and Millennials represent the network's most engaged generational base, making them a high potential segment for retention focused marketing, personalization, flexibility, and understanding what drives their engagement could inform strategies to lift engagement among less active generational segments.

## Discount Impact Page
![Alt text](https://github.com/AwololaRukayat/Membership-Analytics-Engagement-Insights/blob/e31d2f2e710df667958a243c0bf10f9ad151a9c2/Image/Discount.png) <br>
- Discount Impact
The total amount lost to dicount is ₦4.25M, Student discount  drives the highest revenue loss (₦2.13M), followed by Loyalty (₦1.45M) with applied rates of Student 15%, Loyalty 10%, Promo 5%, and None 0%. The Student discount carries both the highest individual rate and the highest total revenue impact, meaning its cost is driven by a combination of depth and volume, not one factor alone. Loyalty members are the most loyal with the longest tenure (646 days), followed by members with no discount (542 days). Student discounted members show the shortest tenure (515 days) which is the opposite of what well discounted members should produce, and suggests the Student discount may be attracting less committed members. Also discount doesn’t drive growth as most members (42%) are non discounted members.
- Service Engagement
Personal Training is the leading engagement driver (532 members), followed by members using both Personal and Group Classes (502 members). Members using neither services (464) showed that they may be engaged with the facility itself and not the services i.e their loyalty isn’t from accountability from a trainer or group classes. Priority should be on understanding why they prefer independent gym use.

## Branch Performance

| Branch | Total Members | Retention Rate | Total Revenue | Avg Tenure (Days) | No. of Locations |
|--------|---------------|----------------|---------------|-------------------|------------------|
| Lagos | 1,420 | 67% | ₦48.65M | 567 | 25 |
| Ibadan | 111 | 61% | ₦3.88M | 509 | 1 |
| Port Harcourt | 199 | 65% | ₦6.68M | 507 | 2 |
| Abuja | 268 | 64% | ₦9.66M | 538 | 3 |

## Recommendations
- Reassess the Student Discount Strategy: 
Reduce the Student discount rate, cap its usage, or restructure it with retention conditions attached (e.g., a lower initial rate that increases toward full price after a defined period). The data confirms this discount costs the most while retaining the fewest members, and remains the leading source of revenue loss.  This is reinforced by the findings that non-discounted members are consistently the most engaged and longest-retained group.
- Apply Branch Specific Discount Rules, Not a Single Network Wide Policy: 
Avoid a blanket "discounts hurt retention" policy applied uniformly across the network. Loyalty and Promo discounts correlate with stronger tenure in some branches and should be preserved or expanded there, while Student discounts should be tightened everywhere. Ibadan's discount mix should be reviewed independently given its low retention.
- Centralize and Standardize Discount Issuance Timing: 
Discount issuance currently follows a rotating quarterly pattern by branch  Abuja peaks in Q4, Ibadan in Q3, Lagos in Q1, and Port Harcourt in Q2  rather than a single, coordinated national strategy. This pattern may be as a result of  local sign up target pressure rather than deliberate pricing strategy. Finance should introduce a centralized discount approval calendar or quota system, so discounting is driven by strategic timing (e.g., genuine seasonal demand) rather than individual branch managers issuing discounts to hit monthly targets.
- Promote Monthly Subscriptions as the Default Acquisition Offer: 
Monthly subscriptions retain best in every branch, ranging from 59% to 65% the most consistent, dependable retention pattern tied to a subscription model. Sales and Marketing should position Monthly as the default recommended plan for new sign-ups, rather than pushing Quarterly or Early Bird plans as a default, since neither shows comparable retention strength anywhere in the network.
- Prioritize Premium Membership as the Core Retention and Upsell Lever:
Use Premium as the primary target tier for converting Basic members upward and for retention focused marketing and renewal campaigns. This is the only finding in the entire analysis that holds true across all four branches with zero exceptions.
- Clarify Elite Membership's Retention Rate Before Acting on It: 
Before drawing conclusions about Elite tier performance, confirm whether its low retention count reflects a smaller cohort size or a genuine at risk segment warranting targeted outreach.
- Tailor Service Bundling Strategy by Branch, Not Network-Wide: 
Group Training leads engagement in three of four branches (Abuja, Ibadan, Port Harcourt), while Lagos stands apart with the combined Personal Training + Group Class leading instead, likely a reflection of Lagos's scale (25 locations). Rather than promoting “Both”, Lagos should pilot the bundled offering first, while Abuja, Ibadan, and Port Harcourt should focus on deepening and promoting their existing Group Training programs, which already show stronger organic engagement.
- Conduct a Standalone Operational Review of Ibadan:
This analysis alone cannot determine whether Ibadan's performance stems from genuine lower local demand,or a marketfit issue specific to that location. A focused operational review covering access hour distribution, and local pricing sensitivity is recommended before any network wide strategy  including recommendations 1 through 7 above  is applied to Ibadan.

## Limitation
While this analysis provides meaningful insights, certain limitations must be acknowledged: 

- Fitness membership doesn't capture data such as:
 Profitability which will help understand the cost ( staffing, rent, utilities, or equipment expenses) incurred in running the gym. As a result, this analysis reports Net Revenue (revenue after discounts), not profitability. 

- Satisfaction: 
The dataset contains no direct satisfaction metric (survey scores, NPS, reviews, or complaints). Any reference to member satisfaction in this analysis is inferred from behavioral factors- visit frequency, session duration, and tenure rather than a direct measure of how members feel about their experience. 

- The Incomplete 2025 data limit the ability to fully compare 2025 performance across all rest of the year.
## Assumption
This analysis relies on several assumptions made in the absence of direct confirmation from business rules. 
- Final price is assumed to reflect actual revenue generated i.e the final price members paid.
- Discount logic (`discount_type`, `discount_rate`) is assumed to follow a single, consistent calculation per member. 
- Branch and home_gym_location are treated as each member's current registered branch.
- Retention measures the percentage of members who remained active at the end of each year.
  
# Implementation 

## Recommendation 1: Restructure the Student Discount

What: Reduce the Student discount rate from 15% to a maximum of 8–10%, or restructure it as a graduated discount (e.g., 15% for the first 3 months, stepping down to 5% thereafter), applied to new sign-ups first.

Who:
- Owner: Finance Manager 
- Support: Branch Managers , Analytics team 
- Approval: CFO

When:
- Week 1: Confirm exact current cost and volume of Student discount usage by branch.
- Week 2: Model 2–3 alternative discount structures against historical tenure data.
- Week 3: Present recommended structure for CFO approval.
- Week 4: Update discount configuration in the membership system for new sign-ups.
- Month 2–3: Monitor tenure of new Student cohort against the previous 15% rate.
- Month 4: Review results; extend to existing Student members at renewal if successful.

Success Metrics:
- Revenue lost to Student discounts reduced by at least 25% .
- Average tenure of new Student discounted members increases toward the Loyalty/Promo benchmark within 90 days.
- No more than a 10% drop in new Student sign-up volume (acceptable trade-off; larger drops require re-evaluation)


Resources Needed:
- Finance analyst time to model discount scenarios (~5 hours/week for 3 weeks).
- Membership system configuration access (IT/Admin).
- No additional budget required. This is a cost-reduction change, not a spending increase.

Risks & Mitigations:
- Risk: Reduced discount suppresses student sign-ups more than expected.
 Mitigation: Pilot the new rate in one branch first; compare sign-up volume before full rollout.
- Risk: Existing Student members react negatively if the discount is changed on active memberships.
 Mitigation: Apply the new rate only to new sign-ups initially; existing members retain their current rate until renewal.

Dependencies:
- Membership/billing system must support tiered or time-based discount rates
- Branch managers must be briefed before the change goes live, to handle member questions consistently.


## Recommendation 2: Promote Premium Membership as the Primary Retention Lever

What: Launch a targeted upsell campaign converting Basic and Standard members, prioritizing members who are highly engaged (frequent visits, long sessions) but not yet on Premium.

Who:
- Owner: Sales & Marketing Lead
- Support: Branch Managers, Analytics team 
- Approval: CMO/Marketing Director

When:
- Week 1: Analytics team pulls list of high-engagement, non-Premium members by branch
- Week 2: Marketing designs upsell messaging and incentive (e.g., first-month discount on upgrade)
- Week 3–4: Pilot campaign in Lagos (highest-volume branch)
- Month 2–3: Roll out to Abuja, Port Harcourt, and Ibadan based on pilot results
- Month 4: Measure and refine

Success Metrics:
- 15% of targeted members convert to Premium within 90 days
- Network wide Premium membership share increases measurably quarter-over-quarter
- Overall retention rate trends upward as Premium's share of total membership grows

Resources Needed:
- Budget: incentive cost for upgrade offers 
- Time: ~10 hours/week (Marketing), branch manager time for in-person conversations
- Tools: existing membership CRM/system for targeted outreach

Risks & Mitigations:
- Risk: Upsell attempts feel pushy and damage member goodwill
 Mitigation: Target only genuinely high engagement members identified through the data
- Risk: Conversion rate is too low to justify campaign cost
 Mitigation: Eliminate or redesign the campaign if pilot conversion falls below 8% after 30 days

Dependencies:
- Branch managers must be trained on Premium's value proposition before conversations begin
- Analytics team must refresh the target member list monthly as engagement data updates

## Recommendation 3: Operational Review of Ibadan

What: Conduct a structured review of Ibadan's staffing levels, access-hour distribution, and local market conditions to determine the root cause of its below network tenure and retention figures.

Who:
- Owner: Operations Manager
- Support: Ibadan Branch Manager, Analytics team 
- Approval: COO/Operations Director

When:
- Week 1–2: Pull and review Ibadan specific staffing schedules and access hour member distribution
- Week 3: On-site or remote interviews with Ibadan branch staff and a sample of members
- Week 4: Compile findings and root-cause assessment
- Month 2: Present findings and proposed branch specific action plan

Success Metrics:
- A clear, evidence-based determination of whether Ibadan's shortfall is demand driven, staffing driven, or market-fit-driven
- A branch specific action plan approved and ready for execution by end of second Month 

Resources Needed:
- Operations staff time (~1 week dedicated review)
- Possible small budget for member interviews/incentives if primary research is needed

Risks & Mitigations:
- Risk: Review concludes without a clear root cause
 Mitigation: Scope the review narrowly (staffing, access, and local competition) rather than open ended, to ensure a decision-ready outcome
- Risk: Findings are deprioritized without a Premium/discount campaign parallel in Ibadan
 Mitigation: Explicitly pause network wide rollout of Recommendations 1 and 2 in Ibadan until this review is complete

Dependencies:
- This review should be treated as a prerequisite before applying Recommendations 1 or 2 to Ibadan

## Conclusion
This analysis provides a structured evaluation of RevUp Fitness performance between 2022-2025. Retention is healthy, but not strong. RevUp retains about 66% of total members each year (1,323 out of 1,998)  in line with the fitness industry average of 60–70%. Discounts are a mixed bag, and one type is clearly a problem. The Student discount costs the business the most (₦2.13M lost, at a 15% rate) and is linked to the shortest member tenure in three branches. In plain terms: it's the most expensive discount, and it keeps members the least amount of time. Members who receive no discount often stay longer than members who pay got price. Premium membership is the strongest, most reliable finding in the entire report. It has the highest retention of any tier  in every single branch, with no exceptions. 
Branch performance tells its own story. Lagos drives the business, holding 71% of all members and 70% of all revenue (₦48.65M of the ₦68.87M total) any change made there will have the biggest impact on the whole company, simply because of its size. Ibadan, on the other hand, needs a closer look: it has an Avg tenure (509 days) and lowest retention (~61%) of all four branches, and is the only branch with just one location instead of several. This alone doesn't tell us why, it just tells us this branch doesn't behave like the others, and deserves its own investigation before applying company wide fixes to it. 6% of revenue was lost to discount and varies among the discount type, 42% of members have no discount indicating discount doesn’t drive growth.





