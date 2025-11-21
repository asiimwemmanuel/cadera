---

**THINKING**

---

**reports**
add a warning at report generation, to ensure all data is complete (NOT mvp)

**reports function adjustment**
before generating reports, go through ACTIVE students, ensure there's nothing missing.

* check their offerings, and ensure they have 'necessary'
  . if MT, all students should have ONLY midterm entries, and no EOT entries.
  . if EOT, all students should have BOTH entries in grade records.
  . no comments should be missing: if a subject is offered, ensure there’s a comment.
* add flag (midterm/endofterm)

---

**comments**
check subject comment dtos, ensure consistency (works tho)
don't load main modal if there is no selected subject
generate a new commentId if it's a new comment.

the main comments panel should know whether or not an entity has been selected from subject sidebar (new prop);
display something if and only if it has. otherwise, put some reasonable placeholder.

remove memoization from any component displaying live data (commentsTable, for example)

---

**promotions**

1. if in terminal class, move student to GraduatedStudent and delete from Student.
2. for every student, update the collection (even if heldBack).

note; all students in Students table ought to have the same (active) collection, of which there can only be 1. this is a side effect that will indirectly happen if the function is engineered well enough.

atomicity and all-or-nothing are paramount.

no heldBack students should be in graduated. semantically, held back students are meant to remain in the same class whilst their peers move on to the next one. their collectionId still updates, mind you.

delete the promoted students from the students table, after they are moved to graduatedstudent.
ensure that ONLY those at a terminal class (i.e. highest) are moved to graduatedstudent;
being held back doesn't mean the student graduates, it means they remain in the same class whilst their collectionId is updated, just like the rest.

---

**REPORTS PAGE (not MVP)**
include user name in table. use the ID in the records to get names.

* aggregate a list of the userId's in the API response, then feed that list into a user helper that returns the name for each.

---

**home page**
fix top class modal in main page (use similar logic as in performance page)

---

**sidebar adjustment (later)**
simply, only display subjects section when contrasting with original subjectsidebar.

---

**misc**
(none beyond above)

---

