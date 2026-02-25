# Product Requirements Document: DoorDash Nutrition Tracking

**Product:** Nutrition Tracking & Dietary Filters  
**Version:** 1.0  
**Status:** Approved for Development  
**Owner:** Product Management  
**Last Updated:** February 2025

---

## Table of Contents
1. [Overview](#overview)
2. [Goals & Success Metrics](#goals--success-metrics)
3. [User Stories](#user-stories)
4. [Functional Requirements](#functional-requirements)
5. [Technical Requirements](#technical-requirements)
6. [Design Requirements](#design-requirements)
7. [Out of Scope](#out-of-scope)
8. [Dependencies](#dependencies)
9. [Launch Plan](#launch-plan)

---

## Overview

### Problem Statement
Health-conscious users lack nutritional transparency when ordering from DoorDash, leading to cart abandonment and platform churn. 68% of surveyed users want macro information before ordering, and 54% would increase order frequency if nutrition tracking were available in-app.

### Solution Summary
Introduce a comprehensive nutrition tracking system that displays per-item macros, provides real-time cart summaries, enables dietary filtering, and allows users to set and track macro goals. The feature will be progressively disclosed to avoid overwhelming casual users while providing depth for committed health trackers.

### Success Metrics
- **Primary:** +13% order frequency among health-conscious user segment
- **Guardrails:** Cart abandonment rate ≤32% (no increase), session time on menu +<15%
- **Adoption:** 35% of active users interact with nutrition features within 90 days

---

## Goals & Success Metrics

### Business Goals
1. Reduce churn among high-LTV health-conscious users by 8%
2. Increase monthly order frequency from 2.3x to 2.6x for target segment
3. Generate $12M incremental GMV in first 12 months

### User Goals
1. Make informed ordering decisions aligned with health/fitness goals
2. Quickly filter restaurants and menu items by dietary preferences
3. Track nutritional intake across multiple orders without manual entry

### Success Metrics

| Metric | Baseline | Target | Measurement |
|--------|----------|--------|-------------|
| Order frequency (health segment) | 2.3x/month | 2.6x/month | Cohort analysis |
| Cart abandonment rate | 32% | ≤32% | Session analytics |
| Dietary filter adoption | N/A | 25% | Feature usage logs |
| Macro goal setup rate | N/A | 15% | User settings data |
| Session time on menu page | Avg 2:15 | <2:35 | Analytics |
| NPS (health segment) | 42 | 50 | Quarterly survey |

---

## User Stories

### Epic 1: Nutrition Visibility

**US-1.1:** As a health-conscious user, I want to see calorie and macro information for each menu item so I can make informed ordering decisions.

**US-1.2:** As a user customizing my order, I want to see updated nutrition info when I modify ingredients so I know the impact of my changes.

**US-1.3:** As a user with dietary restrictions, I want to see allergen warnings and dietary labels (vegan, gluten-free) so I can safely order.

### Epic 2: Cart & Order Tracking

**US-2.1:** As a macro-tracking user, I want to see real-time nutrition totals for my cart so I know my meal's full nutritional impact before checkout.

**US-2.2:** As a user who's set macro goals, I want to see progress bars comparing my cart to my daily targets so I can stay on track.

**US-2.3:** As a user reviewing past orders, I want to see historical nutrition data so I can track my intake over time.

### Epic 3: Discovery & Filtering

**US-3.1:** As a keto dieter, I want to filter menu items by low-carb criteria so I can quickly find suitable options.

**US-3.2:** As a high-protein eater, I want to see which restaurants have the most protein-rich options so I can choose efficiently.

**US-3.3:** As a vegetarian user, I want to filter restaurants and items by vegan/vegetarian tags so I don't waste time browsing incompatible menus.

### Epic 4: Goal Setting & Personalization

**US-4.1:** As a new user interested in nutrition tracking, I want an onboarding flow to set my macro goals so the app can personalize my experience.

**US-4.2:** As a user with changing fitness goals, I want to easily update my macro targets so the app reflects my current needs.

**US-4.3:** As a casual user, I want to skip goal-setting and still see basic nutrition info so I'm not forced into a workflow I don't need.

---

## Functional Requirements

### FR-1: Per-Item Nutrition Display

**FR-1.1:** Display nutrition information on menu item cards
- Show: Calories (prominent), Protein, Carbs, Fat
- Format: "420 cal | 32g protein | 24g carbs | 18g fat"
- Location: Below item description, above price
- Visual: Subtle gray text, not overwhelming

**FR-1.2:** Indicate data source with icon
- Restaurant-verified: Green checkmark icon
- Estimated (USDA database): Gray "~" icon
- Tap icon to see data source details

**FR-1.3:** Update nutrition dynamically with customizations
- Recalculate macros when user adds/removes ingredients
- Show delta: "No cheese: -110 cal, -7g fat"
- Real-time updates (no page refresh)

**FR-1.4:** Handle missing nutrition data gracefully
- Show "Nutrition info unavailable" with feedback link
- Don't hide items or penalize restaurants
- Track unavailability rate for data partnerships

### FR-2: Cart Nutrition Summary

**FR-2.1:** Display persistent cart summary bar
- Position: Below cart items, above checkout button
- Content: Total calories, protein, carbs, fat
- Expandable to show per-item breakdown
- Collapsible to minimize (default state)

**FR-2.2:** Show progress toward macro goals (if set)
- Visual progress bars for each macro
- Color-coded: Green (under target), Yellow (near target), Red (over target)
- Percentage and absolute values: "45g / 150g protein (30%)"

**FR-2.3:** Update in real-time as cart changes
- Add/remove items updates instantly
- Animations: Smooth count-up/down (not jarring)
- No loading states (pre-calculated)

### FR-3: Dietary Filters

**FR-3.1:** Add dietary filter chips to restaurant list view
- Filters: High-Protein (>30g), Low-Carb (<20g), Keto (<10g net carbs), Vegan, Vegetarian, Gluten-Free
- Multi-select enabled
- Pill-style UI, toggleable on/tap
- Clear all button when filters active

**FR-3.2:** Filter menu items within restaurant view
- Same filter options as restaurant list
- Applied client-side for speed
- Show match count: "8 high-protein items"

**FR-3.3:** Smart restaurant badging
- Badge restaurants with strong category matches
- Example: "12+ high-protein options" badge
- Only show if ≥10 items match filter

**FR-3.4:** Persist filter preferences
- Remember last-used filters per session
- Offer "Save as default" option in settings
- Don't auto-apply saved filters (respect browsing mode)

### FR-4: Macro Goals Onboarding

**FR-4.1:** Trigger onboarding on first app open after feature launch
- Optional dismissible flow (not blocking)
- 3-screen carousel: Feature intro, Goal setup, Success confirmation
- Skip button on every screen

**FR-4.2:** Goal setup interface
- Input fields: Calories, Protein, Carbs, Fat
- Pre-filled templates: Cutting, Bulking, Maintenance, Custom
- Helper text: "Based on 180lb person, moderate activity"
- Validation: Reasonable ranges (1200-4500 cal, macros sum correctly)

**FR-4.3:** Enable access from settings anytime
- Path: Settings > Nutrition & Health > Macro Goals
- Edit/delete goals
- Toggle goals on/off without deleting

### FR-5: Data Quality & Attribution

**FR-5.1:** Nutrition data sourcing priority
1. Restaurant-provided API data (highest quality)
2. Restaurant-provided PDF menus (manual entry)
3. USDA FoodData Central database (estimates)
4. ML model predictions (lowest quality, flagged clearly)

**FR-5.2:** User feedback on accuracy
- "Report incorrect nutrition" link on each item
- Form: Expected vs. Actual macros, optional notes
- Triggers manual review if >5 reports on same item

**FR-5.3:** Conservative rounding rules
- Round up calories to nearest 10
- Round macros to nearest gram
- Never show false precision (no decimals)

---

## Technical Requirements

### TR-1: Backend Infrastructure

**TR-1.1:** Nutrition database schema
- Table: `nutrition_data`
  - Fields: `item_id`, `calories`, `protein_g`, `carbs_g`, `fat_g`, `source_type`, `verified`, `last_updated`
- Indexes: `item_id`, `source_type`, `verified`
- Partitioned by restaurant for query performance

**TR-1.2:** API endpoints
- `GET /menu/items/:id/nutrition` - Fetch nutrition for single item
- `GET /menu/items/nutrition` - Batch fetch (up to 100 items)
- `POST /cart/nutrition` - Calculate cart totals (accepts item IDs + customizations)
- `POST /user/macro-goals` - Save user goals
- `GET /user/macro-goals` - Retrieve user goals

**TR-1.3:** Caching strategy
- Cache nutrition data at CDN edge (24hr TTL)
- In-app cache for viewed items (session lifetime)
- Invalidate on menu updates (webhook from restaurant partners)

**TR-1.4:** Performance SLAs
- P95 latency for nutrition fetch: <100ms
- Cart calculation: <50ms
- Filter application: <200ms (client-side)

### TR-2: Data Pipelines

**TR-2.1:** Restaurant data ingestion
- Daily automated imports from restaurant partners (SFTP)
- Schema validation before ingestion
- Automated email alerts on failed imports

**TR-2.2:** USDA data sync
- Weekly pull from FoodData Central API
- Fuzzy matching to menu items (Levenshtein distance)
- Manual review queue for low-confidence matches (<70%)

**TR-2.3:** ML prediction model
- Train on existing verified data
- Features: Item name, description, category, price, ingredients
- Model type: Gradient boosted trees (XGBoost)
- Retraining cadence: Monthly
- Accuracy threshold: 85% on test set

### TR-3: Privacy & Security

**TR-3.1:** User data handling
- Macro goals stored encrypted at rest
- No sharing of nutrition data with third parties
- Option to delete all nutrition history: Settings > Privacy > Clear Nutrition Data

**TR-3.2:** Compliance
- GDPR: Right to erasure (nutrition data included)
- CCPA: Opt-out of analytics tracking for nutrition features
- HIPAA: Not applicable (we're not making medical claims)

---

## Design Requirements

### DR-1: Visual Design Principles

**DR-1.1:** Progressive disclosure
- Default view: Calories only
- Tap to expand: Full macros
- Settings toggle: Always show full macros

**DR-1.2:** Minimize cognitive load
- Use familiar visual language (progress bars, icons)
- Limit color palette: Green (good), Yellow (caution), Red (over)
- No aggressive warnings or shame language

**DR-1.3:** Accessibility
- AA contrast ratios minimum
- Screen reader labels for all nutrition data
- VoiceOver-friendly progress bars

### DR-2: Information Architecture

**DR-2.1:** Entry points to nutrition features
1. Menu item cards (always visible)
2. Cart summary (appears when cart has items)
3. Settings > Nutrition & Health
4. Search results (dietary badges)

**DR-2.2:** Settings hierarchy
```
Settings
└── Nutrition & Health
    ├── Macro Goals (set/edit/delete)
    ├── Default Dietary Filters
    ├── Nutrition Display Preferences
    │   ├── Show on menu items (toggle)
    │   ├── Always expand macros (toggle)
    │   └── Data source icons (toggle)
    └── Privacy
        └── Clear Nutrition History
```

### DR-3: Edge Cases & Error States

**DR-3.1:** Missing nutrition data
- Show: "Nutrition info unavailable" with lightbulb icon
- Action: "Request from restaurant" link (submits to restaurant BD team)

**DR-3.2:** Customization without updated nutrition
- Show: "Custom nutrition unavailable"
- Explanation: "Base item: 420 cal. Custom macros may vary."

**DR-3.3:** Failed API calls
- Graceful degradation: Show last-known values with "May be outdated" warning
- Retry logic: 3 attempts with exponential backoff
- Fallback: Hide nutrition section if repeatedly failing

---

## Out of Scope

The following are explicitly NOT included in V1:

- **Integration with third-party apps** (MyFitnessPal, Apple Health) - Planned for V2
- **Meal planning/calendar features** - Future consideration
- **Nutritionist chat/advice** - Potential premium tier feature
- **Micronutrients** (vitamins, minerals) - Data availability too low
- **Restaurant nutrition scorecards** - Risk of alienating partners
- **Social features** (sharing meals, comparing with friends) - Out of mission
- **Grocery delivery nutrition** - Separate product team owns

---

## Dependencies

### Internal Teams

| Team | Dependency | Timeline |
|------|------------|----------|
| **Engineering (Backend)** | API development, database schema | 6 weeks |
| **Engineering (Mobile)** | iOS/Android UI implementation | 8 weeks |
| **Design** | Visual design, prototype | 3 weeks |
| **Data Science** | ML prediction model | 5 weeks |
| **Restaurant BD** | Partner outreach, data collection | Ongoing |
| **Legal** | Disclaimer copy, liability review | 2 weeks |
| **Marketing** | Launch messaging, ASO | 4 weeks |

### External Dependencies

| Dependency | Risk Level | Mitigation |
|------------|------------|------------|
| Restaurant data provision | High | Start with top 1,000 restaurants, expand gradually |
| USDA API uptime | Low | Cache data locally, weekly sync acceptable |
| App store approval | Medium | Pre-submission review with Apple/Google reps |

---

## Launch Plan

### Phase 1: Internal Beta (Week 1-2)
- Employee dogfooding
- Bug bash sessions
- Performance testing under load

### Phase 2: Closed Beta (Week 3-5)
- 5,000 opted-in power users
- Feedback surveys after 2 weeks
- Iterate on UX pain points

### Phase 3: Gradual Rollout (Week 6-10)
- 10% of users (random sample)
- Monitor cart abandonment, session time, crashes
- Expand to 50%, then 100% if metrics healthy

### Phase 4: Full Launch (Week 11)
- 100% rollout
- App Store featuring push
- PR and social media campaign

### Rollback Criteria
- Cart abandonment increases >5%
- Crash rate >0.1%
- P0 bugs affecting checkout

---

## Risks & Mitigations

| Risk | Likelihood | Impact | Mitigation |
|------|------------|--------|------------|
| Data accuracy complaints | Medium | High | Clear attribution, conservative rounding, feedback loop |
| Restaurant partner resistance | High | Medium | Optional participation, highlight marketing value |
| UI clutter backlash | Low | Medium | A/B test every element, offer "simple mode" |
| Performance degradation | Low | High | Aggressive caching, load testing, gradual rollout |
| Legal liability (dietary claims) | Low | High | Legal-reviewed disclaimers, no medical language |

---

## Appendix A: Mockups

See `assets/wireframes/` for detailed UI mockups.

### Key Screens
1. Menu item card with nutrition display
2. Expanded macro breakdown modal
3. Cart nutrition summary (collapsed/expanded)
4. Dietary filter chips on restaurant list
5. Macro goals onboarding flow
6. Settings > Nutrition & Health

---

## Appendix B: Data Schema

```sql
-- Nutrition data table
CREATE TABLE nutrition_data (
  id BIGSERIAL PRIMARY KEY,
  item_id BIGINT NOT NULL REFERENCES menu_items(id),
  calories INT NOT NULL,
  protein_g DECIMAL(5,1) NOT NULL,
  carbs_g DECIMAL(5,1) NOT NULL,
  fat_g DECIMAL(5,1) NOT NULL,
  fiber_g DECIMAL(5,1),
  sugar_g DECIMAL(5,1),
  sodium_mg INT,
  source_type VARCHAR(20) NOT NULL, -- 'restaurant', 'usda', 'ml_predicted'
  verified BOOLEAN DEFAULT FALSE,
  confidence_score DECIMAL(3,2), -- for ML predictions
  last_updated TIMESTAMP DEFAULT NOW(),
  INDEX idx_item_id (item_id),
  INDEX idx_verified (verified)
);

-- User macro goals table
CREATE TABLE user_macro_goals (
  user_id BIGINT PRIMARY KEY REFERENCES users(id),
  calories_target INT NOT NULL,
  protein_target_g DECIMAL(5,1) NOT NULL,
  carbs_target_g DECIMAL(5,1) NOT NULL,
  fat_target_g DECIMAL(5,1) NOT NULL,
  created_at TIMESTAMP DEFAULT NOW(),
  updated_at TIMESTAMP DEFAULT NOW()
);

-- Nutrition feedback table
CREATE TABLE nutrition_feedback (
  id BIGSERIAL PRIMARY KEY,
  item_id BIGINT NOT NULL REFERENCES menu_items(id),
  user_id BIGINT REFERENCES users(id),
  reported_calories INT,
  reported_protein_g DECIMAL(5,1),
  reported_carbs_g DECIMAL(5,1),
  reported_fat_g DECIMAL(5,1),
  notes TEXT,
  status VARCHAR(20) DEFAULT 'pending', -- 'pending', 'reviewed', 'resolved'
  created_at TIMESTAMP DEFAULT NOW()
);
```

---

## Appendix C: API Examples

### Get Nutrition for Menu Item
```http
GET /api/v1/menu/items/12345/nutrition
Authorization: Bearer {token}

Response 200:
{
  "item_id": 12345,
  "nutrition": {
    "calories": 520,
    "protein_g": 34.0,
    "carbs_g": 42.0,
    "fat_g": 18.0,
    "fiber_g": 6.0
  },
  "source": "restaurant",
  "verified": true,
  "last_updated": "2025-02-20T14:30:00Z"
}
```

### Calculate Cart Nutrition
```http
POST /api/v1/cart/nutrition
Authorization: Bearer {token}
Content-Type: application/json

{
  "items": [
    {
      "item_id": 12345,
      "quantity": 1,
      "customizations": ["no_cheese", "extra_veggies"]
    },
    {
      "item_id": 67890,
      "quantity": 2
    }
  ]
}

Response 200:
{
  "totals": {
    "calories": 1240,
    "protein_g": 86.0,
    "carbs_g": 102.0,
    "fat_g": 44.0
  },
  "items": [
    {
      "item_id": 12345,
      "nutrition": { ... },
      "customization_deltas": {
        "no_cheese": { "calories": -110, "fat_g": -9.0 }
      }
    },
    { ... }
  ]
}
```

---

**Document Status:** Ready for Engineering Kickoff  
**Approval:** Product Leadership ✓ | Engineering Leadership ✓ | Design ✓  
**Next Review:** Post-Beta (Week 5)
