# Create Mode

Use create mode for net-new UI generation: pages, app shells, dashboards,
landing pages, components, flows, and branded surfaces.

Create mode must produce an interface that looks intentionally designed, not
merely functional.

## Creation Contract

Before writing UI code, commit to:

- `Surface`
- `Register`
- `Variance`
- `Density`
- `Motion`
- `Composition strategy`
- `Type strategy`
- `Palette strategy`
- `Spacing strategy`
- `Asset/media strategy`
- `State strategy`
- `Visual commitment`
- `Verification plan`

Do not code before these decisions are named unless the change is tiny.

## Dials

### Variance

- `1-3`: conventional, symmetric, predictable, low risk.
- `4-7`: offset composition, varied rhythm, selective overlap, more editorial
  hierarchy.
- `8-10`: asymmetry, unusual grids, bold negative space, art direction, strong
  visual identity.

High variance must collapse aggressively on mobile.

### Density

- `1-3`: airy, gallery-like, generous section rhythm.
- `4-7`: standard product or marketing density.
- `8-10`: operational cockpit, compact rows, tabular numbers, fewer cards, more
  dividers.

High density requires stronger grouping, typography, and scanning support.

### Motion

- `1-3`: no automatic animation; hover, focus, and active states only.
- `4-7`: purposeful transitions and small reveals.
- `8-10`: choreographed motion only when the surface can justify it.

Motion must serve continuity, feedback, explanation, or atmosphere. Respect
reduced motion.

## Composition Strategies

Pick one primary strategy before coding:

- App shell with strong navigation and work canvas.
- Editorial split.
- Asymmetric hero with supporting object or media.
- Dense operational dashboard.
- Bento with mathematically intentional spans.
- Timeline or process flow.
- Immersive brand scene.
- Form-first conversion flow.
- Comparison or pricing architecture.
- Content or index surface.
- Detail page with primary object and supporting metadata.

Do not default to centered hero plus three equal cards unless that is explicitly
the best fit.

## Anti-Slop Replacements

If you reject a generic pattern, replace it with a specific alternative.

| Avoid | Replace with |
| --- | --- |
| Centered hero plus three cards | Split hero, editorial hierarchy, or asymmetric proof section |
| Purple-blue AI gradient | One restrained accent with coherent neutrals |
| Generic cards everywhere | Dividers, grouped rows, panels only where elevation matters |
| Fake round metrics | Organic realistic data |
| Placeholder names | Contextual names and entities |
| Decorative icons | Icons that clarify action, state, or category |
| Stock-looking empty media | Project assets, generated assets, SVG primitives, or honest placeholders |
| Motion for coolness | Motion for continuity, feedback, reveal, or brand atmosphere |

## Content Rules

Use realistic content. Avoid `Acme`, `John Doe`, `Jane Doe`, `99%`, `1234567`,
and generic slogans like `seamless`, `unlock`, `elevate`, or `next-gen` unless
the user provided them.

Use messy, believable values where fake data is necessary.

## Dependency Rules

Before importing third-party UI, animation, icon, chart, or styling libraries,
inspect the project dependencies.

Prefer Tailwind for styling when the project already has Tailwind configured or
the user asks for Tailwind. Use local tokens, components, and utility patterns
through Tailwind classes instead of introducing parallel CSS systems.

If the dependency is missing, either:

- use existing project primitives,
- write a dependency-free version, or
- clearly state the install command and why the dependency is worth it.

Do not assume React, Next.js, Framer Motion, GSAP, shadcn/ui, or a specific
icon library unless the project already uses it or the user requested it. Do
not add Tailwind to a project that uses another styling system unless the user
requested Tailwind or the change includes the necessary setup.

## Build Passes

1. Structure: semantic layout, landmarks, headings, controls.
2. Visual system: type, color, spacing, rhythm, density.
3. Content: realistic copy, data, labels, empty states.
4. States: hover, focus, active, disabled, loading, empty, error, success where
   relevant.
5. Responsiveness: narrow, medium, wide.
6. Motion/media: purposeful, performant, reduced-motion safe.
7. Cleanup: no unused imports, dead placeholders, broken assets, or generic
   scaffolding.

## Verification

At minimum verify:

- Primary job is obvious.
- Visual commitment is visible in the result.
- No centered-hero, three-card, or default-gradient slop unless justified.
- Narrow layout preserves priority.
- Wide layout does not look stretched or empty.
- Interactive states exist.
- Loading, empty, and error states exist where relevant.
- Contrast, focus, keyboard, and touch targets are acceptable.
- No unverified dependency imports.
- No broken images or placeholder copy unless accepted.

## Output

- `Create preflight`
- `Design decisions`
- `Implementation summary`
- `State coverage`
- `Responsive verification`
- `Remaining risks`
