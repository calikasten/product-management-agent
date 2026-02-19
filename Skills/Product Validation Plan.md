---
name: product-validation-plan
description: Designs a strategy to validate product hypotheses using the leanest possible methods, ranging from low-fidelity prototypes to production experiments and Minimum Viable Products (MVPs).
---

# **Purpose**
This skill helps product managers identify the fastest and most cost-effective ways to validate product assumptions. It systematically reduces the three types of risk (Desirability, Feasibility, Viability) through rapid experimentation, ensuring teams don't waste time, energy, and resources on ideas that won't work.

## When To Use
- Use when a new feature or product idea is proposed and needs validation.
- Use to choose between different testing methods based on cost, time, and evidence strength.
- Use to prioritize which hypotheses to test first using the Assumptions Mapping framework.
- Use to define the "Critical Path" from rough idea to "Earliest Lovable" product.
- Use when deciding if a Proof of Concept (PoC) is necessary before building an MVP.

# **Overall Agent Process**
1. **Formulate Hypotheses:** Write testable, precise, and discrete hypotheses for what needs validation.
2. **Map Assumptions:** Plot hypotheses on the Assumptions Map (Importance vs. Evidence) to identify riskiest areas.
3. **Determine Risk Type:** Categorize by Desirability (market), Feasibility (infrastructure), or Viability (financial) risk.
4. **Determine the Stage:** Choose between Discovery (weak evidence, fast learning) or Validation (strong evidence, confirmation).
5. **Select Experiments:** Choose validation methods based on cost, time, evidence strength, and constraints.
6. **Map the Critical Path for MVP:** Outline progression from "Earliest Showable" to "Earliest Lovable."
7. **Define Success Metrics:** Establish clear, measurable criteria with specific evidence thresholds.

## Specific Process Details

### 1. Formulate Hypotheses
Create testable, precise, and discrete hypotheses using the "We believe that..." format:
- **Testable:** Can be shown true or false based on observable evidence.
- **Precise:** Describes specific what, who, and when with clear success criteria.
- **Discrete:** Tests only one distinct thing.

**Example:** "We believe millennial parents with kids ages 5-9 will pay $15/month for curated science projects."

**Avoid Confirmation Bias:** Also write competing hypotheses to test (e.g., "We believe millennial parents won't subscribe...").

### 2. Map Assumptions (Prioritization Framework)
Use the Assumptions Map to identify which hypotheses to test first:

```
                    ASSUMPTIONS MAP
    
    Important  │  SHARE           │  EXPERIMENT     
               │  (Have Evidence) │  (No Evidence)  
    ───────────┼──────────────────┼─────────────────
               │  - Check evidence│  - Focus here   
               │  - Validate it's │  - High risk    
               │    recent/strong │  - Test first   
    ───────────┼──────────────────┼─────────────────
    Unimportant│  Monitor only    │  Test later     
               │                  │  (if at all)    
    ───────────┴──────────────────┴─────────────────
                Have Evidence       No Evidence
```

**How to Plot:**
- **x-Axis (Evidence):** Place left if you have recent, observable evidence; right if no evidence exists.
- **y-Axis (Importance):** Place top if hypothesis is critical for success; bottom if it's secondary.
- **Priority:** Focus experiments on the "Top Right Quadrant" (important with no evidence).

### 3. Determine Risk Type
Categorize each hypothesis by the three types of risk:

```
         THREE TYPES OF RISK
    
    ┌────────────────────────────────┐
    │   DESIRABILITY RISK            │
    │   (Market Risk)                │
    │                                │
    │   "Do they want this?"         │
    │   - Market too small?          │
    │   - Too few customers?         │
    │   - Can't reach/acquire them?  │
    └────────────────────────────────┘
    
    ┌────────────────────────────────┐
    │   FEASIBILITY RISK             │
    │   (Infrastructure Risk)        │
    │                                │
    │   "Can we do this?"            │
    │   - Can't get key resources?   │
    │   - Can't develop capability?  │
    │   - Can't find key partners?   │
    └────────────────────────────────┘
    
    ┌────────────────────────────────┐
    │   VIABILITY RISK               │
    │   (Financial Risk)             │
    │                                │
    │   "Should we do this?"         │
    │   - Can't generate revenue?    │
    │   - Customers won't pay?       │
    │   - Costs too high for profit? │
    └────────────────────────────────┘
```

