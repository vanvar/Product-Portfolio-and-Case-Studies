# Vision & Strategy: DoorDash Nutrition Tracking

## Product Vision

**Empower every DoorDash user to align their food delivery choices with their health goals—without sacrificing convenience or variety.**

In three years, DoorDash should be the default platform for health-conscious eaters who want restaurant-quality meals that fit their nutritional needs. Success means a user can seamlessly order for a cutting phase, family dinner with dietary restrictions, or post-workout meal—all with full nutritional transparency.

---

## Strategic Context

### Market Opportunity

The health and wellness food market is projected to reach $1 trillion globally by 2027. Within food delivery:
- 41% of consumers say healthy eating is a top priority (Mintel, 2024)
- Meal kit services (Factor, Trifecta) growing 28% YoY by emphasizing nutrition
- Fitness app integrations (MyFitnessPal, LoseIt) show high engagement with food tracking

**DoorDash's position:** Strong restaurant selection and logistics, but lagging competitors in health/wellness features.

### Competitive Landscape

| Platform | Nutrition Features | Strength | Weakness |
|----------|-------------------|----------|----------|
| **Factor/Trifecta** | Full macro breakdowns, curated menus | Nutrition-first positioning | Limited variety, higher prices |
| **Uber Eats** | Basic calorie counts (select restaurants) | Scale and brand | Inconsistent data, no filtering |
| **Grubhub** | None | Partnership relationships | No differentiation on health |
| **DoorDash (current)** | None | Restaurant selection, delivery speed | Losing health-conscious segment |

**Gap:** No major delivery platform offers comprehensive, user-friendly nutrition tools. First-mover advantage available.

---

## Strategic Pillars

### 1. **Transparency Over Prescription**
We provide nutritional data; users make their own choices. No "guilt-tripping" or limiting options—just clear information.

**Why:** Research shows users resist platforms that judge their food choices. They want data, not lectures.

### 2. **Progressive Disclosure**
Nutrition info is visible but not intrusive. Users who care deeply can dive in; casual users aren't overwhelmed.

**Implementation:**
- Default view shows calories only
- Tap to expand full macros
- Filters and goals are opt-in

### 3. **Data Quality as Competitive Moat**
Accurate nutrition data is hard to get and maintain. Investing in restaurant partnerships and ML-powered estimation creates defensibility.

**Roadmap:**
- Phase 1: Restaurant-provided data + USDA estimates
- Phase 2: Computer vision for portion verification
- Phase 3: User-submitted corrections (community moderation)

---

## User Segmentation

### Primary Segment: Committed Health Trackers
- **Size:** ~8% of active users (∼2.4M users)
- **Behavior:** Order 4+ times/month, use nutrition apps, higher AOV
- **Needs:** Precise macros, customization-aware calculations, goal tracking
- **Value:** 3.2x LTV of average user

### Secondary Segment: Casual Health-Conscious
- **Size:** ~22% of active users (∼6.6M users)
- **Behavior:** Order 2-3 times/month, periodic dieting, price-sensitive
- **Needs:** Simple calorie visibility, quick filters (low-carb, vegan)
- **Value:** 1.4x LTV of average user

### Tertiary Segment: Dietary-Restricted
- **Size:** ~5% of active users (∼1.5M users)
- **Behavior:** Medical/religious restrictions, high retention once onboarded
- **Needs:** Allergen warnings, religious dietary filters (halal, kosher)
- **Value:** 2.1x LTV (sticky due to limited alternatives)

---

## Strategic Hypotheses (To Validate)

### H1: Nutrition visibility reduces churn
**Test:** Cohort analysis comparing churn rates pre/post feature access  
**Success:** ≥5% reduction in 90-day churn for health segment

### H2: Dietary filters drive incremental orders
**Test:** A/B test filter UI on/off  
**Success:** +10% order frequency in treatment group

### H3: Macro goals increase basket size
**Test:** Compare AOV for users who set goals vs. don't  
**Success:** +$4 AOV for goal-setting users

### H4: Data quality threshold matters
**Test:** Show estimated vs. verified nutrition data, measure trust/usage  
**Success:** 2x higher engagement with verified data

---

## Differentiation Strategy

### Why DoorDash Wins in Nutrition

1. **Restaurant Breadth**
   - 450,000+ restaurants vs. Factor's 50 curated meals
   - Users don't sacrifice variety for health

