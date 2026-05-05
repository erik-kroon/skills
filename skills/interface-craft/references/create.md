# Create Mode

Use create mode for net-new UI: pages, app shells, dashboards, components,
flows, landing pages, and brand surfaces.

Create mode should make the interface feel specific, usable, and composed. It
should not automatically make the surface louder, more decorative, or more
experimental.

## Creation Contract

Before writing UI code, identify:

- `Surface`: product, brand, hybrid, or unknown.
- `Register`: quiet, standard, or expressive.
- `Primary job`: what the user should accomplish first.
- `Composition`: app shell, form-first flow, dashboard, content surface, detail
  page, comparison, editorial page, or another fitting structure.
- `Reuse`: local components, tokens, assets, icons, and styling conventions.
- `Content`: realistic copy and data, or the exact user-provided content.
- `States`: loading, empty, error, success, disabled, hover, focus, and active
  where relevant.
- `Responsive plan`: narrow and wide behavior.
- `Verification`: browser, screenshot, tests, or stated limitation.

For tiny additions, keep this contract implicit and proceed.

## Register Rules

- `Quiet`: operational products, admin tools, dense dashboards, settings,
  forms, developer tools, and repeated workflows. Use restrained color, clear
  grouping, compact rhythm, and predictable controls.
- `Standard`: most product pages and mixed surfaces. Use a clear hierarchy,
  enough warmth to avoid template feel, and limited expressive moments.
- `Expressive`: campaigns, portfolios, editorial pages, launches, games, or
  brand-first surfaces. Use only when the surface benefits from stronger visual
  identity.

When unsure, choose the quieter register. A precise interface is better than an
overdesigned one.

## Build Passes

1. Structure: semantic layout, landmarks, headings, controls, and navigation.
2. Hierarchy: primary action, scan path, grouping, and density.
3. System fit: reuse local components, spacing, color, typography, and icons.
4. Content: replace placeholders with realistic labels, names, data, and empty
   states.
5. Interaction: hover, focus, active, disabled, loading, empty, error, and
   success states where relevant.
6. Responsiveness: verify narrow and wide layouts without overlap or hidden
   primary actions.
7. Cleanup: remove unused imports, dead placeholders, broken assets, and
   unverified dependencies.

## Pattern Checks

Avoid generic AI defaults, but do not overcorrect into spectacle.

| Weak default | Better replacement |
| --- | --- |
| Centered hero plus three identical cards | Structure that matches the actual job: form, dashboard, comparison, detail, index, or editorial layout |
| Purple-blue glow palette | A restrained palette with one purposeful accent and readable neutrals |
| Cards around everything | Dividers, rows, sections, or panels only where framing helps |
| Fake round metrics | Believable values, labels, ranges, and timestamps |
| Decorative icons | Icons that clarify action, state, category, or object type |
| Motion for visual noise | Motion for feedback, continuity, reveal, or orientation |

## Dependency Rules

Inspect project dependencies before importing third-party UI, animation, icon,
chart, or styling libraries.

If a dependency is missing, either use existing primitives, write a
dependency-free version, or state the install command and why it is worth it.
Do not assume React, Next.js, Tailwind, Framer Motion, GSAP, shadcn/ui, or a
specific icon library unless the project already uses it or the user requested
it.

## Verification

At minimum verify:

- Primary job is obvious.
- Register matches the surface.
- Local design conventions are respected.
- Narrow layout preserves priority.
- Wide layout does not look stretched or empty.
- Interactive and async states exist where relevant.
- Contrast, focus, keyboard path, and touch targets are acceptable.
- No broken images, placeholder content, or unverified dependency imports.

## Output

- `Create mode`
- `Register`
- `Primary job`
- `Implementation summary`
- `State coverage`
- `Responsive verification`
- `Remaining risks`
