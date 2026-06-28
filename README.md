# vivekvishwakarma_bitsom_ba_2511306_part2_kpi_experiment

# Part 2: KPI Framework & Business Experiment Analysis

## Business Context
The company tested a new onboarding and activation campaign (Treatment) against the existing experience (Control) to improve early engagement and conversion. Leadership requires a data-driven recommendation on whether to launch this campaign globally.

## Dataset Description
- **Source:** `campaign_experiment_data.xlsx`
- **Scope:** User-level experiment logs tracking funnel progression (visits, trials, onboarding), monetization (conversion, revenue), and operational friction (support tickets, refunds).

## North Star Metric Selected
**Paid Conversion Rate (`converted_to_paid`):** Chosen because it is the ultimate measure of sustainable business growth. Top-of-funnel metrics are vanity indicators if they do not convert to paid subscriptions. 

## KPI Tree Summary
The North Star metric breaks down into a chronological 4-phase funnel:
1. **Top-of-Funnel Intent** (Landing Page Visits, Traffic Mix)
2. **Product Activation** (Trial Starts, Onboarding Completion)
3. **Engagement Velocity** (Engagement Score, Days to Convert)
4. **Revenue Yield** (ARPU, Premium Upgrades)
This is coupled with a strict risk layer monitoring **Guardrails**: Refund Request Rate and Support Ticket Escalation.

## Experiment Analysis Approach
Data was cleaned and validated prior to analysis. Missing categorical variables (device, traffic, plan) were standardized to 'Unknown' to ensure clean segment reporting. Nulls in `days_to_convert` were intentionally retained as they correctly represent non-converted users, and missing `engagement_score` values were left blank to prevent artificially skewing the pivot table averages.

## Hypothesis Test Summary
A two-tailed T-Test assuming unequal variances was conducted on the binary `converted_to_paid` column.
- **Null Hypothesis (H0):** There is no significant difference in the Paid Conversion Rate between the Control and Treatment groups.
- **Result:** The resulting P-Value was **0.000987**. Since this is well below the 0.05 alpha threshold, we reject the Null Hypothesis. The Treatment definitively drove higher conversion.

## Guardrail Metrics Considered
- 30-Day Refund Requested Rate
- Support Tickets per User
- Average Days to Convert
*Increases in these metrics signify operational friction and poor user-intent acquisition, which can offset revenue gains.*

## Final Recommendation
**Continue Testing.** Do not launch to 100% of the user base. Guardrail and segment analysis indicates that while the Treatment successfully altered funnel dynamics and increased conversion, it introduced severe operational strain—specifically a massive spike in Support Tickets among Mobile users (2.38 average tickets vs Desktop's 0.35). The mobile UX bottleneck must be isolated and fixed in a V2 iteration before a global launch.

## Assumptions and Limitations
- **Assumptions:** Revenue tracked is recognized MRR; support tickets are directly correlated with the onboarding experience.
- **Limitations:** The dataset does not provide granular timestamp data for funnel drop-offs or specific UI click-paths, limiting our ability to identify the exact screen causing the mobile support ticket spike.

## Screenshots Included
- `summary_metrics.png`: Aggregated Control vs Treatment performance with segment drill-downs.
- `hypothesis_test_output.png`: Evidence of statistical testing and P-Value generation.
- `kpi_tree_preview.png`: Visual breakdown of the North Star framework.