**Test in Order:** Desirability first (no point building what nobody wants), then Feasibility, then Viability.

### 4. Determine the Stage
Choose between Discovery and Validation based on uncertainty level:

```
    DISCOVERY vs VALIDATION
    
    Idea ──────────────────────────────► Business
         [Search & Testing]        [Execution]
    
    High ─────────────────────────────► Low
    Uncertainty                     Uncertainty
    
    DISCOVERY                       VALIDATION
    ├─ Goal: Find direction        ├─ Goal: Confirm direction
    ├─ Evidence: Weak is OK        ├─ Evidence: Strong required
    ├─ Speed: Fast & cheap         ├─ Speed: More time/cost
    ├─ Examples:                   ├─ Examples:
    │  • Customer Interviews       │  • Concierge MVP
    │  • Paper Prototypes          │  • Presale
    │  • Landing Pages             │  • Clickable Prototype
    └─ • Fake Door Tests           └─ • Single Feature MVP
```

**Also Consider:**
- **Proof of Concept (PoC):** Focuses on **Feasibility** only. Validates "can this be built?"
- **Prototype:** Visual aid for **Desirability** feedback. Range from sketches to high-fidelity wireframes.
- **Minimum Viable Product (MVP):** Production-ready with minimum features to provide **Value** and test market.

### 5. Select Experiments

**EXPERIMENT SELECTION RULES OF THUMB:**
1. **Go cheap and fast at the beginning** - When uncertainty is high, use quick experiments to find direction.
2. **Increase evidence strength with multiple experiments** - Don't make big decisions based on one test.
3. **Pick strongest evidence given constraints** - Balance speed/cost with evidence quality.
4. **Reduce uncertainty before building** - The higher the build cost, the more you need to test first.

**Three Questions to Ask:**
1. **Type of hypothesis?** What risk am I testing (Desirability/Feasibility/Viability)?
2. **Level of uncertainty?** How much do I already know? (Less knowledge = cheaper/faster tests)
3. **Urgency?** When is my next decision point or funding deadline?

#### DISCOVERY EXPERIMENTS (Quick & Cheap, Weak-to-Moderate Evidence)

**Research & Analysis**
```
┌──────────────────────────┬──────┬──────────┬──────────┬─────────┬──────────────────────────────────────┐
│ Experiment               │ Cost │ Time     │ Evidence │ Risk    │ Description                          │
├──────────────────────────┼──────┼──────────┼──────────┼─────────┼──────────────────────────────────────┤
│ Customer Interviews      │ $    │ 1-3 days │ ★★★      │ D/F/V   │ Talk to users about jobs, pains,     │
│                          │      │          │          │         │ gains. Strong for understanding      │
│                          │      │          │          │         │ problems.                            │
├──────────────────────────┼──────┼──────────┼──────────┼─────────┼──────────────────────────────────────┤
│ Search Trend Analysis    │ $    │ 1-3 hrs  │ ★★       │ D       │ Google Trends, keyword search volume │
│                          │      │          │          │         │ to gauge interest.                   │
├──────────────────────────┼──────┼──────────┼──────────┼─────────┼──────────────────────────────────────┤
│ Customer Support         │ $    │ 1-3 days │ ★★★      │ D       │ Mine support tickets for common pain │
│ Analysis                 │      │          │          │         │ points.                              │
├──────────────────────────┼──────┼──────────┼──────────┼─────────┼──────────────────────────────────────┤
│ Discussion Forums        │ $    │ 1-3 days │ ★★       │ D       │ Reddit, forums, social media for     │
│                          │      │          │          │         │ user conversations about problems.   │
└──────────────────────────┴──────┴──────────┴──────────┴─────────┴──────────────────────────────────────┘
```

