# Logic Prototypes

Use a logic prototype when the risk is hidden in state, rules, ordering, or API
shape. The user should be able to drive the model and immediately see what
changed.

## Shape

1. Write the prototype question at the top of the file or in a nearby
   `NOTES.md`.
2. Isolate the decision logic from the interface:
   - Pure reducer for event-driven state.
   - Explicit state machine when legal transitions matter.
   - Plain functions when there is no ongoing state.
   - Small module or class only when the concept genuinely owns internal state.
3. Build the thinnest interactive shell:
   - Terminal loop, CLI prompt, tiny local page, or existing test harness.
   - Render full current state after every action.
   - Show available commands or actions in the same view.
4. Keep state in memory unless persistence is the question.
5. Add one command or documented invocation that starts the prototype.

## Useful Actions

- Add, remove, advance, cancel, retry, reset, import sample, simulate failure,
  toggle flag, change role, and jump to edge case.
- Include actions that are uncomfortable to reason about on paper.
- Prefer representative fixtures over a large fake dataset.

## Verification

- Run the prototype once from the documented command.
- Exercise at least one normal path and one edge path.
- Note surprising behavior or unresolved questions in the final answer or
  prototype notes.

## Promotion

When the answer is useful, keep the validated rule shape and discard the shell.
Production implementation still needs normal tests, input validation, error
handling, and integration with real persistence or services.

## Anti-Patterns

- Mixing terminal prompts, logging, and business logic in one inseparable file.
- Connecting to production data.
- Adding tests for the throwaway shell.
- Generalizing for future scenarios that are not part of the question.
- Treating a prototype reducer or state machine as production-ready just
  because it felt right during exploration.
