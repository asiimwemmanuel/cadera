THINKING

--- reports ---
add a warning at report generation, to ensure all data is complete (NOT mvp)

--- comments ---
check subject comment dtos, ensure consistency (works tho)
don't load main modal if there is no selected subject
generate a new commentId if it's a new comment.

--- promotions ---

1. if in terminal class, move student to GraduatedStudent and delete from Student.
2. for every student, update the collection (even if heldBack).

REPORTS PAGE (not MVP):
include user name in table. use the ID in the records to get names.

- aggregate a list of the userId's in the API response, then feed that list into a user helper that returns the name for each.

note; all students in Students table ought to have the same (active) collection, of which there can only be 1. this is a side effect that will indirectly happen if the function is engineered well enough.

atomicity and all-or-nothing are paramount.

no heldBack students should be in graduated. semantically, held back students are meant to remain in the same class whilst their peers move on to the next one. their collectionId still updates, mind you.

delete the promoted students from the students table, after they are moved to graduatedstudent.
ensure that ONLY those at a terminal class (i.e. highest) are moved to graduatedstudent;
being held back doesn't mean the student graduates, it means they remain in the same class whilst their collectionId is updated, just like the rest.

--- home page ---
fix top class modal in main page (use similar logic as in performance page)