**Interest Testing**
```
┌──────────────────────────┬──────┬──────────┬──────────┬─────────┬──────────────────────────────────────┐
│ Experiment               │ Cost │ Time     │ Evidence │ Risk    │ Description                          │
├──────────────────────────┼──────┼──────────┼──────────┼─────────┼──────────────────────────────────────┤
│ Fake Door Test           │ $    │ 1-3 days │ ★★★      │ D       │ "Coming soon" link to measure clicks/│
│                          │      │          │          │         │ interest. Strong signal.             │
├──────────────────────────┼──────┼──────────┼──────────┼─────────┼──────────────────────────────────────┤
│ Feature Stub             │ $    │ 1-3 days │ ★★★      │ D       │ Link to non-existent feature to      │
│                          │      │          │          │         │ measure demand within existing       │
│                          │      │          │          │         │ product.                             │
├──────────────────────────┼──────┼──────────┼──────────┼─────────┼──────────────────────────────────────┤
│ Online Ad                │ $$   │ 1-3 days │ ★★★      │ D       │ Run targeted ads to measure click-   │
│                          │      │          │          │         │ through rates on value prop.         │
├──────────────────────────┼──────┼──────────┼──────────┼─────────┼──────────────────────────────────────┤
│ Email Campaign           │ $    │ 1-3 days │ ★★★      │ D       │ Test messaging, measure opens/clicks/│
│                          │      │          │          │         │ replies.                             │
├──────────────────────────┼──────┼──────────┼──────────┼─────────┼──────────────────────────────────────┤
│ Social Media Campaign    │ $-$$ │ 1-3 days │ ★★       │ D       │ Shares, likes, comments as interest  │
│                          │      │          │          │         │ signals.                             │
└──────────────────────────┴──────┴──────────┴──────────┴─────────┴──────────────────────────────────────┘
```

**Low-Fidelity Prototypes**
```
┌──────────────────────────┬──────┬──────────┬──────────┬─────────┬──────────────────────────────────────┐
│ Experiment               │ Cost │ Time     │ Evidence │ Risk    │ Description                          │
├──────────────────────────┼──────┼──────────┼──────────┼─────────┼──────────────────────────────────────┤
│ Paper Prototype          │ $    │ 1-3 hrs  │ ★★       │ D/F     │ Hand-drawn screens for usability     │
│                          │      │          │          │         │ testing.                             │
├──────────────────────────┼──────┼──────────┼──────────┼─────────┼──────────────────────────────────────┤
│ Storyboard               │ $    │ 1-3 hrs  │ ★★       │ D       │ Visual narrative of user journey.    │
├──────────────────────────┼──────┼──────────┼──────────┼─────────┼──────────────────────────────────────┤
│ Explainer Video          │ $$   │ 1-3 days │ ★★★      │ D       │ Demonstrate value prop, measure      │
│                          │      │          │          │         │ signup conversions.                  │
├──────────────────────────┼──────┼──────────┼──────────┼─────────┼──────────────────────────────────────┤
│ Brochure/Data Sheet      │ $    │ 1-3 hrs  │ ★★       │ D/V     │ One-pager with value prop and pricing│
│                          │      │          │          │         │ to test B2B interest.                │
└──────────────────────────┴──────┴──────────┴──────────┴─────────┴──────────────────────────────────────┘
```

**Card Sorting & Prioritization**
```
┌──────────────────────────┬──────┬──────────┬──────────┬─────────┬──────────────────────────────────────┐
│ Experiment               │ Cost │ Time     │ Evidence │ Risk    │ Description                          │
├──────────────────────────┼──────┼──────────┼──────────┼─────────┼──────────────────────────────────────┤
│ Card Sorting             │ $    │ 1-3 hrs  │ ★★       │ D       │ Test information architecture with   │
│                          │      │          │          │         │ users.                               │
├──────────────────────────┼──────┼──────────┼──────────┼─────────┼──────────────────────────────────────┤
│ Buy a Feature            │ $    │ 1-3 hrs  │ ★★★      │ D/V     │ Give users budget to "buy" features, │
│                          │      │          │          │         │ reveals priorities.                  │
└──────────────────────────┴──────┴──────────┴──────────┴─────────┴──────────────────────────────────────┘
```

#### VALIDATION EXPERIMENTS (Higher Cost/Time, Strong Evidence)

