# DoorDash Nutrition Tracking Feature - Case Study

## Executive Summary

This case study documents the end-to-end product development of a nutrition tracking feature for DoorDash, aimed at retaining and growing the health-conscious user segment. The feature suite includes per-item macro displays, real-time cart nutrition summaries, dietary filters, and an onboarding flow for macro goals.

---

## 🔍 Problem Statement

**Business Problem:**  
Health-conscious users were abandoning DoorDash for meal kit services like Factor or returning to home cooking due to lack of nutritional transparency. This segment represents high lifetime value (LTV) users with above-average order frequency and basket sizes.

**User Problem:**  
Users committed to fitness goals or dietary plans couldn't make informed ordering decisions. Without nutritional information, they either:
- Abandoned carts mid-session
- Ordered conservatively (smaller baskets)
- Switched to competitors with better nutritional visibility
- Stopped using food delivery altogether

---

## 💡 Key Insight

Research with 40 users revealed strong demand for nutritional transparency:

| Finding | Impact |
|---------|--------|
| **68%** wanted calorie/macro info before ordering | Massive unmet need for nutrition data |
| **54%** said they'd order more frequently with in-app tracking | Direct revenue opportunity |
| **42%** had abandoned DoorDash orders specifically due to nutrition uncertainty | Quantifiable churn driver |
| **31%** switched to Factor or similar services in past 6 months | Competitive threat |

**Core insight:** Users weren't asking for healthier food options—they wanted transparency to make their own informed choices within existing restaurant offerings.

---

## 🛠️ Solution Overview

### Feature Set

1. **Per-Item Macro Display**
   - Calories, protein, carbs, fat visible on all menu items
   - Customization-aware calculations (e.g., "no cheese" updates macros)
   - Clearly attributed source (restaurant-provided or estimated)

2. **Real-Time Cart Nutrition Summary**
   - Live-updating macro totals as items are added
   - Visual progress bars comparing to user goals (if set)
   - Expandable item-by-item breakdown

3. **Dietary Filters**
   - Pre-built filters: High-protein, Low-carb, Keto-friendly, Vegan, Vegetarian
   - Multi-select capability
   - Smart restaurant badging (e.g., "8 high-protein options")

4. **Macro Goals Onboarding**
   - Optional first-time setup flow
   - Pre-filled templates (cutting, bulking, maintenance)
   - Skippable with easy access in settings

---

## 📊 Success Metrics & Guardrails

### North Star Metric
**Order frequency among health-conscious users** (+15% target)

### Primary Success Metrics

| Metric | Baseline | Target | Why It Matters |
|--------|----------|--------|----------------|
| Order frequency (health segment) | 2.3x/month | 2.6x/month | Primary signal that nutrition visibility drives repeat usage |
| Cart abandonment rate | 32% | ≤32% | Guardrail—ensures feature doesn't add friction |
| Dietary filter adoption | N/A | 25% | Feature discoverability and relevance indicator |

### Guardrail Metrics

- **Session time on menu page:** Should increase <15% (guards against analysis paralysis)
- **App ratings/sentiment:** Monitor for complaints about clutter or overwhelm
- **Restaurant partner satisfaction:** Track any concerns about nutrition accuracy

---

## 🎯 Target Audience

**Primary:** Health-conscious frequent orderers
- Age 25-45
- Order 4+ times per month
- Higher basket values ($30+ average)
- Use fitness/nutrition apps (MyFitnessPal, Lose It)

**Secondary:** Dietary-restricted users
- Medical restrictions (diabetes, heart disease)
- Lifestyle choices (keto, vegan, halal)

---

## 📈 Expected Business Impact

### Revenue Impact
- **Retention:** 8% reduction in churn among health segment (∼$4.2M ARR saved)
- **Frequency:** 13% increase in monthly orders from segment ($6.8M incremental GMV)
- **Acquisition:** 5% lift in health-conscious user signups via App Store featuring

### Strategic Benefits
- Competitive differentiation vs. Uber Eats and Grubhub
- Foundation for premium "DoorDash Health" subscription tier
- Data asset for restaurant partners (menu optimization insights)

---

## 📁 Related Documents

- **[Vision & Strategy](vision-strategy.md)** - Long-term product vision and strategic rationale
- **[Product Requirements Document](prd.md)** - Detailed technical and functional specifications
- **[Business Case](business-case.md)** - Financial model and ROI analysis
- **[Go-to-Market Strategy](gtm-strategy.md)** - Launch plan and rollout approach
- **[Roadmap](roadmap.md)** - Multi-quarter feature evolution plan
- **[Prototype](prototype/index.html)** - Interactive mockup of key user flows

---

## 🏆 Key Learnings

### What Worked
- **Transparency over prescription:** Users didn't want DoorDash to tell them what to eat—they wanted data to make their own choices
- **Guardrail metrics upfront:** Defining "bad" outcomes (analysis paralysis, increased friction) prevented scope creep toward overly complex UI

### What We'd Do Differently
- Start with restaurant partnerships earlier to improve nutrition data accuracy
- Test dietary filter taxonomy more rigorously (users confused "keto-friendly" vs. "low-carb")
- Build macro goals onboarding as A/B test from day one (initially delayed launch)

---

## Contact

For questions about this case study or to discuss the product development process, please reach out.

---

*This is a portfolio case study demonstrating product management skills in user research, prioritization, cross-functional collaboration, and data-driven decision making.*
