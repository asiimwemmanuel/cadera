---
# ✅ 16/09/25 TODO List
---

## 🎯 High-Level

- Implement midterm/EOT via a simple pipeline appendage in the subject record at report time — ⏳

---

## 🚀 WEEK 1 — MVP COMPLETION

| Task                                     | Assignee        | Status         | Notes                                                                            |
| ---------------------------------------- | --------------- | -------------- | -------------------------------------------------------------------------------- |
| Role separation completion               | Emmanuel        | ✅ Complete    |                                                                                  |
| Promotion system                         | Emmanuel        | 🚧 In Progress | Needs archive access on students page: sort by collections, parse `archivedData` |
| Report zipping                           | Joshua          | 🚧 In Progress |                                                                                  |
| Email system on teacher account creation | Joshua & Albert | ⏳ Pending     |                                                                                  |
| Implement forgot password logic          | Joshua          | ⏳ Pending     |                                                                                  |

---

## 🔗 WEEK 2 — DATA INTEGRATION

| Task                                               | Assignee | Status |
| -------------------------------------------------- | -------- | ------ |
| Add teacher & student data                         | Emmanuel | ⏳     |
| Add top class data                                 | Emmanuel | ⏳     |
| Add class average to class service (for dashboard) | —        | ⏳     |

> **Internal target ship date:** `6th Oct`

---

## ⚙ OTHER: Performance & Infra

### 1. Speed Up Queries

| Task                         | Assignee | Status         |
| ---------------------------- | -------- | -------------- |
| Fix double API calls         | Emmanuel | ✅ Done        |
| Simple caching & memoization | Joshua   | 🚧 In Progress |
| Prisma Accelerate            | Emmanuel | 🚧 In Progress |

### 2. Fix cookie system with browser integration — 🚧 In Progress (Emmanuel)

---

## 🧩 Additional Features (Later)

- Edit mode — ⏳ Pending

---

# 🔐 THE GREAT LOCK-IN OF 2025

## Login Flow (Non-MVP) — ⏳ Pending

- OTP validation on login page
- OTP must match email and:

  - Not expired
  - `mustChangePassword === true`

- Valid OTP → Force password change screen
- Separate **OTP UI section**

### Password Reset Logic — ⏳ Design Pending

**If Teacher:**

| Approach            | Status | Notes                                                       |
| ------------------- | ------ | ----------------------------------------------------------- |
| Admin-approval flow | ⏳     | Request → Admin email → Approve → Force-reset on next login |
| Self-service flow   | ⏳     | Same system but scoped to user only                         |

> Choose based on fastest secure implementation.

---

## 🎭 Role Separation — Scope

| Module   | Status  |
| -------- | ------- |
| Grades   | ⏳      |
| Comments | ⏳      |
| Reports  | ✅ Done |

---

## ☁ Hosting Planning — ⏳ Pending

- OnRender deployment
- DB + server monthly breakdown
- Annual cost projection

---

## 📦 Other — ⏳ Pending

- Reports should be exported as **timestamped ZIP**

---

# 🧠 MAIN IMPLEMENTATION NOTES

### Login & Auth

| Task                                               | Status |
| -------------------------------------------------- | ------ |
| Fix JWT cookie bug                                 | ✅     |
| Ensure session persistence                         | 🚧     |
| Prevent login requirement on reload (localStorage) | 🚧     |
| Account handling: PIN, change password, edit       | ⏳     |

### Roles + Permissions

> Security enforced by **data not being fetched** — ongoing policy

---

## 👨‍🎓 Students Page — ✅ Mostly done

| Item                                                      | Status |
| --------------------------------------------------------- | ------ |
| Subject offerings limited per class                       | ✅     |
| "Edit profile" modal flicker fix                          | ✅     |
| Prefill fields                                            | ⏳     |
| Editable fields: name, parent email, ID, subject offering | ⏳     |
| Fetch classes + student count (backend change)            | ⏳     |

### Add New Student Modal

- UI same as edit flow — ⏳
- Modal flicker bug still present — 🚧 Needs fixing

---

## 👩‍🏫 Teachers Page — 🚧 Almost done

## 🏫 Classes Page — 🚧 In Development ("getting cooked")

> Target: **Edit-only functionality**

## 🧮 Grades Page — ✅ Mostly done

## 💬 Comments Page — ✅ Mostly done

## 📑 Reports Page — ✅ Mostly done

## 🎓 School Page — 🚧 Almost done (promotions logic pending)

## ⚙ Settings Page — ⏳

- Replace all avatars with placeholders

---
