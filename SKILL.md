---
name: ai-native-design-system
description: Build, refine, or apply an AI-native design system for an existing product UI. Use when the user asks to create, optimize, audit, or evolve design tokens, DESIGN.md, showcase pages, or to design/modify product UI after a design system already exists and must be followed.
---

# AI Native Design System

## Purpose

Use this skill to turn an existing product UI and/or visual references into an AI-native design system that future agents can use consistently.

The output should separate:

- **Tokens**: lock consistency with concrete values.
- **DESIGN.md**: express aesthetic intent, rules, and generation guidance.
- **Showcase**: visually demonstrate the system and component forms with minimal, polished examples.

A component library is a later engineering layer, not part of the default design-system foundation. Build it only when the user explicitly asks for reusable frontend components, and tailor it to the project's framework and conventions.

## Context Modes

Choose the context mode before deciding how much project inspection is needed.

### Concept Mode

Use this when there is no code project yet, or the user is exploring visual direction from references, screenshots, moodboards, product ideas, or verbal descriptions.

In Concept Mode:

- Do not perform project intake.
- Analyze product surface, audience, mood, density, interaction expectations, and visual references.
- Produce direction notes, token drafts, `DESIGN.md` drafts, or showcase prototypes only when requested.
- Do not assume a frontend framework, file structure, or component implementation target.

### Project Mode

Use this when there is an existing codebase and the user wants to create, refine, or apply a design system inside that project.

In Project Mode:

- Perform project intake only to the depth needed for the task.
- Prefer the project's existing framework, styling system, UI libraries, icon libraries, and file organization.
- Do not add new UI frameworks, icon libraries, font packages, animation libraries, or styling systems unless the project already uses them or the user explicitly approves.

## Work Modes

This skill has two work modes. Choose the mode from the user's request and the project state.

### Create / Refine Design System Mode

Use this mode when the user asks to create, rebuild, optimize, audit, or evolve the design system itself, including `DESIGN.md`, tokens, showcase pages, or design-system component foundations.

Follow the Hard Gate and Workflow below before changing design source-of-truth files.

### Apply Existing Design System Mode

Use this mode when the project already has a design system, such as `design/DESIGN.md` and `design/tokens/*`, and the user asks to design, implement, optimize, or modify product UI.

In this mode, the design system is the source of truth. Do **not** invent a new visual direction, palette, spacing rhythm, component style, or interaction language unless the user explicitly asks to evolve the design system.

Before changing UI, do this:

1. Read `design/DESIGN.md`.
2. Read available token files, preferring `design/tokens/tokens.ts`, `design/tokens/tokens.css`, or `design/tokens/tokens.json`.
3. Inspect existing design-system components if present, such as `src/components/design-system/*`.
4. Inspect the target screen/component and nearby UI that already follows the system.
5. Identify which design-system rules apply: color roles, type scale, spacing, radius, shadow, density, motion, touch targets, and platform constraints.

When implementing UI:

- Prefer existing tokens, component variants, and local UI patterns over new one-off styles.
- Use explicit hex/rgba values when the project requires older WebView or embedded runtime compatibility.
- Keep component behavior aligned with the product surface, such as touch-first tablet, mobile, dashboard, or courseware.
- Preserve existing design-system source files unless the user explicitly asks to update them.
- If a needed pattern is missing from the design system, either keep it as a local product-specific exception or ask whether to extend the design system.
- If a local UI improvement reveals a reusable rule, proactively ask at the end whether to sync it back into `DESIGN.md`, tokens, showcase, or component-library code.

Verification in this mode:

- Run the project’s normal checks, such as `npm run lint` and `npm run build`, when available.
- Perform browser-based visual QA only when the user explicitly requests it or the project workflow requires it.
- Confirm the final UI follows the existing `DESIGN.md` and token intent, not just that it compiles.

## Hard Gate

Before creating or changing production design system files in Create / Refine Design System Mode, confirm the product surface and visual direction.

In Apply Existing Design System Mode, do not re-ask for visual direction if the existing design system already defines it. Instead, read and follow the existing design system. Ask only if the user wants to intentionally change or expand the system.

### 1. Product Surface

Ask where the product primarily runs, unless the user has already made it clear.

Examples:

