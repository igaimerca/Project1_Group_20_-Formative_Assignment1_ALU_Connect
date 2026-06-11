# ALU Connect — Simple Demo Script (5 presenters)

**Total time:** 12–15 minutes (~2–3 min each)  
**Record on:** iPhone simulator or real phone (not browser)  
**Tip:** Read the lines in **bold** — they are what you say out loud. Tap what is under **Show**.

---

## Everyone — before you start (30 seconds, anyone)

**Say:**  
“Hi, we are the ALU Connect team — Aime, Aurele, Emmanuel, Mildred, and Shakira. We built a mobile app so ALU students can find events, opportunities, and clubs across Kigali, Mauritius, and the Virtual Hub in one place.”

**Show:** App icon or splash screen.

---

## 1. Aime — Intro, onboarding & login (~2.5 min)

**Say:**  
“I’ll start with how users enter the app.”

**Show:** Fresh install or logged-out state.

**Say:**  
“On first open, we have three onboarding slides. They explain what the app does. You can skip or swipe through. This only shows once — we save that in SharedPreferences.”

**Show:** Swipe onboarding → tap Get Started.

**Say:**  
“For login we have SSO, Google, Apple, and email. SSO signs you in as an organizer who can post. Create account uses the same SSO flow.”

**Show:** Tap **Sign in with ALU Account (SSO)** → land on Home.

**Say:**  
“The bottom bar has five tabs — Home, Explore, Create, Chats, and Profile. We use Provider to manage navigation and app state.”

**Show:** Tap each tab quickly, then stop on Home.

**Say:**  
“Our design uses a dark background and gold accents from the ALU brand. That’s me — Aime. Next is Aurele on Home and Explore.”

---

## 2. Aurele — Home & Explore (~3 min)

**Say:**  
“I’ll show how students discover content.”

**Show:** Home tab.

**Say:**  
“On Home, these category chips filter what you see. All shows featured events, upcoming events, opportunities, and clubs. Events shows only events. Opportunities shows only internships and fellowships.”

**Show:** Tap **Events** → then **Opportunities** → then **All**.

**Say:**  
“Featured events scroll sideways. Tap one to see details.”

**Show:** Tap a featured card (briefly), go back.

**Say:**  
“Explore is the main discovery hub. At the top we put campus filters — Kigali, Mauritius, Virtual Hub — so users don’t miss them. You can search and filter by type.”

**Show:** Explore tab → tap **Kigali** campus card → show filtered list → tap **All Campuses**.

**Say:**  
“There are also tabs for My RSVPs and Clubs. Empty states tell you what to do next if nothing is here.”

**Show:** My RSVPs tab → Clubs tab → back to Discover.

**Say:**  
“That’s Aurele. Emmanuel will show RSVP and how data is saved. Mildred will show chats after that.”

---

## 3. Emmanuel — Events, RSVP & persistence (~2.5 min)

**Say:**  
“I’ll show event details and how we save data.”

**Show:** Explore → tap any event.

**Say:**  
“On the event page you see date, campus, location, and who’s going. Students can tap Going or Interested. The count updates right away.”

**Show:** Tap **Going** → then **Interested**.

**Say:**  
“You can bookmark with the save icon. My RSVPs lists everything you marked Going or Interested.”

**Show:** Save icon → Explore → **My RSVPs** tab.

**Say:**  
“All of this is stored in SQLite on the phone — feed items, RSVPs, clubs, chats, and saved posts. Login and profile use SharedPreferences.”

**Show:** (Optional) Briefly open `lib/data/database/database_helper.dart` or `lib/providers/feed_provider.dart` in the editor.

**Say:**  
“Now I’ll prove it persists. I’ll close the app completely and open it again.”

**Show:** Stop app → relaunch → still logged in, RSVP still there.

**Say:**  
“That’s Emmanuel. Mildred will show chats.”

---

## 4. Mildred — Chats (~2 min)

**Say:**  
“I’ll show how students message each other.”

**Show:** Chats tab.

**Say:**  
“You can filter All Chats, Groups, or Peers. Unread messages show a badge. Open a thread, read messages, and send a reply or use a quick reply.”

**Show:** Open a thread → send a message → tap a quick reply.

**Say:**  
“Chats are saved in SQLite so messages stay after you close the app. That’s Mildred — Shakira will show create and profile.”

---

## 5. Shakira — Create, edit, profile & wrap-up (~2.5 min)

**Say:**  
“I’ll show how organizers post and manage content.”

**Show:** Create tab (must be logged in with SSO).

**Say:**  
“Only organizers can create posts. Students see a locked screen. We can publish an Event or Opportunity with title, description, date, time, campus, category, and a cover image.”

**Show:** Fill a short test post OR show an existing one → Publish (if quick).

**Say:**  
“In Profile, My Posts lists what you published. You can edit or delete your own posts.”

**Show:** Profile → **My Posts** → **Edit** → change title → Save → or **Delete** with confirm.

**Say:**  
“Saved shows bookmarked items. Notifications shows chats and updates. Help and Support opens a sheet with our email support@aluconnect.com and a phone number.”

**Show:** Saved → Notifications → **Help & Support** sheet.

**Say:**  
“We also have chats with quick replies, club join buttons, animations on lists, and a custom date-time picker. That makes the app feel polished for ALU students.”

**Say (closing — all can join):**  
“That’s ALU Connect. Thank you from all five of us. Our GitHub repo and contribution tracker are in the report.”

---

## Quick checklist (tick before uploading)

- [ ] Recorded on phone or simulator (not web only)  
- [ ] All 5 members spoke  
- [ ] Showed: login, home filters, campus explore, RSVP, create/edit post, profile, app restart  
- [ ] Mentioned SQLite + SharedPreferences  
- [ ] Video is 10–15 minutes  
- [ ] Uploaded and link added to PDF + tracker  

---

## If someone is absent

| Person | Cover their part |
|--------|------------------|
| Aime | Onboarding + login + tab overview |
| Aurele | Home categories + Explore campus filter |
| Emmanuel | RSVP + restart app |
| Mildred | Chats + send message |
| Shakira | Create post + My Posts edit/delete + Profile |
