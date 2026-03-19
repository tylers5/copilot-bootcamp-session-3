# Product Requirements Document (PRD) - Todo App Upgrade

## 1. Overview

The current Todo app is very basic and only supports a task title and completed status. This upgrade is intended to make the app more useful without adding unnecessary complexity. The confirmed MVP adds optional due dates, task priorities, and simple date-based filters while keeping storage local and avoiding backend changes. Follow-up enhancements such as overdue highlighting and sorting are intentionally deferred to Post-MVP.

---

## 2. MVP Scope

- Add an optional `dueDate` field to each task.
- Store `dueDate` using ISO `YYYY-MM-DD` format.
- Add a `priority` field with enum values `P1`, `P2`, and `P3`.
- Default `priority` to `P3` when a value is not provided.
- Support filter views for `All`, `Today`, and `Overdue` tasks.
- Show completed tasks in the `All` view.
- Exclude completed tasks from the `Today` and `Overdue` views.
- Keep task storage local only.
- Do not make backend changes for MVP.
- Validate task data with these rules:
	- `title` is required.
	- `priority` must be one of `P1`, `P2`, or `P3`.
	- `dueDate` is optional.
	- Invalid `dueDate` values should be ignored and treated as absent.

---

## 3. Post-MVP Scope

- Visually highlight overdue tasks so they stand out in the task list.
- Add sorting rules in this order:
	- overdue tasks first
	- then by priority from `P1` to `P3`
	- then by due date ascending
	- tasks without a due date last

---

## 4. Out of Scope

- Notifications
- Recurring tasks
- Multi-user functionality
- Keyboard navigation
- External storage