- Website / marketing site
- SaaS dashboard / admin console
- Mobile app
- Tablet app
- Desktop app
- Mini program
- TV / kiosk
- Game / interactive courseware

Do not separately ask for primary interaction mode. Infer it from the product surface and project constraints:

- Mobile, tablet, kiosk, and courseware imply touch-first.
- Website and dashboard imply mouse/keyboard with responsive touch support.
- TV implies remote-control or focus-navigation constraints.
- Existing project docs and runtime constraints override generic assumptions.

Do not ask which showcase shape to create by default. The default showcase is a **component foundation showcase**: a polished visual canvas that demonstrates components, states, density, and token usage. Adapt its canvas to the product surface:

- Website: web component foundation canvas.
- SaaS/admin: dashboard component foundation canvas.
- Mobile app: mobile app component foundation canvas.
- Tablet app: tablet app component foundation canvas.
- Game/courseware: interactive stage component foundation canvas.

Other showcase formats are supported only when the user explicitly asks, such as official website showcase, real framework component implementation showcase, or design-guidelines/documentation portal.

### 2. Visual Direction

Ask whether the user has visual references.

- If the user has references, ask for the paths, URLs, screenshots, folders, or files, then analyze them.
- If the user has no references, ask for a short verbal description of the desired mood, audience, and product personality.
- In both cases, summarize 1-3 visual directions and ask the user to confirm one direction before building.

Do not skip this gate unless the user has already provided the product surface and visual reference or clearly approved a direction in the current conversation.

## Workflow

### 1. Audit The Current UI

In Concept Mode, skip this step.

In Project Mode, read only enough of the project to safely complete the request.

For design-system creation, refinement, or screen-level UI work:

- Read `package.json` to identify framework, build scripts, UI libraries, icon libraries, styling tools, and useful verification commands.
- Locate routing and page structure, such as `src/pages`, `src/features`, `src/routes`, `src/App.tsx`, `app/`, `pages/`, `src/views`, or `pages/`.
- Locate styling sources, such as global CSS, Tailwind config, CSS modules, theme files, or existing token files.
- Locate reusable UI, such as `src/components`, `src/components/ui`, `src/components/design-system`, or framework-specific component folders.
- Inspect representative pages, especially entry/home flows and screens the user already likes.
- Inventory existing colors, typography, spacing, radius, shadows, density, and motion patterns.
- Check platform constraints such as mobile, tablet, WebView, accessibility, or touch-first requirements.

For tiny UI edits, do the smallest useful inspection: read the target component, nearby patterns, and relevant design rule or token.

### 2. Gather Visual Direction

Use the confirmed product surface to interpret the references. A design system can have different presentation forms; do not force every system into a website-like showcase.

Ask the visual-reference question after product surface is known.

If references exist:

- Read local HTML, screenshots, design files, or reference folders when available.
- Extract spacing, type hierarchy, radius, shadow, information density, motion style, layout traits, and color roles.
- Distinguish what to borrow from what to avoid. Do not copy a reference literally.

If references do not exist:

- Ask concise questions about tone, audience, and examples in words.
- Convert the user's description into 1-3 named visual directions.

Then confirm the selected direction with the user before implementation.

### 3. Apply To Product UI

When modifying real product UI, use the lightest process that can safely complete the task.

#### Tiny UI Edit

Use for copy, spacing, color, one button, one small state, or a narrowly scoped component adjustment.

- Read the target component and the nearest relevant design rule, token, or nearby UI pattern.
- Make the change without broad redesign.
- Run the smallest useful verification.

#### Screen-Level UI Edit

Use for layout, hierarchy, component composition, responsive behavior, or multiple interaction states on one screen.

- Read `DESIGN.md`, available tokens, the target screen, and nearby UI that already follows the system.
- Understand the user task on that screen. Visual hierarchy should follow task priority, not decoration.
- Preserve existing behavior, data flow, route structure, and accessibility semantics unless the user asked to change them.
- Improve in this order: information architecture, layout and spacing, component hierarchy, interaction states, color polish, then motion.
- Ensure relevant interactive elements have visible default, active/pressed, disabled, loading, and focus states.

#### System-Level UI Edit

Use for tokens, `DESIGN.md`, showcase, reusable components, multiple screens, or visual direction changes.

- Use the full design-system workflow.
- Confirm direction or sync decisions when source-of-truth files change.
- Do not silently promote local product-specific styles into the design system.

