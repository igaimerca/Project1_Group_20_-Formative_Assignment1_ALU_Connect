# ALU Connect — Formative Assignment 1 Technical Report

**Group:** ALU Connect Team (Aime, Aurele, Emmanuel, Shakira)  
**Course:** Mobile Application Development  
**Submission file:** `ALU_Connect_Formative_Assignment1.pdf`

---

## 1. Introduction & Product Vision

### 1.1 Overview

ALU Connect is a Flutter mobile application built for the African Leadership University (ALU) community. It addresses fragmented campus communication by giving students one place to discover events, internships, clubs, and leadership opportunities across Kigali, Mauritius, and the Virtual Hub. The app supports onboarding, authentication, a personalized home feed, exploration with campus filters, RSVP workflows, role-gated content creation, community chats, and a profile hub for posts, saved items, and support.

Our goal was not to copy sample layouts, but to design a product that feels native to ALU: multi-campus, leadership-oriented, and socially engaging while remaining technically credible for a formative mobile assignment.

### 1.2 Fit with ALU Culture & Context

- **Multi-campus discovery** — Students filter by Kigali, Mauritius, Virtual Hub, or view all campuses from a prominent Explore selector.
- **Cohort social proof** — Event detail shows how many peers from the user’s cohort are attending, encouraging participation.
- **Role-gated publishing** — Only organizers (SSO / approved emails) can create posts; students engage via RSVP, save, and chat. This mirrors real campus permission models.
- **Pan-African content** — Mock data uses ALU-relevant workshops, hackathons, internships, and Rwandan community names.
- **Community over isolation** — Group and peer chat threads tie to clubs and events, not anonymous feeds alone.

### 1.3 Engaging & Unique Features

| Feature | Why it engages |
|--------|----------------|
| Featured events carousel | Visual, swipeable highlights on Home |
| Category chips (All / Events / Opportunities / Clubs) | Home content adapts to what the user wants |
| Campus explore cards with counts | Makes cross-campus discovery obvious |
| RSVP Going / Interested | Low-friction commitment with persisted state |
| Cover image upload on create | Personal, visual posts from organizers |
| Edit & delete own posts | Organizers manage content without admin tools |
| Saved items + My Posts | Personal library and publishing history |
| Help & Support sheet | One-tap email (`support@aluconnect.com`) or phone |
| Dark + gold UI | Aligns with ALU branding; high contrast for readability |
| Animations | Splash, fade/slide transitions, staggered list items |

---

## 2. Design Rationale & Implementation

### 2.1 UI/UX Redesign

We redesigned navigation and layout rather than cloning reference screens:

- **Bottom navigation (5 tabs)** — Home, Explore, Create, Chats, Profile keeps primary actions one tap away.
- **Explore as hub** — Discover, My RSVPs, and Clubs live in one tab with sub-tabs, reducing stack depth.
- **Home category filtering** — Selecting Events shows only upcoming events; Opportunities shows internships/fellowships; All shows featured + sections.
- **Campus selector at top of Explore** — Replaced a hidden bottom-of-list pattern with horizontal cards and an active-filter banner.
- **Empty states** — Every major list guides the user (e.g. “Explore events”, “Create a post”) instead of blank screens.
- **Custom date/time widget** — Native pickers for create/edit; consistent display on cards and detail screens.

**Typography & color:** Background `#0B111D`, gold accent `#F9B83E` from the ALU logo, Inter via Google Fonts. Touch targets ≥ 48dp on primary buttons.

### 2.2 Navigation & State Handling

- **Provider (`ChangeNotifier`)** — `AuthProvider`, `FeedProvider`, `ClubProvider`, `ChatProvider`, `NavigationProvider`.
- **Main shell** — `AnimatedSwitcher` on tab index; filters and scroll positions held in providers.
- **Detail routes** — `FadeSlideRoute` for event detail, edit post, saved, notifications.
- **SQLite (`sqflite`)** — Feed items, RSVPs, clubs, chat threads/messages, saved IDs; survives app restart.
- **SharedPreferences** — Onboarding complete, login session, user profile JSON.
- **Atomic updates** — RSVP changes update attendee count, SQLite, and UI in one `FeedProvider` method.

