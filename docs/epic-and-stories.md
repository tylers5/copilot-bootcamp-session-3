You are a product development assistant. Update `docs/epics-and-stories.md` by adding technical requirements derived from the acceptance criteria already defined in that file.

Your task:

1. Read the current content of `docs/epics-and-stories.md`.
2. For each story in that file, review the acceptance criteria and derive technical requirements that are necessary to implement the story.
3. Use the current codebase as the source of truth for those technical requirements.
4. Explicitly reference the existing frontend and backend implementation in:
   - `packages/frontend/`
   - `packages/backend/`
5. Base the technical requirements on what the code already does today, what must change to satisfy the acceptance criteria, and where that work belongs.
6. Keep the technical requirements implementation-oriented and concrete.
7. Do not invent features, architecture, endpoints, or storage patterns that are not supported by the current codebase or the acceptance criteria.
8. Preserve existing epic, story, and acceptance criteria content unless a small clarification is required for consistency.

Guidance for technical requirements:

- Call out likely frontend changes when the story affects UI state, forms, display logic, filtering, sorting, or client-side validation.
- Call out likely backend changes when the story affects persistence, API contracts, database schema, server-side validation, filtering, or sorting.
- If a story can be implemented entirely in the frontend or entirely in the backend, say so clearly.
- If the current implementation already partially satisfies the story, note the remaining work rather than restating completed behavior as new work.
- Keep requirements short, specific, and actionable.

Expected output format inside `docs/epics-and-stories.md`:

- Epic and story titles remain in place.
- Each story should include:
  - `Acceptance Criteria`
  - `Technical Requirements`

Example structure:

## Story: <Story Title>

### Acceptance Criteria

- <criterion>

### Technical Requirements

- Update frontend component or state management in the relevant file.
- Update backend API, persistence, or validation in the relevant file if needed.

If `docs/epics-and-stories.md` does not exist, stop and ask for the correct target file before making changes.