For all implementation depths:

- Prefer existing project components, tokens, and local patterns before adding one-off styles.
- Use local one-off styles only when the pattern is truly screen-specific.
- If a repeated local pattern emerges, ask whether to promote it into tokens, `DESIGN.md`, showcase, or reusable components.
- Do not introduce a new visual direction for one page.
- Do not redesign unrelated areas just because they are nearby.
- For touch-first or embedded products, avoid hover-only interactions and keep core touch targets at least 44px.

### 4. Handle Design Debt

For existing products with inconsistent legacy UI:

- Do not rewrite the entire product unless requested.
- New or touched surfaces should follow the design system.
- Legacy screens can be migrated gradually.
- When old styles conflict with the design system, prefer scoped adaptation first.
- Record reusable decisions in `DESIGN.md` only after user confirmation.

### 5. Define The Architecture

Use this default structure unless the project already has a better convention:

```text
design/
├── DESIGN.md
├── showcase/
│   └── index.html
└── tokens/
    ├── tokens.ts
    ├── tokens.json
    └── tokens.css
```

Place project-specific decisions in the project, not in this skill. If the project needs reference files, put them under the project such as `design/references/` or `design/decisions/`.

### 6. Write Tokens

Create semantic token groups, not just raw palettes:

- `color`: background, surface, text, border, action, status, reward/playful, focus.
- `space`: 4px-based scale with product-specific rhythm.
- `typography`: font family, display/title/section/body/caption levels.
- `radius`: small controls through large panels.
- `shadow`: separate action, HUD, card, panel, modal, and inner shadows.
- `density`: roomy, balanced, compact.
- `motion`: durations, easing, press/float transforms.

Tokens should use explicit hex/rgba values for important visuals, especially when Android WebView or embedded runtimes matter.

### 7. Write DESIGN.md

Make `DESIGN.md` readable by future AI agents.

Cover:

- Visual theme and atmosphere.
- Color intent and color proportions.
- Typography rules.
- Spacing system.
- Radius system.
- Shadow rhythm.
- Information density.
- Motion style.
- Layout patterns.
- AI generation rules.

Use natural design language plus exact values where they matter. Explain why each choice exists.

Use `references/DESIGN-md-example.md` as the structural reference. It is modeled after the strong part of a token/design-intent handoff: visual theme, color roles, typography rules, component styling, layout principles, depth, Do/Don't, responsive behavior, agent prompt guide, and iteration audit guide.

### 8. Represent Base Components In Showcase

Create or refine a small visual proof set first:

- Button
- Input
- Card

Represent these as HTML/CSS examples in the standalone showcase unless the user explicitly asks for an engineering component library. For touch-first products, keep core controls at least 44px tall and include pressed/active feedback.

Do not create `design-system/components.md` by default. Put essential component intent in `DESIGN.md`, and make the concrete visual form visible in `design/showcase/index.html`.

If the user asks to build a component library, create framework-native reusable components that match the design system, such as React/Vue/Svelte components in the project's existing component location.

### 9. Build A Showcase

The showcase should be a polished visual proof, not a long document.

Default to a standalone HTML showcase:

```text
design/showcase/index.html
```

Use a framework route or component showcase only when the user explicitly asks to integrate the showcase into the current frontend, or when the project already has an established design-system route that should be updated.

Default showcase type:

- Build a component foundation showcase by default.
- Match the canvas to the product surface, such as tablet app, mobile app, dashboard, web, or game/courseware.
- For tablet products, do not create a marketing website layout; use a tablet app canvas with component/state groupings.
- For website products, a website-style showcase can be appropriate.
- For documentation-heavy systems, create a guidelines/documentation portal only when requested.
- For existing frontend projects, create real framework component implementation only when the user asks for a component library or integrated component showcase.

If the user says the showcase shape feels wrong or they do not like the current showcase form, pause implementation and offer alternative presentation formats with short explanations:

- **Component Foundation Showcase**: default; compact canvas that displays components, states, density, and token usage.
- **Product Surface Showcase**: a realistic app/screen sample for the product's primary device, such as tablet classroom, dashboard, mobile flow, or courseware stage.
- **Official Website Showcase**: marketing/webpage-style presentation with nav, hero, sections, proof blocks, and CTA; use only for web or brand-site needs.
- **Real Framework Component Showcase**: implemented in the project's frontend framework and importable component layer; use when building a component library.
- **Design Guidelines Portal**: documentation-heavy portal like a design system website; use when the user wants browsable rules and long-form guidance.
- **Token Spec Preview**: token-first page showing palette, type, spacing, radius, shadows, motion, Do/Don't, and AI prompt examples.