```
Onboarding → Login → MainShell
  ├── Home (feed categories)
  ├── Explore (Discover | RSVPs | Clubs + campus filter)
  ├── Create (role-gated publish)
  ├── Chats (threads + detail)
  └── Profile (posts, saved, notifications, support)
```

### 2.3 Technical Architecture

```
lib/
├── core/           theme, constants, navigation transitions
├── data/           models, mock seed, SQLite, preferences
├── providers/      app state
├── screens/        feature screens by domain
└── widgets/        reusable cards, empty states, date/time, campus selector
```

**Key packages:** `provider`, `sqflite`, `shared_preferences`, `google_fonts`, `image_picker`, `url_launcher`, `intl`, `uuid`.

### 2.4 Major Product Decisions

| Decision | Justification |
|----------|---------------|
| SQLite + SharedPreferences | Structured persistence for feeds/chats; lightweight session flags |
| Mock seed data | No ALU API in scope; demonstrates full offline UX |
| `canPost` on profile | Realistic organizer vs student roles for demos |
| Edit/delete by `host` name | Simple ownership model without backend auth |
| Support email `support@aluconnect.com` | Branded, maintainable contact channel |

### 2.5 Error Handling

Login validation, form validation on publish (title ≥ 5, description ≥ 20 chars), empty search with “Clear filters”, unauthorized create screen, sign-out confirmation, delete-post confirmation, compact empty states to avoid layout overflow.

---

## 3. Challenges, Team & References

### 3.1 Challenges & Solutions

| Challenge | Solution |
|-----------|----------|
| iOS `sqflite_darwin` build error | `flutter clean`, reinstall pods, static frameworks in Podfile |
| Layout overflow on small tabs | Scrollable, compact `EmptyState` with `LayoutBuilder` |
| Campus filter hard to find | Moved to top of Explore with visual cards |
| Date/time inconsistency | Shared `AluDateTimePicker` and `AluDateTimeDisplay` widgets |
| Image picker on iOS | Native permissions in Info.plist; full restart after plugin add |
| Post lifecycle | `updateFeedItem` / `deleteFeedItem` in SQLite + provider; edit screen reuses create form |

### 3.2 Team & Contributions

**Active members (4):** Aime, Aurele, Emmanuel, Shakira — each with a dedicated Git branch (`aime`, `aurele`, `emmanuel`, `shakira`). Mildred is no longer on the team; her tasks were redistributed (see `TEAM_CONTRIBUTIONS.md`).

**Contribution tracker:** [ADD GOOGLE SHEET LINK — copy course template]

**GitHub repository:** [ADD REPO URL]

### 3.3 Demo Video Alignment (10–15 min)

The demo should run on **iOS Simulator or physical device** (not browser-only). Cover: onboarding, SSO login, home categories, explore + campus filter, RSVP, create post with image, edit/delete from My Posts, chats, profile (saved, notifications, help sheet), app restart to prove SQLite/SharedPreferences, and a short code walkthrough (one provider + database helper).

See `docs/DEMO_VIDEO_SCRIPT.md` for a timed script.

### 3.4 Future Work

Real ALU SSO, push notifications, backend API, comment threads on posts, analytics for organizers.

### 3.5 References

African Leadership University. (n.d.). *About ALU*. https://alueducation.com  

Google. (n.d.). *Flutter documentation*. https://docs.flutter.dev  

Material Design. (n.d.). *Accessibility*. https://m3.material.io  

Provider package. (n.d.). https://pub.dev/packages/provider  

SQLite / sqflite. (n.d.). https://pub.dev/packages/sqflite  

Shared preferences. (n.d.). https://pub.dev/packages/shared_preferences  

---

*Export this document to PDF (≤ 3 pages) as `ALU_Connect_Formative_Assignment1.pdf` — use Print to PDF or Pandoc with tight margins.*
