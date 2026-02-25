# Product Requirements Document: AI Closet Organizer

**Product:** AI Closet Organizer  
**Version:** 1.0  
**Status:** Approved for Development  
**Last Updated:** February 2025

---

## Overview

### Problem
Users own 77 garments on average but wear only 20%, leading to decision fatigue, duplicate purchases, and wardrobe guilt. Existing closet apps require 2-3 hours of manual cataloging, causing 73% drop-off during onboarding.

### Solution
Mobile app with AI-powered photo cataloging (10-minute setup for 50 items) and context-aware daily outfit suggestions based on weather, calendar, and mood.

### Success Criteria
- Onboarding completion: 65% (vs. 27% competitor benchmark)
- Daily outfit engagement: 40%
- Wardrobe utilization: 40% (vs. 20% industry average)

---

## User Stories

### Epic 1: Effortless Cataloging

**US-1.1:** As a new user, I want to photograph multiple clothing items at once so I can catalog my closet in minutes, not hours.

**US-1.2:** As a user, I want AI to automatically tag my items (category, color, fabric) so I don't have to manually input details for every garment.

**US-1.3:** As a user, I want to easily correct AI mistakes with one tap so I feel in control of my wardrobe data.

### Epic 2: Smart Outfit Suggestions

**US-2.1:** As a daily user, I want to see 3-5 outfit suggestions each morning so I can quickly choose what to wear without decision fatigue.

**US-2.2:** As a user with calendar events, I want outfit suggestions appropriate for my schedule (meetings, dates, gym) so I'm always dressed right for the occasion.

**US-2.3:** As a user checking weather, I want outfits adapted to temperature and precipitation so I'm comfortable all day.

### Epic 3: Wardrobe Insights

**US-3.1:** As a user, I want to see which items I rarely wear so I can either style them differently or declutter.

**US-3.2:** As a user, I want to track what I've worn recently so I avoid outfit repetition when seeing the same people.

**US-3.3:** As a user, I want to save successful outfit combinations so I can recreate them easily.

---

## Functional Requirements

### FR-1: AI Photo Cataloging

**FR-1.1: Bulk Photo Upload**
- User can take multiple photos in one session (batch mode)
- App detects individual garments in each photo (up to 5 per image)
- Background removal isolates each item

**FR-1.2: Automatic Tagging**
- AI assigns:
  - **Category:** Top, Bottom, Dress, Outerwear, Shoes, Accessory
  - **Color:** Primary + secondary colors (18 standard options)
  - **Fabric:** Cotton, Denim, Silk, Wool, Polyester, Leather, etc.
  - **Occasion:** Casual, Work, Formal, Athletic
  - **Pattern:** Solid, Striped, Floral, Graphic, etc.
  - **Season:** Spring/Summer, Fall/Winter, Year-round
- Confidence threshold: Display tag only if >70% confident

**FR-1.3: One-Tap Corrections**
- User taps any auto-tag to see alternative options
- Corrections feed back into ML model (continuous improvement)
- Show "improving AI accuracy" message after corrections

**FR-1.4: Progress Tracking**
- Display item count: "15 items cataloged — keep going!"
- Celebrate milestones: "🎉 50 items! Your closet is taking shape."
- Show preview outfit after 10+ items

### FR-2: Daily Outfit Suggestions

