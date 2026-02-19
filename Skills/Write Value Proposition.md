---
name: write-value-proposition
description: Facilitates creation and refinement of value propositions using the Strategyzer Value Proposition Canvas, supporting new products, existing offerings, multiple segments, and validation testing.
---

# **Purpose**
This skill helps product managers and teams design compelling value propositions using the Strategyzer Value Proposition Canvas. It guides users through the Customer Profile (jobs, pains, gains) and Value Map (products/services, pain relievers, gain creators) to achieve strong product-customer fit. Based on _Value Proposition Design_ (Osterwalder et al., Strategyzer).

## When To Use
- Use when creating a value proposition for a new product or feature.
- Use when refining an existing value proposition that lacks clarity or resonance.
- Use when developing multiple value proposition variations for different customer segments.
- Use when testing or validating a value proposition with customers or stakeholders.
- Use during discovery to align offerings with customer needs before or after a Lean Canvas session.

## When Not To Use
- Do not use when the user needs a full business model (use **lean-canvas-brainstorm** instead).
- Do not use when the primary goal is competitive analysis (use **market-research** instead).
- Do not use when the user needs implementation-ready requirements (use **write-prd** instead).

# **Overall Agent Process**
1. **Determine Context:** Identify whether the user is creating new, refining existing, building segment variations, or testing a value proposition.
2. **Gather or Reference Inputs:** Collect customer segment, product/offering, and any existing canvas or research. Suggest **market-research** or **customer-interview-prep** if customer understanding is weak.
3. **Build Customer Profile First:** Fill the Customer Profile (right side) with jobs, pains, and gains—one segment per canvas. Use the "Five Whys" to uncover deeper motivations.
4. **Build Value Map:** Design the Value Map (left side) to address the highest-priority jobs, pains, and gains. Make deliberate tradeoffs; do not try to address everything.
5. **Check Fit:** Verify that pain relievers and gain creators map to important jobs, extreme pains, and essential gains. Mark addressed (✓) vs. unaddressed (×) elements.
6. **Output Canvas Artifact:** Present the Value Proposition Canvas using the Markdown layout. Include Fit Check and optional ad-lib statement. For multiple segments, output separate canvases.
7. **Suggest Next Steps:** Recommend validation (e.g., **product-validation-plan**) or downstream work (e.g., **write-prd**, **lean-canvas-brainstorm**) based on fit stage.

## Specific Process Details

### 2. Gather or Reference Inputs
- If the user has completed a Lean Canvas, reference the **Customer Segments**, **Problem**, **Solution**, and **Unique Value Proposition** blocks to seed the Value Proposition Canvas.
- If customer understanding is thin, suggest running **market-research** or **customer-interview-prep** before or in parallel. The **customer-interview-prep** skill can follow the Value Proposition Design flow: create profile → create interview outline → conduct interview → capture → search for patterns → synthesize.
- If refining an existing value proposition, ask for the current statement, customer feedback, and known gaps.

### 3. Build Customer Profile First
The Customer Profile contains only **observable** elements about the customer—things outside your direct control. Complete this before the Value Map.

**Jobs-to-be-done:** Tasks customers are trying to accomplish, problems they are trying to solve, or needs they are trying to satisfy. _Jobs are tasks; gains are outcomes—do not mix them._ Label each as:
- **Functional:** Tangible tasks (e.g., "process invoices," "track inventory").
- **Social:** How others perceive them (e.g., "impress my boss," "look credible to peers").
- **Emotional:** How they want to feel (e.g., "feel in control," "reduce anxiety").

**Supporting jobs** (when relevant): Jobs arising from customer roles—**Buyer of value** (comparing offers, deciding, buying, checkout, delivery), **Cocreator of value** (reviews, feedback, participating in design), **Transferrer of value** (canceling, disposing, transferring, reselling).

**Job context:** Consider the context in which jobs are performed (e.g., calling on a train vs. in a car). Context may impose constraints or change priorities.

Push beyond functional jobs; social and emotional jobs often drive stronger differentiation.

**Customer Pains:** Anything that annoys customers before, during, or after trying to get a job done, or prevents them from getting it done. Seek three types:
- **Undesired outcomes/problems:** Functional, social, emotional, or ancillary (e.g., "solution doesn't work," "I look bad doing this").
- **Obstacles:** Things that prevent or slow progress (e.g., "I lack the time," "I can't afford existing solutions").
- **Risks:** Potential bad outcomes (e.g., "I might lose credibility," "a security breach would be disastrous").

Use "Five Whys" to reach root causes. **Make pains concrete:** Instead of "takes too long," specify "wasting more than X minutes." Ask how customers measure pain severity.

**Pains vs. Gains:** Do not put opposites in both (e.g., "salary increase" in gains and "salary decrease" in pains). Pains should focus on barriers, obstacles, and risks—not the inverse of gains.

**Customer Gains:** Benefits and outcomes customers want. Seek four types:
- **Required:** Must-haves without which a solution wouldn't work.
- **Expected:** Baseline gains we expect from a solution.
- **Desired:** Beyond expectations; customers would love to have them.
- **Unexpected:** Beyond what customers would ask for; delighters.

**Make gains concrete:** Instead of "better performance," specify "increased performance of more than X."