**Interactive Prototypes**
```
┌──────────────────────────┬──────┬───────────┬──────────┬─────────┬──────────────────────────────────────┐
│ Experiment               │ Cost │ Time      │ Evidence │ Risk    │ Description                          │
├──────────────────────────┼──────┼───────────┼──────────┼─────────┼──────────────────────────────────────┤
│ Clickable Prototype      │ $$   │ 1-3 weeks │ ★★★★     │ D/F     │ High-fidelity interactive mockup.    │
│                          │      │           │          │         │ Strong usability evidence.           │
├──────────────────────────┼──────┼───────────┼──────────┼─────────┼──────────────────────────────────────┤
│ Life-Sized Prototype     │ $$$  │ 1-3 weeks │ ★★★★     │ D/F     │ Physical prototype at full scale for │
│                          │      │           │          │         │ hardware/physical products.          │
├──────────────────────────┼──────┼───────────┼──────────┼─────────┼──────────────────────────────────────┤
│ 3D Print                 │ $$   │ 1-3 days  │ ★★★      │ D/F     │ Physical prototype for hardware      │
│                          │      │           │          │         │ validation.                          │
└──────────────────────────┴──────┴───────────┴──────────┴─────────┴──────────────────────────────────────┘
```

**Call-to-Action Tests**
```
┌──────────────────────────┬──────┬───────────┬──────────┬─────────┬──────────────────────────────────────┐
│ Experiment               │ Cost │ Time      │ Evidence │ Risk    │ Description                          │
├──────────────────────────┼──────┼───────────┼──────────┼─────────┼──────────────────────────────────────┤
│ Simple Landing Page      │ $    │ 1-3 hrs   │ ★★★      │ D/V     │ One-page site with signup to measure │
│                          │      │           │          │         │ conversion rates.                    │
├──────────────────────────┼──────┼───────────┼──────────┼─────────┼──────────────────────────────────────┤
│ Presale                  │ $$   │ 1-3 weeks │ ★★★★★    │ D/V     │ Accept actual orders before building.│
│                          │      │           │          │         │ Payment = very strong evidence.      │
├──────────────────────────┼──────┼───────────┼──────────┼─────────┼──────────────────────────────────────┤
│ Mock Sale                │ $$   │ 1-3 days  │ ★★★★     │ D/V     │ Present sale, collect emails instead │
│                          │      │           │          │         │ of payment. Strong price testing.    │
├──────────────────────────┼──────┼───────────┼──────────┼─────────┼──────────────────────────────────────┤
│ Crowdfunding             │ $$   │ 1-3 mos   │ ★★★★★    │ D/V     │ Kickstarter/Indiegogo campaign.      │
│                          │      │           │          │         │ Actual payments = strongest evidence.│
├──────────────────────────┼──────┼───────────┼──────────┼─────────┼──────────────────────────────────────┤
│ Split Test (A/B Test)    │ $$   │ 1-3 weeks │ ★★★★     │ D/V     │ Compare two versions to optimize     │
│                          │      │           │          │         │ conversion.                          │
├──────────────────────────┼──────┼───────────┼──────────┼─────────┼──────────────────────────────────────┤
│ Validation Survey        │ $    │ 1-3 days  │ ★★★      │ D/V     │ Structured survey after discovery    │
│                          │      │           │          │         │ phase to confirm insights at scale.  │
└──────────────────────────┴──────┴───────────┴──────────┴─────────┴──────────────────────────────────────┘
```

**Minimal Products (MVPs)**
```
┌──────────────────────────┬──────┬───────────┬──────────┬─────────┬──────────────────────────────────────┐
│ Experiment               │ Cost │ Time      │ Evidence │ Risk    │ Description                          │
├──────────────────────────┼──────┼───────────┼──────────┼─────────┼──────────────────────────────────────┤
│ Concierge                │ $$   │ 1-3 weeks │ ★★★★★    │ D/F/V   │ Deliver value manually (human-       │
│                          │      │           │          │         │ powered). Customer knows it's manual.│
│                          │      │           │          │         │ Very strong.                         │
├──────────────────────────┼──────┼───────────┼──────────┼─────────┼──────────────────────────────────────┤
│ Wizard of Oz             │ $$$  │ 1-3 weeks │ ★★★★★    │ D/F/V   │ Deliver value manually, but customer │
│                          │      │           │          │         │ thinks it's automated. Very strong.  │
├──────────────────────────┼──────┼───────────┼──────────┼─────────┼──────────────────────────────────────┤
│ Single Feature MVP       │ $$$  │ 1-3 mos   │ ★★★★★    │ D/F/V   │ Build one core feature only. Real    │
│                          │      │           │          │         │ product in production.               │
├──────────────────────────┼──────┼───────────┼──────────┼─────────┼──────────────────────────────────────┤
│ Mash-Up (Piecemeal)      │ $$   │ 1-3 weeks │ ★★★★     │ D/F/V   │ Combine existing tools/services      │
│                          │      │           │          │         │ (Zapier, APIs) to simulate product.  │
└──────────────────────────┴──────┴───────────┴──────────┴─────────┴──────────────────────────────────────┘
```

