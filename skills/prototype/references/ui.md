# UI Prototypes

Use a UI prototype when the decision is about layout, flow, information
hierarchy, affordances, or interaction feel. Prefer making variants available
inside the real product context so density, navigation, data, and constraints
are visible.

## Shape

1. State the UI question and number of variants.
   - Default to three.
   - Cap at five unless the user explicitly asks for broader exploration.
2. Prefer an existing route or host surface.
   - Keep real data loading, auth, navigation, and shell when safe.
   - Swap only the prototype subtree.
   - Create a new prototype route only when there is no plausible host.
3. Make variants structurally different.
   - Different layout, grouping, scan path, primary action, or interaction
     model.
   - Avoid variants that only change theme, copy, or spacing.
4. Add a visible variant switcher.
   - URL-backed when the app has routing/search params.
   - Keyboard or button controls when simple.
   - Clearly marked as prototype UI.
   - Hidden or removed before production.
5. Cover representative states:
   - Default, empty, loading, error, long text, narrow viewport, and dense data
     when relevant.

## Relationship To Interface Craft

Use `prototype` to explore competing directions before the decision is known.
Use `interface-craft` when the direction is chosen and the task is to design,
redesign, finish, fortify, or critique the actual interface.

When a UI prototype becomes real implementation, switch to `interface-craft`
and apply the normal frontend quality bar: accessibility, responsive behavior,
states, design-system fit, performance, and verification.

## Verification

- Run the app or route.
- Check at least one narrow and one wide viewport when feasible.
- Confirm each variant renders and the switcher does not obscure important UI.
- Record which variant or combination answered the question.

## Promotion

Delete losing variants and the switcher. Rebuild or harden the winner as
production code instead of blindly shipping prototype shortcuts.

## Anti-Patterns

- Isolated mock pages when an existing product surface would reveal more.
- Three card-grid variants with different colors.
- Shared layout abstractions that prevent variants from disagreeing.
- Real destructive mutations from a throwaway prototype.
- Leaving prototype routes or switchers in production bundles.
