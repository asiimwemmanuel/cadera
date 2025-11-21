# ✨ TODO.md — MVP + Features + Bugs ✨

## 🏁 MVP Completion — Target: 24th Nov

- **Supabase DB backups:** weekly, include rollback (DB-side).
- **Data migration:** SPC per student, class entries in admin/students.
- **Midterm handling:** allow blank description; modify mark entry:
  - Mid only → final = mid
  - Mid + end → final = average
  - Otherwise → final = null

- **Redesign reports template:** comment limit 500 chars / ~20 words.
- **CI/CD improvements:** local DB setup to avoid mutating production.

---

## 🐛 BUGFIXES

- Performance overview div (main page) — ✅ done.
- Review UX for data/table labels.
- Performance overview charts.
- Comments page: prevent HEAD from editing teacher comments.

---

## 🚀 FUTURE / NON-MVP

- Access archived students (target pre-Jan '26).
- Add account name to report logs.

---

## 📊 High-Level / Other Implementation Notes

- Midterm/EOT pipeline appendage at report time. ⚡
- Email system on teacher account creation — ⏳ Pending.
- Forgot password logic — ⏳ Pending.
- Student demotion — ⏳ Pending.

### Students Page

- Subject offerings per class — ✅ Done.
- Prefill fields — ⏳ Pending.
- Editable fields (name, parent email, ID, subject offering) — ⏳ Pending.
- Fetch classes + student count — ⏳ Pending.
- Add New Student modal — ⏳ Pending; flicker bug ⚠️

### Teachers / Classes / Grades / Reports

- Teachers Page — almost done.
- Classes Page — in dev, edit-only.
- Grades Page — mostly done.
- Comments Page — mostly done.
- Reports Page — mostly done.
- School Page — almost done (promotion logic pending).
- Settings Page — pending; replace avatars with placeholders 🖼️.

---

## ⚡ Performance & Infra

- Fix double API calls — ✅ Done.
- Simple caching & memoization — ⏳ In Progress.
- Prisma Accelerate — ⏳ In Progress.
- Cookie system + browser integration — ⏳ In Progress.

---

## 🔐 Auth & Role Separation

- JWT cookie bug — ✅ Done.

- Session persistence — ⏳ In Progress.

- Prevent login requirement on reload (localStorage) — ⏳ In Progress.

- Role separation modules:
  - Grades — ⏳ Pending
  - Comments — ⏳ Pending
  - Reports — ✅ Done

- Users cannot access data not fetched (enforced backend).

---

## 🏗️ Hosting Planning

- OnRender deployment 🌐
- DB + server monthly cost 💰
- Annual cost projection 📈

---

✅ **Non-Misc Addendum:** Implement midterm/EOT via simple pipeline appendage at report time.