Recommend the best alternative based on product surface, but let the user choose before rebuilding the showcase.

For the standalone HTML showcase:

- It should work by opening the file directly when possible.
- Prefer linking or embedding `design/tokens/tokens.css` so the showcase reflects real token values.
- Keep CSS and markup self-contained enough that it can be reviewed before any frontend app exists.
- Treat it as the bridge between `DESIGN.md` and future implementation.

Rules:

- Keep text minimal: short headings, labels, swatches, and component samples.
- Avoid excessive nested containers.
- Prefer one clear page rhythm: header, hero/sample area, component grid, token samples.
- Do not show long token values unless the user asks.
- Do not use decorative gradients, blobs, or large illustrations unless the selected direction calls for them.
- Demonstrate states: default, secondary, reward/success, danger, disabled, loading, input helper/error, cards, density, type, radius, shadow.

#### Showcase Nesting & Layout Rules

To avoid visual noise (such as "Double-Carding" or nested shadow/border noise) in the showcase, enforce the following host container rules for components to ensure compatibility across different color themes:

1. **Atomic / Floating Controls**:
   - *Definition*: Components without an integrated shadow, border, or base panel (e.g., buttons, badges, basic text inputs).
   - *Showcase Rule*: Must be wrapped in a design-system-defined container/card background (e.g., Card/Panel component or system card background token) to provide contrast. Hardcoding specific color values (like white) is strictly prohibited; abstract semantic colors or host components must be used to ensure adaptability across different color themes (e.g., dark mode, theme variants).
2. **Self-Contained / Panel Components**:
   - *Definition*: Components that already include their own background, border-radius, and shadow (e.g., Bento chat input areas, voice input popups, composite content panels).
   - *Showcase Rule*: Follow the "No Double-Shelling" principle; nesting inside other card containers with borders/shadows is strictly prohibited. These must be placed directly on the showcase default App Background Token. Only non-background, non-shadow, non-border layout containers (e.g., width-constrained or centered containers) are permitted for layout assistance.

### 10. Iterate With Taste Feedback & Sync Trigger

When the user critiques the showcase and you finish the visual/code optimization, you **MUST proactively ask the user** whether they want to synchronize and upgrade these adjustments back to the design system's source of truth:

- Concrete values go to tokens.
- Aesthetic rationale and generation rules go to `DESIGN.md`.
- Visual proof go to the showcase.
- Component-library behavior goes to reusable frontend components only when a component library exists or the user asks to create one.

Never silently synchronize design source-of-truth files without explicit user confirmation, but always proactively suggest the sync checklist at the end of your execution turn to ensure two-way alignment.

Keep project-specific preferences in the project files, not in this skill.

### 11. Verify

Run the project’s available non-visual checks before declaring completion.

Typical checks:

```bash
npm run lint
npm run build
```

Also validate token JSON when present:

```bash
python3 -m json.tool design/tokens/tokens.json
```

Do a code-level visual risk review:

- obvious overflow risks
- hover-only interactions
- missing active/focus/disabled/loading states
- unsupported CSS for the target platform
- token drift
- newly introduced one-off styles
- layout choices likely to clip text or controls
- showcase nesting alignment (atomic controls sit on system-themed container backgrounds; self-contained components avoid double-carding without hardcoded colors)

Browser-based visual QA is optional and user-triggered. Do not automatically open browsers, take screenshots, or run multi-viewport visual inspection unless the user explicitly requests it or the project workflow requires it.

When the user explicitly requests visual QA:

- Open the affected page or showcase when possible.
- Check the requested viewport or device targets.
- Inspect overlap, clipping, text overflow, color rendering, interaction states, and asset/media rendering.
- Report concrete visual findings and fixes.

If browser-based visual QA was not performed, say so clearly in the final response.

## Output Summary

In the final response, mention:

- Files created or changed.
- The selected visual direction.
- The core token decisions.
- Verification commands and results.
- Any warnings that pre-existed or remain.
