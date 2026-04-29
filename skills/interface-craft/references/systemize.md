# Systemize Mode

Use systemize mode to turn repeated interface decisions into reusable system
assets.

## Look For

- Repeated component structures.
- Repeated spacing, color, radius, shadow, or motion decisions.
- Repeated empty, error, loading, success, and permission states.
- Inconsistent variants that should be one component.
- Local primitives that belong in the design system.
- Repeated copy patterns that need a content convention.

## Workflow

1. Discover repeated patterns and name their differences.
2. Choose what should become reusable.
3. Define the component API, token, or content convention.
4. Migrate the smallest useful set of call sites.
5. Document intended use where the repo already documents design decisions.

## Output

- `Candidates`
- `Systemization plan`
- `New or changed system assets`
- `Migrated usage`
- `Follow-up candidates`
