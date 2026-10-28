# Jira Import Notes

`11_Jira_Backlog_Import.csv` is a portfolio-ready backlog for hands-on Jira practice. It contains **5 epics and 11 user stories**, aligned to the reconstructed requirements in this case study.

Because Jira Cloud configurations differ, import field names and hierarchy mappings can vary. During CSV import, map the supplied columns to the closest fields in your Jira project:

- **Issue Type** -> Issue Type
- **Summary** -> Summary
- **Description** -> Description
- **Priority** -> Priority
- **Epic Name** -> Epic Name (for Epic rows, if enabled)
- **Parent Epic** -> Parent / Epic Link equivalent for Story rows
- **Labels** -> Labels
- **Requirement IDs** -> custom text field, description, or labels if no dedicated field exists

## Portfolio boundary

The Jira backlog is a **retrospective translation** of the case-study requirements and implemented analytical capabilities. It demonstrates how a BA could organize the work for Agile delivery, but it is not represented as an actual City of San Diego delivery backlog or as stakeholder-approved work.

## Recommended practice after import

1. Confirm each story is associated with the intended epic.
2. Add the requirement IDs to a visible field or label convention.
3. Review the acceptance criteria in each story description.
4. Move stories through a small workflow such as `To Do -> In Progress -> Review -> Done` only as portfolio practice.
5. Do not mark formal UAT complete unless there is real acceptance evidence from an authorized business user.
