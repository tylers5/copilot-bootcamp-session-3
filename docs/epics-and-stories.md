# Todo Upgrade Epics And Stories

## Technical Context

### Frontend Package

- The frontend is a React application using Material UI components.
- The main workflow is split across `App`, `TaskForm`, and `TaskList`.
- `App` submits task creates and updates through `fetch` calls to `/api/tasks` and refreshes the list after writes.
- `TaskForm` already supports `title`, `description`, and `due_date`, and it enforces a required title before submit.
- `TaskList` already fetches tasks from `/api/tasks`, renders due dates, and supports edit, delete, and completion toggling.
- Frontend technical references:
  - `packages/frontend/src/App.js`
  - `packages/frontend/src/TaskForm.js`
  - `packages/frontend/src/TaskList.js`
  - `packages/frontend/src/__tests__/App.test.js`

### Backend Package

- The backend is an Express application backed by an in-memory SQLite database.
- The current `tasks` table includes `title`, `description`, `due_date`, `completed`, and `created_at`.
- The API already supports create, list, detail, update, toggle complete, and delete operations.
- The list endpoint currently supports completion filtering and keyword search, and sorts by due date followed by creation date.
- Backend technical references:
  - `packages/backend/src/app.js`
  - `packages/backend/src/index.js`
  - `packages/backend/__tests__/tasks.test.js`
  - `packages/backend/package.json`

## MVP

### Epic: Task Metadata

#### Story: Add due date field to tasks

- Frontend technical notes:
  - `TaskForm` already captures `due_date` and normalizes values for edit mode.
  - `TaskList` already displays due dates as chips.
- Backend technical notes:
  - The database schema and existing task endpoints already support `due_date`.
  - This story is primarily about keeping the behavior aligned with the PRD and preserving the field through task create and update flows.

#### Story: Add priority field with default P3

- Frontend technical notes:
  - Add priority input handling to `TaskForm`.
  - Render priority in `TaskList` so users can see the assigned value.
- Backend technical notes:
  - Extend the `tasks` table and request handling in the API to persist `priority`.
  - Ensure create and update endpoints default missing priority values to `P3`.

#### Story: Validate due date and priority values

- Frontend technical notes:
  - Keep the existing required-title validation in `TaskForm`.
  - Add validation or normalization for supported priority values and invalid due-date input.
- Backend technical notes:
  - Enforce the same validation rules in create and update endpoints.
  - Treat invalid due-date values as absent, matching the PRD.

### Epic: Date-Based Filtering

#### Story: Add All Today and Overdue filters

- Frontend technical notes:
  - Add filter state and controls near the task list view.
  - Update `TaskList` rendering so the list reflects the selected filter.
- Backend technical notes:
  - Decide whether `Today` and `Overdue` filtering should be handled in the client or exposed through API query support.
  - Preserve the current `/api/tasks` contract if filtering remains frontend-only.

#### Story: Exclude completed tasks from Today and Overdue views

- Frontend technical notes:
  - Reuse each task's `completed` flag when applying `Today` and `Overdue` filters.
  - Keep completed tasks visible in the `All` view.
- Backend technical notes:
  - If filters move server-side, combine date-based rules with the existing `completed` query behavior.

### Epic: Local Data Handling

#### Story: Persist due date and priority locally

- Frontend technical notes:
  - The current frontend depends on the `/api/tasks` API and a local development proxy.
  - If MVP must remain local-only, document whether local persistence means browser storage, the in-memory backend, or both.
- Backend technical notes:
  - The current backend stores tasks only in memory and resets on restart.
  - No external storage should be introduced for MVP.

## Post-MVP

### Epic: Overdue Task Visibility

#### Story: Highlight overdue tasks in the list

- Frontend technical notes:
  - Add visual treatment in `TaskList` based on overdue state.
  - Keep the styling distinct from the existing completed-task styling.
- Backend technical notes:
  - No backend changes are required if overdue state is derived from `due_date` in the UI.

### Epic: Task Sorting

#### Story: Sort tasks by overdue status priority and due date

- Frontend technical notes:
  - If sorting is applied in the UI, it should happen before rendering the task list.
  - Sorting will depend on both `due_date` and the new `priority` field.
- Backend technical notes:
  - The current API sorts by due date and creation date.
  - If sorting moves server-side, update the list query in `app.js` to match the Post-MVP sort order.