---
name: calculate-roi
description: Forecasts the profitability of a new product or feature by calculating the 3-year Return on Investment (ROI) based on initial CapEx, ongoing OpEx, and projected revenue.
---

# **Purpose**
This skill helps product managers build a financial forecast to understand when an initial investment will generate revenue and what the overall return will be after three years. It bridges the gap between market sizing (TAM) and financial viability, providing a clear business case for new initiatives.

## When To Use
- Use when building a business case for a new product or feature.
- Use to compare the potential profitability of different product options.
- Use during annual or quarterly planning to justify resource allocation.
- Use to identify the "break-even" point for a specific investment.

# **Overall Agent Process**
1. **Identify Initial Investment (CapEx):** Determine the Year 1 costs required to build and launch the solution.
2. **Determine Ongoing Investment (OpEx):** Identify yearly operational expenses for Years 2 and 3.
3. **Integrate Revenue Forecasts:** Gather projected annual income (ideally informed by the `calculate-tam` and `pricing-brainstorm` skills).
4. **Calculate Annual Net Profit:** Subtract OpEx from revenue for each year.
5. **Determine 3-Year Totals:** Sum the net profit across the 3-year period.
6. **Output the ROI Model:** Present a structured table showing the Year 1–3 breakdown and the final ROI percentage.

## Specific Process Details

### 1. Identify Initial Investment (CapEx & OpEx)
- **CapEx (Capital Expenditure):** The initial "one-time" investment in Year 1.
- **OpEx (Operating Expenditure):** Ongoing costs like hosting, maintenance, and support.
- **Accuracy Factors:** Proactively ask about additional expenses like Customer Support resources, COGS (Cost of Goods Sold), or new CAC (Customer Acquisition Cost) for marketing campaigns.

### 6. Output the ROI Model
Use the following formula:
**ROI % = (Total 3-Year Net Profit) / (Initial CapEx Investment)**

Present the final result in this format:

```markdown
| Category                         | Year 1   | Year 2   | Year 3   | **TOTAL**               |
| -------------------------------- | -------- | -------- | -------- | ----------------------- |
| **Initial Investment (CapEx)**   | [Amount] |          |          | [Amount]                |
| **Annual Income (Revenue)**      | [Amount] | [Amount] | [Amount] | [Amount]                |
| **Ongoing Investment (OpEx)**    | [Amount] | [Amount] | [Amount] | [Amount]                |
| **Annual Net Profit**            | ([Loss]) | [Amount] | [Amount] | **[3-Year Net Profit]** |
| **ROI % Over 3 Years**           |          |          |          | **[Percentage]%**       |
```

# **Final Instructions**
1. **Factor in COGS:** Always ask if a percentage of revenue is paid to third-party data providers or partners.
2. **Be Realistic:** Remind users that Year 1 typically shows a net loss due to the initial CapEx.
