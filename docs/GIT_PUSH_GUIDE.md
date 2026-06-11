# ALU Connect — Git setup for the whole team

Follow the steps **in order**. Do not skip ahead.

| | GitHub URL |
|--|------------|
| **Clone from (old repo)** | https://github.com/igaimerca/Project1_Group_20_ALU_Connect.git |
| **New repo (final `origin`)** | https://github.com/igaimerca/Project1_Group_20_-Formative_Assignment1_ALU_Connect.git |

**Plan**
1. Aime pushes `main` with **README only** to the new repo  
2. Each person clones, points to the new repo, creates **their branch**, adds **their files**, pushes  
3. Later: merge all branches into `main` on GitHub  

---

# STEP 1 — Aime only (do this first)

## 1.1 Open the project folder

```bash
cd 2026/alu_connect
```

## 1.2 Remove old remote and add the new repo

```bash
git remote remove origin
```

If you see `error: No such remote: 'origin'` — ignore it and continue.

```bash
git remote add origin https://github.com/igaimerca/Project1_Group_20_-Formative_Assignment1_ALU_Connect.git
```

## 1.3 Push `main` with README only

```bash
git checkout main
git rm -r --cached .
git add README.md
git commit -m "docs: initial README for ALU Connect project"
git push -u origin main
```

Your files are still on your computer. Only README is on GitHub `main` for now.

## 1.4 Create your branch `aime` and push your files

```bash
git checkout -b aime
git add lib/main.dart lib/app.dart lib/screens/onboarding/onboarding_screen.dart lib/screens/auth/login_screen.dart lib/providers/auth_provider.dart lib/providers/navigation_provider.dart lib/widgets/navigation/main_shell.dart lib/data/local/preferences_service.dart lib/data/models/user_profile.dart lib/core/navigation/page_transitions.dart lib/core/constants/app_strings.dart
git commit -m "feat(auth): add onboarding, login, and app navigation shell"
git push -u origin aime
```

## 1.5 Push project config (pubspec, platforms, assets, docs)

Still on branch `aime`. Run this **second commit**:

```bash
git checkout aime
git add pubspec.yaml pubspec.lock analysis_options.yaml .gitignore .metadata android/ ios/ linux/ macos/ windows/ web/ assets/ test/ docs/
git commit -m "chore: add Flutter project config, platforms, assets, and team docs"
git push origin aime
```

> **Important:** run this on branch `aime`, NOT on `main`.  
> If `pubspec.yaml` is missing, restore it:  
> `git checkout 7711c8b -- pubspec.yaml pubspec.lock android/ ios/ ...`  
> (or ask Aime — chore commit is already on `origin/aime` now)

> Never run `git init` again — it destroys history.  
> Never `git add` on `main` except README.

## 1.6 Tell the team

Send this message in your group chat:

> Aime pushed `main` (README only) and `aime` branch.  
> Everyone: follow **STEP 2** in `docs/GIT_PUSH_GUIDE.md`, then your name in **STEP 3**.

---

# STEP 2 — Everyone else (Aurele, Emmanuel, Mildred, Shakira)

**Wait until Aime confirms `main` is on the new repo.**

## 2.1 Clone the old repo

```bash
git clone https://github.com/igaimerca/Project1_Group_20_ALU_Connect.git alu_connect
cd alu_connect
```

## 2.2 Remove old remote and add the new repo

```bash
git remote remove origin
git remote add origin https://github.com/igaimerca/Project1_Group_20_-Formative_Assignment1_ALU_Connect.git
git fetch origin
```

## 2.3 Confirm you see `main` from the new repo

```bash
git branch -r
```

You should see `origin/main`.

---

# STEP 3 — Each person pushes their branch

Find **your name** below. Run every command in your section.

---

## Aurele

```bash
git checkout -b aurele origin/main
git add lib/screens/home/home_screen.dart lib/screens/explore/explore_screen.dart lib/widgets/explore/campus_selector.dart lib/widgets/cards/featured_event_card.dart lib/widgets/common/app_header.dart lib/widgets/common/search_field.dart lib/widgets/common/filter_chips_row.dart
git commit -m "feat(home): add home feed, explore discover, and campus filters"
git push -u origin aurele
```