**FR-2.1: Weather Integration**
- Pull from OpenWeather API (user's location)
- Display: Temp, "feels like," precipitation, wind
- Suggest appropriate layers, fabrics, footwear

**FR-2.2: Calendar Integration** (Premium)
- Request calendar permission (optional)
- Parse event titles for keywords: "interview," "date," "gym," "wedding"
- Suggest event-appropriate attire

**FR-2.3: Mood-Based Filtering**
- User sets daily mood: Comfy, Bold, Professional, Casual, Creative
- AI weights outfit suggestions toward mood aesthetic

**FR-2.4: Smart Combinations**
- Algorithm ensures:
  - Color harmony (no clashing)
  - Occasion appropriateness
  - Recently worn items deprioritized
  - User's saved favorites surface more often
- Display 3-5 complete outfits (top + bottom + shoes + optional accessories)

### FR-3: Outfit Tracking

**FR-3.1: "Worn Today" Tap**
- One-tap mark item as worn (updates last-worn date)
- Option to mark entire outfit at once
- Stores wear history for analytics

**FR-3.2: Save Outfits**
- Tap heart icon to save combination
- Name outfit (optional): "Monday meeting," "Date night"
- Access saved outfits from separate tab

**FR-3.3: Outfit History**
- Calendar view of past outfits
- Filter by date, event, season
- Prevent repeats: "You wore this 3 days ago"

### FR-4: Wardrobe Insights

**FR-4.1: Underused Items**
- "Hidden Gems" section shows items unworn 30+ days
- For each: Show 3 outfit suggestions featuring that item
- Option to remove/donate directly to resale apps

**FR-4.2: Utilization Dashboard**
- Visual: Circular chart showing % of wardrobe worn
- Goal: "You're wearing 32% of your closet. Goal: 40%"
- Item-level: Color-code by wear frequency (green = often, red = never)

**FR-4.3: Duplicate Detection**
- Flag similar items: "You have 3 black t-shirts"
- Suggest keeping favorites, donating duplicates

---

## Technical Requirements

### TR-1: Machine Learning

**TR-1.1: On-Device Processing**
- CoreML (iOS) / TensorFlow Lite (Android)
- Model size: <50MB (app store constraint)
- Inference time: <3 seconds per item

**TR-1.2: Model Training**
- Initial dataset: 200K labeled garment images
- Categories: 15 primary, 8 secondary subcategories
- Accuracy target: 90%+ on validation set
- Continuous learning: User corrections retrain model weekly

**TR-1.3: Fallback Handling**
- If confidence <70%: Show "I'm not sure — tap to tag manually"
- Allow skip: User can add item without full tagging

### TR-2: Backend Architecture

**TR-2.1: Database Schema**
```
users
├── user_id (PK)
├── email, created_at, premium_status

items
├── item_id (PK)
├── user_id (FK)
├── category, color, fabric, occasion, pattern, season
├── photo_url (S3 link if cloud backup enabled)
├── times_worn, last_worn_date
├── ai_confidence_score

outfits
├── outfit_id (PK)
├── user_id (FK)
├── item_ids (array)
├── saved_date, last_worn_date, outfit_name

wear_history
├── history_id (PK)
├── user_id (FK)
├── item_id (FK)
├── worn_date
```

**TR-2.2: APIs**
- Weather: OpenWeather API (free tier: 1K calls/day)
- Calendar: iOS EventKit / Android Calendar API
- Backend: Node.js + Express, PostgreSQL
- Cloud storage: AWS S3 (optional, user-consented)

### TR-3: Performance

**TR-3.1: App Launch**
- Cold start: <2 seconds
- Warm start: <0.5 seconds

**TR-3.2: Photo Processing**
- Background removal: <5 seconds per item
- AI tagging: <3 seconds per item
- Batch upload: Process in parallel, max 5 concurrent

**TR-3.3: Offline Mode**
- All core features work offline (on-device AI)
- Sync when reconnected (outfit suggestions cache 7 days)

---

## Design Requirements

### DR-1: Onboarding Flow

**Screen 1:** Welcome + Value Prop
- Headline: "Your closet, organized in 10 minutes"
- Subtext: "AI does the work. You get the outfits."
- CTA: "Start cataloging"

**Screen 2:** Camera Permissions
- "We need camera access to photograph your clothes"
- "Photos never leave your phone unless you enable cloud backup"

**Screen 3:** Catalog Items
- Camera view with AI detection overlay
- Real-time item count: "5 items detected — tap to capture"
- Progress bar: 10 items = "Getting there!", 25 = "Halfway!", 50 = "Almost done!"

**Screen 4:** Review & Correct
- Grid view of tagged items
- Tap item to correct tags
- "Looks good? Tap Next"

**Screen 5:** First Outfit Preview
- "Here's what you can wear tomorrow!"
- Show 1 outfit from cataloged items
- CTA: "See more outfits"

### DR-2: Daily Home Screen

**Layout:**
- Top: Weather widget (temp, icon, "Feels like 52°F")
- Middle: "Today's Outfits" carousel (3-5 swipeable cards)
- Bottom: Quick actions (Add item, View closet, Settings)

**Outfit Card:**
- Visual: Outfit illustration (items arranged vertically)
- Text: "Perfect for: Rainy office day"
- Buttons: "I'll wear this" (saves to today), "Not today" (swipe away)

### DR-3: Visual Design

**Color Palette:**
- Primary: Warm beige (#F5E6D3)
- Accent: Terracotta (#D68A73)
- Text: Charcoal (#2E2E2E)
- Success: Sage green (#A3B18A)

**Typography:**
- Headings: Inter, 700 weight
- Body: Inter, 400 weight
- Mono (item tags): SF Mono

**Imagery:**
- Minimalist line illustrations for empty states
- User photos prominent (not buried in grids)

---

## Out of Scope (V1)

- Social features (outfit sharing, following friends)
- Shopping integration (buy new items)
- Men's formal wear (focus on casual/workwear first)
- Video try-ons or AR overlays
- Multi-user households (shared closets)

---

## Launch Plan

### Phase 1: Internal Beta (Weeks 1-2)
- 50 employee testers
- Focus: AI accuracy, crash rate, onboarding time

### Phase 2: External Beta (Weeks 3-6)
- 500 users via TestFlight
- Focus: Outfit relevance, feature usage, NPS

### Phase 3: Soft Launch (Week 7)
- iOS App Store, US only
- No paid marketing (organic + PR)
- Monitor: Onboarding completion, D1/D7 retention

### Phase 4: Full Launch (Week 10)
- Influencer partnerships, App Store featuring push
- Paid acquisition (Instagram, TikTok)
- Target: 10K downloads in month 1

---

## Appendix: API Examples

**POST /items/upload**
```json
{
  "user_id": "abc123",
  "photo": "base64_encoded_image",
  "ai_tags": {
    "category": "top",
    "color": ["white", "blue"],
    "fabric": "cotton",
    "confidence": 0.92
  }
}
```

**GET /outfits/daily**
```json
{
  "user_id": "abc123",
  "date": "2025-02-26",
  "weather": {
    "temp": 52,
    "conditions": "rainy"
  },
  "outfits": [
    {
      "outfit_id": "out_001",
      "items": ["item_12", "item_34", "item_56"],
      "reason": "Perfect for rainy office day"
    }
  ]
}
```

---

**Document Status:** Ready for Engineering Kickoff  
**Next Review:** Post-Beta (Week 6)