**Rank jobs, pains, and gains:**
- **Jobs:** Important vs. Insignificant
- **Pains:** Extreme vs. Moderate
- **Gains:** Essential vs. Nice to have

**One segment per canvas:** Never mix multiple customer segments (e.g., payers and users) into one Customer Profile. Create separate canvases for each segment.

**Avoid product lens:** Step into the customer's shoes. Do not list only jobs, pains, and gains that the current product addresses. Think like an anthropologist—what do customers really need and want?

### 4. Build Value Map
The Value Map contains elements you **design**—things within your control.

**Products & Services:** The bundle of offerings that help customers get jobs done. List only those targeted at the specific customer segment. Types may include: Physical/tangible, Intangible, Digital, Financial.

**Pain Relievers:** How your offering alleviates specific customer pains. Link each to a pain in the Customer Profile. Do not add products or services here—these are explanations of how value is created. It is okay if a pain reliever also addresses gains.

**Gain Creators:** How your offering creates desired gains. Link each to a gain in the Customer Profile. Do not add products or services here. It is okay if a gain creator also addresses pains.

**Focus on priority:** Address only the highest-priority jobs, extreme pains, and essential gains. Make deliberate tradeoffs. Trying to satisfy everything leads to weak, unfocused value propositions.

### 5. Check Fit
You achieve **Fit** when customers get excited about your value proposition—when you address important jobs, alleviate extreme pains, and create essential gains. Three stages:
- **Problem-Solution Fit (on paper):** You have designed a value proposition that addresses relevant jobs, pains, and gains. Not yet validated with customers.
- **Product-Market Fit (in the market):** Evidence that your value proposition creates customer value and gets traction.
- **Business Model Fit (in the bank):** Evidence that the value proposition can be embedded in a profitable, scalable business model.

For each pain reliever and gain creator, verify it maps to a job, pain, or gain in the Customer Profile. Mark addressed (✓) and unaddressed (×) elements. If a pain reliever or gain creator doesn't fit anything, it may not be creating customer value.

### 6. Output Canvas Artifact
Use the following Markdown structure to present the Value Proposition Canvas:

```markdown
## Value Proposition Canvas: [Customer Segment Name]

### VALUE MAP (Left)                    | ### CUSTOMER PROFILE (Right)
--------------------------------------|--------------------------------------
**Products & Services**               | **Customer Jobs** (Important ↓ Insignificant)
• [Offering 1]                        | • [Job 1] (functional/social/emotional)
• [Offering 2]                        | • [Job 2]
• [Offering 3]                        | • [Job 3]

**Pain Relievers**                    | **Pains** (Extreme ↓ Moderate)
• [Reliever 1] → [Pain] ✓             | • [Pain 1]
• [Reliever 2] → [Pain] ✓             | • [Pain 2]
                                     | • [Pain 3] × (not addressed)

**Gain Creators**                     | **Gains** (Essential ↓ Nice to have)
• [Creator 1] → [Gain] ✓               | • [Gain 1]
• [Creator 2] → [Gain] ✓              | • [Gain 2]
                                     | • [Gain 3] × (not addressed)

**Fit Check:** [Count of ✓ vs. ×. Note which important jobs, extreme pains, and essential gains are addressed vs. deprioritized.]

**Fit Summary:** [1–2 sentence statement of how the Value Map addresses the highest-priority Customer Profile elements.]

**Ad-lib (optional):** Our [products/services] help(s) [customer segment] who want to [job] by [pain reliever] and [gain creator] (unlike [alternative]).
```

### 7. Suggest Next Steps
- **Problem-Solution Fit:** Suggest **product-validation-plan** or **market-validation-plan** to test the value proposition with customers.
- **Product-Market Fit:** Suggest **write-prd** to capture requirements, or **lean-canvas-brainstorm** to expand into a full business model.
- **Business model:** Suggest **lean-canvas-brainstorm** if the user needs to expand into a full business model or validate Business Model Fit.

# **Integration with Other Skills**
- **lean-canvas-brainstorm:** Use to seed or extend the Value Proposition Canvas. The Lean Canvas "Unique Value Proposition" and "Problem/Solution" blocks map to the Value Map and Customer Profile.
- **market-research:** Use when competitive context or market understanding is needed to differentiate the value proposition.
- **write-prd:** Use after the value proposition is validated to capture implementation-ready requirements.
- **customer-interview-prep:** Use to gather evidence for jobs, pains, and gains. Follow the flow: create profile → interview outline → conduct → capture → search for patterns → synthesize.
- **product-validation-plan:** Use to design experiments that test the value proposition with real customers.

# **Final Instructions**
1. **Customer Profile before Value Map:** Always complete the Customer Profile first, without filtering through the product lens.
2. **One segment per canvas:** If the user describes multiple segments, create separate canvases. Do not merge them.
3. **Prioritize and trade off:** Help the user identify the top 3–5 jobs, pains, and gains to address. Use ranking (Important/Extreme/Essential). Explicitly note what is being deprioritized (×).
4. **Include social and emotional jobs:** Push beyond functional jobs when the user lists only obvious tasks.
5. **Link explicitly:** When filling the Value Map, show which pain relievers map to which pains and which gain creators map to which gains.
6. **Make it concrete:** Encourage specific, measurable descriptions for pains and gains (e.g., "more than X minutes," "increase of Y%").