---

## Emmanuel

```bash
git checkout -b emmanuel origin/main
git add lib/screens/events/event_detail_screen.dart lib/screens/events/my_rsvps_screen.dart lib/providers/feed_provider.dart lib/data/database/database_helper.dart lib/data/mock/mock_data.dart lib/data/models/feed_item.dart lib/widgets/cards/feed_item_card.dart lib/widgets/common/date_time_widget.dart
git commit -m "feat(events): add event detail, RSVP flow, SQLite feed persistence"
git push -u origin emmanuel
```

---

## Mildred

```bash
git checkout -b mildred origin/main
git add lib/screens/chats/chats_screen.dart lib/screens/chats/chat_detail_screen.dart lib/providers/chat_provider.dart lib/data/models/chat_models.dart lib/widgets/cards/chat_thread_tile.dart
git commit -m "feat(chats): add chat threads, messaging, and quick replies"
git push -u origin mildred
```

---

## Shakira

```bash
git checkout -b shakira origin/main
git add lib/screens/create/create_post_screen.dart lib/screens/clubs/clubs_tab.dart lib/screens/profile/profile_screen.dart lib/screens/profile/my_posts_screen.dart lib/screens/profile/edit_post_screen.dart lib/screens/profile/notifications_screen.dart lib/screens/profile/saved_screen.dart lib/providers/club_provider.dart lib/data/models/club.dart lib/data/local/image_storage.dart lib/widgets/cards/club_card.dart lib/widgets/profile/help_support_sheet.dart lib/widgets/common/splash_screen.dart lib/widgets/common/empty_state.dart lib/widgets/common/fade_in_item.dart lib/widgets/common/gradient_button.dart lib/widgets/common/outlined_gold_button.dart lib/widgets/common/alu_logo.dart lib/widgets/common/feed_cover_image.dart lib/core/theme/app_colors.dart lib/core/theme/app_theme.dart assets/images/ ios/Runner/Info.plist android/app/src/main/AndroidManifest.xml
git commit -m "feat(profile): add create post, clubs, profile, and shared UI components"
git push -u origin shakira
```

---

# STEP 4 — Merge everything to `main` (later, whole team)

When all 5 branches are pushed:

1. Go to https://github.com/igaimerca/Project1_Group_20_-Formative_Assignment1_ALU_Connect.git  
2. Click **Pull requests** → **New pull request**  
3. Merge in this order (or any order):
   - `aime` → `main`
   - `aurele` → `main`
   - `emmanuel` → `main`
   - `mildred` → `main`
   - `shakira` → `main`
4. Fix merge conflicts if GitHub shows any  
5. After all merged, everyone runs:

```bash
git checkout main
git pull origin main
flutter pub get
flutter run
```

---

# FIX — accidentally pushed everything to `main`

If `main` has the full app instead of README only:

```bash
cd alu_connect
git fetch origin
git checkout main
git reset --hard 1333f33
git push --force origin main
```

> Replace `1333f33` with your README-only commit hash (`git log --oneline` → look for `docs: initial README`).

Check branches:

```bash
git ls-tree -r --name-only origin/main    # should show README.md only
git ls-tree -r --name-only origin/aime    # should show only Aime's files
```

---

# Problems?

| Problem | Fix |
|---------|-----|
| `remote remove origin` fails | Skip it. Run `git remote add origin ...` only. |
| Branch already exists | `git branch -D aurele` then create again from `origin/main` |
| `git push` asks for login | Use GitHub username + Personal Access Token (not password) |
| Nothing to commit | Make sure you are in the `alu_connect` folder and files exist on disk |
| `origin/main` not found | Aime has not pushed `main` yet — wait for STEP 1 |

---

# Who owns which files?

See `docs/TEAM_FOLDER_SPLIT.md` for the full folder list.
