# ✨ TODO.md — MVP + Features + Bugs ✨

## 🏁 MVP Completion — Target: 24th Nov

- **Supabase DB backups:** weekly, include rollback (DB-side). - ✅ done
- **Data migration:** SPC per student, class entries in admin/students. - ✅ done
- **CI/CD improvements:** local DB setup to avoid mutating production.
- **Midterm handling:** allow blank description; modify mark entry: - ✅ done
  - Mid only → final = mid
  - Mid + end → final = average
  - Otherwise → final = null

- **Redesign reports template:** comment limit 50 words. - done

---

## 🐛 BUGFIXES

- Report dropdown to access archived data (EA)
- Performance overview div (main page) — ✅ done.
- Review UX for data/table labels. - ✅ done
- Performance overview charts. - ✅ done
- Comments page: prevent HEAD from editing teacher comments. - ✅ done
- Students page: sticky scrollbar makes last entry hard to read. - ✅ done

---

## 🚀 FUTURE / NON-MVP

- MTA implementation (EA)
  - new subject merchant (ID, name, subscription mechanism)
- Access archived students (target pre-Jan '26).
- Add account name to report logs.
- Do a code review
- Develop langing page (AM \* JM)
- write documentation for backend (EA)

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
- Simple caching & memoization — done
- Prisma Accelerate — done.
- Cookie system + browser integration — done

---

## 🔐 Auth & Role Separation

- JWT cookie bug — ✅ Done.

- Session persistence — ✅ done.

- Prevent login requirement on reload (localStorage) — done

- Role separation modules:
  - Grades — ⏳ Pending
  - Comments — ⏳ Pending
  - Reports — ✅ Done

- Users cannot access data not fetched (enforced backend).

---

## 🏗️ Hosting Planning

- DB + server monthly cost 💰
- Annual cost projection 📈

---
