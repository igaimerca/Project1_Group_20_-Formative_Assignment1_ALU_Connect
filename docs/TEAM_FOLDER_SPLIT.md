# ALU Connect — Code split by team member (5 people)

Each person works on their **branch**, owns the folders below, and opens a PR to `main`.  
Only touch **your folders** + shared files listed under your name.

**Copy-paste `git add` + commit message:** [GIT_PUSH_GUIDE.md](GIT_PUSH_GUIDE.md)

---

## Quick reference

| Person   | Branch     | Main area                          |
|----------|------------|------------------------------------|
| **Aime**     | `aime`     | App entry, auth, onboarding, nav   |
| **Aurele**   | `aurele`   | Home + Explore (discover)            |
| **Emmanuel** | `emmanuel` | Events, RSVP, database, feed data  |
| **Mildred**  | `mildred`  | Chats                                |
| **Shakira**  | `shakira`  | Create, clubs, profile, UI polish  |

---

## 1. Aime — `aime`

**You own:**

```
lib/main.dart
lib/app.dart

lib/screens/onboarding/
lib/screens/auth/

lib/providers/auth_provider.dart
lib/providers/navigation_provider.dart

lib/widgets/navigation/main_shell.dart

lib/data/local/preferences_service.dart
lib/data/models/user_profile.dart

lib/core/navigation/
```

**Also maintain (integration):**

```
lib/core/constants/app_strings.dart   ← add global strings only
pubspec.yaml                          ← dependencies (coordinate with team)
README.md
docs/DELIVERABLES.md
CONTRIBUTING.md
TEAM_CONTRIBUTIONS.md
```

**Your demo video part:** Onboarding, login, bottom navigation.

**Push commands:**

```bash
git checkout aime
git pull origin main
# edit your files
git add lib/main.dart lib/app.dart lib/screens/onboarding/ lib/screens/auth/ \
  lib/providers/auth_provider.dart lib/providers/navigation_provider.dart \
  lib/widgets/navigation/ lib/data/local/preferences_service.dart \
  lib/data/models/user_profile.dart lib/core/navigation/
git commit -m "feat(auth): your change"
git push origin aime
```

---

## 2. Aurele — `aurele`

**You own:**

```
lib/screens/home/
lib/screens/explore/explore_screen.dart

lib/widgets/explore/
lib/widgets/cards/featured_event_card.dart

lib/widgets/common/app_header.dart
lib/widgets/common/search_field.dart
lib/widgets/common/filter_chips_row.dart
```

**Read-only (do not edit — ask Emmanuel/Shakira):**

- `lib/providers/feed_provider.dart` — use it, don’t rewrite
- `lib/screens/events/` — Emmanuel’s

**Your demo video part:** Home categories, Explore discover, campus filter.

**Push commands:**

```bash
git checkout aurele
git pull origin main
git add lib/screens/home/ lib/screens/explore/explore_screen.dart \
  lib/widgets/explore/ lib/widgets/cards/featured_event_card.dart \
  lib/widgets/common/app_header.dart lib/widgets/common/search_field.dart \
  lib/widgets/common/filter_chips_row.dart
git commit -m "feat(home): your change"
git push origin aurele
```

---

## 3. Emmanuel — `emmanuel`

**You own:**

```
lib/screens/events/

lib/providers/feed_provider.dart

lib/data/database/database_helper.dart
lib/data/mock/mock_data.dart
lib/data/models/feed_item.dart

lib/widgets/cards/feed_item_card.dart
lib/widgets/common/date_time_widget.dart
```

**Shared file rule:** `explore_screen.dart` is Aurele’s — if My RSVPs tab needs changes, tell Aurele or put UI in `my_rsvps_screen.dart` (yours).

**Your demo video part:** Event detail, RSVP, My RSVPs, app restart persistence.

**Push commands:**

```bash
git checkout emmanuel
git pull origin main
git add lib/screens/events/ lib/providers/feed_provider.dart \
  lib/data/database/ lib/data/mock/mock_data.dart lib/data/models/feed_item.dart \
  lib/widgets/cards/feed_item_card.dart lib/widgets/common/date_time_widget.dart
git commit -m "feat(rsvp): your change"
git push origin emmanuel
```

---

## 4. Mildred — `mildred`

**You own:**

```
lib/screens/chats/

lib/providers/chat_provider.dart

lib/data/models/chat_models.dart

lib/widgets/cards/chat_thread_tile.dart
```

**Database note:** Chat tables live in `database_helper.dart` (Emmanuel’s file).  
For chat schema changes: open a small PR to `emmanuel` branch or ask Emmanuel to add your SQL.

**Your demo video part:** Chat list, filters, send message, quick replies.

**Push commands:**

```bash
git checkout mildred
git pull origin main
git add lib/screens/chats/ lib/providers/chat_provider.dart \
  lib/data/models/chat_models.dart lib/widgets/cards/chat_thread_tile.dart
git commit -m "feat(chats): your change"
git push origin mildred
```

