# Story: Sort tasks by overdue status priority and due date

## Acceptance Criteria

- Overdue tasks appear before non-overdue tasks.
- Within the same overdue grouping, tasks are ordered by priority from `P1` to `P3`.
- Tasks with due dates are ordered by ascending due date after overdue and priority rules are applied.
- Tasks without due dates appear last.
- This work is treated as Post-MVP.

## Technical Requirements

- Implement task sorting with this precedence: overdue status, priority, due date, undated last.
- Use task `priority` and `dueDate` values to calculate ordering.
- Keep sorting enhancements separate from MVP delivery.