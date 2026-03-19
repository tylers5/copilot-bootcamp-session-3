# Story: Exclude completed tasks from Today and Overdue views

## Acceptance Criteria

- Completed tasks remain visible in the `All` view.
- Completed tasks do not appear in the `Today` view.
- Completed tasks do not appear in the `Overdue` view.

## Technical Requirements

- Preserve existing completed-task visibility in the `All` view.
- Update `Today` and `Overdue` filtering logic to include only incomplete tasks.
