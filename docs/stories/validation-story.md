# Story: Validate due date and priority values

## Acceptance Criteria

- Task title is required.
- Priority values are limited to `P1`, `P2`, and `P3`.
- `dueDate` remains optional.
- Invalid `dueDate` values are ignored and treated as absent.

## Technical Requirements

- Validate required task data before saving locally.
- Reject or normalize invalid priority values so only `P1`, `P2`, and `P3` are stored.
- Treat invalid `dueDate` values as missing instead of persisting malformed data.