2. **Customization Engine**
   - Existing customization platform (add/remove ingredients)
   - Real-time macro recalculation as users modify orders
   - Competitors can't match this without similar infrastructure

3. **Logistics Speed**
   - 30-min delivery maintains convenience
   - Meal kits require planning days ahead

4. **Data Network Effects**
   - More users = more nutrition data corrections
   - Restaurant partners incentivized to provide accurate data (visibility boost)

---

## Long-Term Product Roadmap (3 Years)

### Year 1: Foundation (Current Initiative)
- ✅ Core nutrition display (calories, macros)
- ✅ Dietary filters
- ✅ Basic goal tracking

### Year 2: Intelligence & Personalization
- ML-powered meal recommendations based on goals
- Integration with Apple Health, MyFitnessPal, Strava
- "Smart Reorder" suggesting meals that fit remaining daily macros
- DoorDash Health subscription tier ($9.99/mo)
  - Verified nutrition data priority
  - Advanced meal planning
  - Nutritionist chat support

### Year 3: Ecosystem & Services
- DoorDash Kitchen partnerships for nutrition-optimized menus
- White-label nutrition tools for restaurant partners
- B2B wellness program partnerships (corporate meal benefits)
- Expansion into grocery delivery with nutrition tracking

---

## Success Criteria (12-Month Horizon)

### Business Metrics
- **Health segment retention:** 92% → 95%
- **Order frequency (health users):** 2.3x/mo → 2.6x/mo
- **Feature adoption:** 35% of active users enable nutrition display
- **Revenue impact:** $12M incremental GMV from segment

### Product Metrics
- **Dietary filter usage:** 25% of sessions
- **Macro goal setup:** 15% of health segment
- **Data accuracy:** <5% user-reported errors
- **NPS lift:** +8 points among health segment

### Strategic Metrics
- **Competitive win-backs:** 20,000 users who left for Factor/Trifecta
- **App Store featuring:** "Health & Fitness" category placement
- **Press coverage:** 3+ major tech/health publication features

---

## Risk Mitigation

### Risk 1: Restaurant Partner Resistance
**Concern:** Restaurants fear nutrition data will reduce orders  
**Mitigation:**
- Show data that transparency *increases* average order value
- Offer "nutrition verified" badge as marketing tool
- Make participation optional initially

### Risk 2: Data Accuracy Liability
**Concern:** Incorrect nutrition data leads to legal issues  
**Mitigation:**
- Clear disclaimers (estimates vs. verified)
- Conservative rounding
- Legal review of all UI copy
- Insurance policy for food data liability

### Risk 3: Feature Bloat / UI Clutter
**Concern:** Overwhelming casual users  
**Mitigation:**
- Strict adherence to progressive disclosure
- A/B test every UI element for impact on conversion
- "Simple mode" toggle to hide all nutrition UI

### Risk 4: Competitive Response
**Concern:** Uber Eats or Grubhub copies feature quickly  
**Mitigation:**
- Move fast on advanced features (personalization, integrations)
- Build data moat through restaurant partnerships
- Lock in users with macro goal history (switching cost)

---

## Alignment with DoorDash's Mission

**DoorDash Mission:** *"Empower local economies by connecting people with the things they love."*

This feature aligns by:
- **Empowering users:** Giving them data to make informed choices
- **Supporting local restaurants:** Helping health-focused eateries reach their target audience
- **Expanding "things they love":** Letting users enjoy restaurant food while meeting health goals (not forcing a choice)

---

## Appendix: Research Insights

### User Interview Quotes

> *"I literally calculate macros on my phone's calculator while looking at the menu. It takes forever and I usually just give up and order from Factor."* — Sarah, 29, fitness enthusiast

> *"I'd order DoorDash 3x more if I knew the calorie counts. Right now I only use it for cheat meals."* — Mike, 34, weight loss journey

> *"The worst is when you're being so careful all week, then you find out that 'healthy' salad was 1,200 calories because of the dressing."* — Jessica, 41, marathon training

### Survey Data (n=1,200)

- 68% want calorie/macro info before ordering
- 54% would order more frequently with nutrition tracking
- 42% have abandoned orders due to nutrition uncertainty
- 77% trust restaurant-provided data over estimates
- 31% have switched to meal kits specifically for nutrition visibility

---

*Document Version: 1.0*  
*Last Updated: February 2025*  
*Owner: Product Management*
