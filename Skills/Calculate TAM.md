---
name: calculate-tam
description: Sizes the Total Addressable Market (TAM), Serviceable Available Market (SAM), and Serviceable Obtainable Market (SOM) to expose, challenge, and test assumptions for market opportunity.
---

# **Purpose**
This skill helps product managers calculate the size of a market opportunity. It goes beyond simple math to expose and challenge the assumptions behind "who is out there," "will they buy it," and "at what price," providing a data-driven foundation for prioritizing product options.

## When To Use
- Use when evaluating a new product or feature idea to understand the potential revenue ceiling.
- Use when building a business case for internal funding or stakeholder approval.
- Use to prioritize different market segments or demographics.
- Use to define targets for sales and marketing teams (SOM).

# **Overall Agent Process**
1. **Define Market Tiers:** Distinguish between the Total Addressable Market (TAM), Serviceable Available Market (SAM), and Serviceable Obtainable Market (SOM).
2. **Conduct Research:** Approach sizing through competitive analysis, primary research (interviews/surveys), and secondary research (industry reports).
3. **Execute TAM Calculation:** Walk through the five-step math process (Universe -> Interest -> Conversion -> Price -> Result).
4. **Challenge Assumptions:** Explicitly identify the hypothesis behind each variable and suggest ways to test them.
5. **Output the Market Model:** Present the final calculation with visible assumptions and a tracking plan.

## Specific Process Details

### 1. Define Market Tiers
- **TAM (Total Addressable Market):** Total market demand for the product or service.
- **SAM (Serviceable Available Market):** The segment of the TAM targeted by your products which is within your geographical and technical reach.
- **SOM (Serviceable Obtainable Market):** The realistic portion of SAM that you can capture.

### 3. Execute TAM Calculation
1. **Determine the Possible Universe:** Identify the total number of potential clients that exist.
2. **Determine Interest by Proxy:** Use binary scores (0 or 1) to filter the universe (e.g., current clients only, enterprise-only, or specific industry).
3. **Estimate Conversion Likelihood:** Assign a conservative percentage for how likely an interested client is to convert.
4. **Determine Price:** Assign a median dollar amount converted clients would pay, potentially varied by client size (ARR).
5. **Calculate Final TAM:** Multiply the converted prospects by the determined price.

For visibility of assumptions, alternatively use the "Drake Equation":
**TAM = N * price**
Where *N* = (Total # of potential clients) * (Probability of interest) * (Probability of conversion).

# **Final Instructions**
1. **Be Conservative:** It is better to underestimate interest and conversion than to overestimate.
2. **Expose Assumptions:** Do not provide a single number without listing the underlying hypothesis for each variable.
3. **Plan for Tracking:** Suggest ways to quantify and track these assumptions before and after launch to support course correction.