**B2B Specific**
```
┌──────────────────────────┬──────┬───────────┬──────────┬─────────┬──────────────────────────────────────┐
│ Experiment               │ Cost │ Time      │ Evidence │ Risk    │ Description                          │
├──────────────────────────┼──────┼───────────┼──────────┼─────────┼──────────────────────────────────────┤
│ Letter of Intent         │ $    │ 1-3 weeks │ ★★★★★    │ D/V     │ Formal commitment from customer to   │
│                          │      │           │          │         │ purchase. Very strong (but not as    │
│                          │      │           │          │         │ strong as payment).                  │
├──────────────────────────┼──────┼───────────┼──────────┼─────────┼──────────────────────────────────────┤
│ Pop-Up Store             │ $$$  │ 1-3 weeks │ ★★★★     │ D/V     │ Temporary physical presence to test  │
│                          │      │           │          │         │ retail/B2C concept.                  │
└──────────────────────────┴──────┴───────────┴──────────┴─────────┴──────────────────────────────────────┘
```

**Technical**
```
┌──────────────────────────┬──────┬───────────┬──────────┬─────────┬──────────────────────────────────────┐
│ Experiment               │ Cost │ Time      │ Evidence │ Risk    │ Description                          │
├──────────────────────────┼──────┼───────────┼──────────┼─────────┼──────────────────────────────────────┤
│ Extreme Programming      │ $$   │ 1-3 days  │ ★★★★     │ F       │ Time-boxed technical investigation   │
│ Spike                    │      │           │          │         │ to prove feasibility.                │
└──────────────────────────┴──────┴───────────┴──────────┴─────────┴──────────────────────────────────────┘
```

#### EXPERIMENT SEQUENCES (Chaining Tests Together)

**B2B Software Example:**
Customer Interviews → Customer Support Analysis → Feature Stub → Single Feature MVP

**B2C Software Example:**
Search Trends → Online Ad → Simple Landing Page → Wizard of Oz → Single Feature MVP

**B2B Services Example:**
Stakeholder Interviews → Brochure → Presale → Concierge (manual delivery)

**Hardware Example:**
Paper Prototype → 3D Print → Crowdfunding → Pop-Up Store

### 6. Map the Critical Path for MVP
Follow the progression to ensure the product remains valuable and lovable:

```
    MVP PROGRESSION PATH
    
    1. Earliest Showable
       └─► Rough concept, napkin sketch
           Get initial feedback
    
    2. Earliest Testable
       └─► Functional enough for testing
           Run usability tests
    
    3. Earliest Usable
       └─► Solves core user problem
           User can accomplish job
    
    4. Earliest Likable
       └─► Positive user experience
           Users want to use it
    
    5. Earliest Lovable (MVP)
       └─► Valuable enough to sell
           Ready for early adopters
```

# **Final Instructions**
1. **Start with Desirability Risk:** Test market demand before feasibility or viability.
2. **Focus on Top Right Quadrant:** Test important hypotheses where you lack evidence.
3. **Go Fast and Cheap First:** Use discovery experiments early, validation experiments later.
4. **Multiple Experiments per Hypothesis:** Don't make big decisions on one test.
5. **Evidence Before Building:** The higher the build cost, the more testing needed first.
6. **Prioritize Value:** Always aim for "Minimum Valuable Product" that solves real pain.
7. **Differentiate PoC vs. MVP:** PoC proves it _can_ be built; MVP proves it _should_ be built.
