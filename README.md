**ABC Test Analysis**

**Problem Statement**

The Project is to work with sample datasets relating to a new in-app screen (let's say app name - Troop ) presented to users. After a user has installed the Troop app, we ask them to verify their phone number as an initial layer of security. The user is asked to enter their phone number, and once submitted to us they receive a message with a one-time password (OTP). If the new user successfully enters the OTP, they reach the next layer of security and can start building their Troop profile.

In this challenge, we have a sample results from an ABC test (with each variant shown at random to users) which include an additional an option to verify your phone number using WhatsApp as opposed to Text message (SMS):

A SMS Only → Verify your phone number using SMS

B SMS Primary → Verify your phone number using SMS or WhatsApp

C WhatsApp Primary → Verify your phone number using WhatsApp or SMS

The task is to analyze the data and decide if the feature has led to an improved product. Note that, we have only provided data for the first method of verification each user selected.

**Analysis Approach**

**Overview**

An A/B/C test was conducted to evaluate the performance of three different screens in the user flow. The primary goal is to increase the conversion rate, measured as the proportion of users who successfully completed verification. Secondary metrics included method selection rates, cost per verified user, and demographic splits (gender, age, country).

**Hypothesis**

**Null Hypothesis:** There are no considerable differences between the three variations

**Alternate Hypothesis:** There will be considerable variation within the three

**Success Metrics**

**Primary metric -** Verification Conversion Rate

**Secondary metrics:**

\- Method selection rate

\- Demographic splits

\- Cost per verified user

**Guardrail metric** - Non verification rate (failures, drop-off, abandoned etc)

These were chosen because:

\- Conversion rate directly measures success of the screen

\- Cost and method provide operational insights

\- Demographics ensure results are not biased by user composition

**Analytical Approach**

Total users reached:

Group A - 6382

Group B - 5924

Group C - 6118

Before diving into the analysis, I looked at the demographic breakdown of the data to make sure it's balanced and not biased. This helps ensure that our analysis reflects the full picture.

**Overall Conversion Rates**

| **Group** | **Users** | **Verified** | **Conversion_rate** |
| --- | --- | --- | --- |
| A   | 6382 | 5573 | 87.32% |
| --- | --- | --- | --- |
| B   | 5924 | 5498 | 92.81% |
| --- | --- | --- | --- |
| C   | 6118 | 5679 | 92.82% |
| --- | --- | --- | --- |

**Primary metric: Conversion Rate**

**Statistical Analysis**

- **Chi-square test (overall A/B/C) →** χ²=152.372, p=0.0000 → Statistically significant

There is a statistically significant difference in conversion rates between at least one pair of groups. In other words, the performance of the screens is not the same - at least one screen performs meaningfully better or worse than the others.

- **Pairwise two-proportion z-tests** to identify which specific groups differ from each other

The results were:

\- **A vs B:** diff = +5.5 percentage points (pp), p < 0.001 → statistically significant

\- **A vs C:** diff = +5.5 pp, p < 0.001 → statistically significant

_\-_ **B vs C:** diff = 0.02 pp, p = 0.97 _→_ not significant

**Groups B and C** both significantly outperform Group A in terms of conversion rate, while there is no significant difference between B and C. This indicates that either B or C could be chosen as the better-performing screen, as both deliver equally strong results.

**Secondary metrics**

**Method selection rate**

From the chart, it suggests that users prefer WhatsApp when given the option, but Group A's experience didn't even expose that option.  

This likely impacted verification rates (12.68% non-verified), since WhatsApp might be faster or more user-friendly in some countries, but not accessible in others.

**Cost per verified user**

The cost per verified user is nearly identical across all three groups, only a \$0.001 difference between A and B (less than 1% variation).  
This means that the new designs (B and C) achieve their higher conversion rates (as you found earlier) without increasing cost.

| **Group** | **Total cost (usd)** |
| --- | --- |
| **A** | **\$ 0.146** |
| --- | --- |
| **B** | **\$ 0.147** |
| --- | --- |
| **C** | **\$ 0.146** |
| --- | --- |

**Guardrail metrics**
- Drop off rate after verification
- Time to successful verification
- Bounce Rate
  
**Executive Summary**

- From the analysis, it is clear that offering a second option significantly improves outcomes compared to restricting users to a single option, which led to increased failures.
- When comparing Option B and Option C, both perform better across primary, secondary, and guardrail metrics, indicating that either could be a viable choice. However, selecting between B and C would require a longer testing duration to reach a conclusive result.
- Additionally, keeping WhatsApp as the primary option could introduce challenges in regions where it is highly restricted or banned, making this an important consideration in the decision-making process.

**Additional Data Needs**

- Regional availability and restrictions for each messaging option
- User engagement and behavioral metrics (click through rates, user onboarding)
- Success rates over a longer duration to capture behaviour changes over time and in unusual situations.
- Long-term performance metrics (Retention or continued engagement after first use, sessions per user)
