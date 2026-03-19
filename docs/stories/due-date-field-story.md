# Story: Add due date field to tasks

## Acceptance Criteria

- Tasks support an optional `dueDate` field.
- `dueDate` values use ISO `YYYY-MM-DD` format when present.
- Users can create a task without providing a due date.

## Technical Requirements

- Extend the task data model to include an optional `dueDate` field.
- Support creating and updating tasks with a `dueDate` value.
- Preserve the `dueDate` value in local task storage.