---

## 5. Shakira — `shakira`

**You own:**

```
lib/screens/create/
lib/screens/clubs/
lib/screens/profile/

lib/providers/club_provider.dart

lib/data/models/club.dart
lib/data/local/image_storage.dart

lib/widgets/cards/club_card.dart
lib/widgets/profile/

lib/widgets/common/splash_screen.dart
lib/widgets/common/empty_state.dart
lib/widgets/common/fade_in_item.dart
lib/widgets/common/gradient_button.dart
lib/widgets/common/outlined_gold_button.dart
lib/widgets/common/alu_logo.dart
lib/widgets/common/feed_cover_image.dart

assets/images/
```

**Platform (only when your feature needs it):**

```
ios/Runner/Info.plist          ← camera/photo permissions (create post)
android/app/src/main/AndroidManifest.xml
```

**Your demo video part:** Create/edit/delete post, clubs, profile, help & support.

**Push commands:**

```bash
git checkout shakira
git pull origin main
git add lib/screens/create/ lib/screens/clubs/ lib/screens/profile/ \
  lib/providers/club_provider.dart lib/data/models/club.dart \
  lib/data/local/image_storage.dart lib/widgets/cards/club_card.dart \
  lib/widgets/profile/ lib/widgets/common/splash_screen.dart \
  lib/widgets/common/empty_state.dart lib/widgets/common/fade_in_item.dart \
  lib/widgets/common/gradient_button.dart lib/widgets/common/outlined_gold_button.dart \
  lib/widgets/common/alu_logo.dart lib/widgets/common/feed_cover_image.dart \
  assets/images/
git commit -m "feat(profile): your change"
git push origin shakira
```

---

## Shared by everyone (rules)

| Path | Owner | Rule |
|------|-------|------|
| `lib/core/theme/` | Shakira (visual), anyone for small fixes | PR review by Shakira |
| `lib/core/constants/app_strings.dart` | Aime | Add strings here, don’t hardcode in screens |
| `lib/core/navigation/page_transitions.dart` | Aime | Use `pushFadeSlide()` for new screens |
| `lib/data/database/database_helper.dart` | Emmanuel | Others request chat/club SQL via PR |
| `pubspec.yaml` | Aime | Say in group chat before adding packages |
| `docs/DEMO_VIDEO_SCRIPT.md` | Whole team | Each person edits only their section |

**Do not edit** another member’s folder without their OK. Use PRs to `main`.

---

## Merge workflow (all 5)

```bash
# Before you start each session
git checkout <your-branch>
git fetch origin
git merge origin/main

# After you finish
git push origin <your-branch>
# Open PR on GitHub: <your-branch> → main
```

Every member needs **at least 2–3 commits** on their branch before submission.

---

## Folder tree (who owns what)

```
lib/
├── main.dart                          Aime
├── app.dart                           Aime
├── core/
│   ├── constants/app_strings.dart     Aime
│   ├── navigation/                    Aime
│   └── theme/                         Shakira (lead)
├── data/
│   ├── database/database_helper.dart  Emmanuel
│   ├── local/
│   │   ├── preferences_service.dart   Aime
│   │   └── image_storage.dart         Shakira
│   ├── mock/mock_data.dart            Emmanuel
│   └── models/
│       ├── feed_item.dart             Emmanuel
│       ├── chat_models.dart           Mildred
│       ├── club.dart                  Shakira
│       └── user_profile.dart          Aime
├── providers/
│   ├── auth_provider.dart             Aime
│   ├── navigation_provider.dart       Aime
│   ├── feed_provider.dart             Emmanuel
│   ├── chat_provider.dart             Mildred
│   └── club_provider.dart             Shakira
├── screens/
│   ├── onboarding/                    Aime
│   ├── auth/                          Aime
│   ├── home/                          Aurele
│   ├── explore/explore_screen.dart    Aurele
│   ├── events/                        Emmanuel
│   ├── chats/                         Mildred
│   ├── create/                        Shakira
│   ├── clubs/                         Shakira
│   └── profile/                       Shakira
└── widgets/
    ├── navigation/main_shell.dart     Aime
    ├── explore/                       Aurele
    ├── profile/                       Shakira
    ├── cards/
    │   ├── featured_event_card.dart   Aurele
    │   ├── feed_item_card.dart        Emmanuel
    │   ├── chat_thread_tile.dart      Mildred
    │   └── club_card.dart             Shakira
    └── common/
        ├── app_header.dart            Aurele
        ├── search_field.dart          Aurele
        ├── filter_chips_row.dart      Aurele
        ├── date_time_widget.dart      Emmanuel
        ├── splash_screen.dart         Shakira
        ├── empty_state.dart           Shakira
        ├── fade_in_item.dart          Shakira
        ├── gradient_button.dart       Shakira
        ├── outlined_gold_button.dart  Shakira
        ├── alu_logo.dart              Shakira
        └── feed_cover_image.dart      Shakira
```
