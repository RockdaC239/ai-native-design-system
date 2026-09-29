# Product AI Native Design System

`tokens` lock consistency. `DESIGN.md` explains aesthetic intent, usage boundaries, and AI generation rules. Future agents should read this file before generating UI, then use `design/tokens` for exact values and `design/showcase/index.html` for visual proof.

## 1. Visual Theme & Atmosphere

Describe the product as a lived interface, not as a color list.

- What category is this product in?
- Who uses it, and in what environment?
- What emotional state should the UI create?
- What should lead: content, product imagery, data, character, task, or component interaction?

Example structure:

> This product should feel like [metaphor grounded in the domain]. It should be [3-5 traits], but never [2-3 anti-traits].

Key characteristics:

- Primary surface rhythm.
- Signature color move.
- Signature type move.
- Signature interaction move.
- Density and spacing personality.
- Strongest non-goals.

## 2. Color Palette & Roles

Define colors by job, not by visual preference.

### Primary Brand

- **Primary Anchor** (`#000000`): where it appears, how often, and what it signals.
- **Primary Action** (`#000000`): main CTA, selected state, active route, or core task.

### Secondary & Accent

- **Interaction Accent** (`#000000`): hover, focus, pressed, reward, or motion-only use.
- **Support Accent** (`#000000`): secondary signal or temporary emphasis.

### Surfaces & Backgrounds

- **App Background** (`#000000`): default page/app canvas.
- **Surface Default** (`#000000`): cards, panels, sheets.
- **Surface Raised** (`rgba(...)`): floating or elevated surfaces.
- **Divider / Border** (`#000000`): quiet separation.

### Text & Neutrals

- **Text Strong** (`#000000`): titles and primary labels.
- **Text Body** (`#000000`): readable body copy.
- **Text Muted** (`#000000`): metadata and helper text.
- **Text Inverse** (`#000000`): text on dark or saturated surfaces.

### Semantic Colors

- Success, warning, error, info, reward, disabled.
- Explain when each can appear and what it must not replace.

### Gradient Rules

If gradients exist, state exactly where they are allowed.

- Allowed: section backgrounds, hero atmosphere, data visualization, or none.
- Not allowed: gradient buttons, gradient text, decorative blobs, or other banned cases.

## 3. Typography Rules

Explain the voice of the type system.

### Font Family

- Primary family and fallback.
- Why it fits the product.
- Whether display and UI use different weights.

### Hierarchy

| Role | Size | Weight | Line Height | Use |
| --- | --- | --- | --- | --- |
| Display | 40px | 900 | 46px | Major moment |
| Title | 32px | 900 | 38px | Page title |
| Section | 24px | 800 | 30px | Panel title |
| Body | 16px | 500 | 24px | Default reading |
| Caption | 12px | 700 | 16px | Metadata |

### Principles

- Which weights are part of the product voice.
- Whether labels use sentence case, title case, or uppercase.
- Letter-spacing rule.
- Body copy length and line-height rule.

## 4. Component Styling

Describe components by state and role.

### Buttons

Primary:

- Background, text, border, radius, padding, height.
- Hover/focus/pressed/disabled/loading states.
- Motion duration and transform.
- What kinds of actions can use it.

Secondary:

- How it differs from primary.
- Whether it can sit next to primary.

Destructive / reward / special variants:

- Exact semantic boundaries.
- Forbidden uses.

### Inputs & Forms

- Default field treatment.
- Focus ring.
- Error message style.
- Helper text style.
- Compact vs touch-first sizing.

### Cards & Panels

- Default card.
- Raised panel.
- Feature card.
- Empty/loading/error states.
- Padding and radius by hierarchy.

### Navigation / Status / HUD

If the product uses persistent status elements, define:

- What status belongs there.
- Where it appears.
- How dense it can be.
- How it responds on smaller devices.

## 5. Layout Principles

### Spacing System

- Base unit.
- Common rhythm values.
- Section padding.
- Card padding.
- Inline spacing.
- Micro spacing.

### Grid & Container

- Product surface and primary viewport.
- Max width or device frame.
- Column patterns.
- Outer padding.
- Breakpoint strategy.

### Density

Define density tiers:

- Roomy: who it is for and when to use it.
- Balanced: default product density.
- Compact: admin/editor/data-heavy cases only.

## 6. Radius System

List radius values by role:

- Small utility.
- Inputs.
- Buttons.
- Cards.
- Main panels.
- Pills / circular controls.

Explain why multiple radii exist and what hierarchy they express.

## 7. Depth & Elevation

Define a small elevation ladder.

| Level | Treatment | Use |
| --- | --- | --- |
| 0 | none | Flat surfaces |
| 1 | subtle shadow | Standard card |
| 2 | medium shadow | Main panel |
| 3 | action depth | Primary/reward action |
| 4 | modal shadow | Dialog/sheet |
| Focus | ring | Keyboard/touch focus |

Explain whether the system is flat, tactile, dramatic, glassy, or toy-like. State where shadows must not be used.

## 8. Motion Style

Define motion as product behavior, not decoration.

- Press feedback.
- Hover behavior.
- Page/sheet/dialog entrance.
- Loading state.
- Ambient motion if allowed.
- Reduced-motion rule.

## 9. Do's and Don'ts

### Do

- Use the primary color for core actions.
- Preserve the declared type hierarchy.
- Use exact radius and shadow tiers.
- Keep density aligned with the product surface.
- Use showcase and tokens as the visual source of truth.

### Don't

- Add colors outside the token roles.
- Invent gradients or decorative effects not approved here.
- Use the wrong showcase form for the product surface.
- Replace touch-first sizing with desktop-only controls.
- Mix multiple surface rhythms in one screen.

## 10. Responsive / Device Behavior

Describe behavior by product surface.

- Mobile: stacking, minimum touch size, bottom actions.
- Tablet: canvas/frame, side panels, large touch targets.
- Desktop/dashboard: columns, sidebars, keyboard/mouse affordances.
- TV/kiosk: focus states, remote navigation, distance readability.

## 11. Agent Prompt Guide

### Quick Role Reference

- Primary action:
- Primary background:
- Surface:
- Text strong:
- Border:
- Reward/accent:
- Focus:

### Example Component Prompts

1. "Create a primary CTA with [color], [height], [radius], [shadow], [font], and [pressed state]."
2. "Create a standard card with [surface], [padding], [radius], [shadow level], and [title/body hierarchy]."
3. "Create an input field with [border], [focus ring], [helper text], and [error state]."
4. "Create a product-surface showcase section for [device], using [density], [tokens], and [component states]."

## 12. Iteration Audit Guide

When refining generated UI:

1. Audit color roles: every color must map to a declared role.
2. Audit type: display, title, body, and caption must use declared sizes and weights.
3. Audit radius: every container should land on the radius scale.
4. Audit shadow: every shadow should land on the elevation ladder.
5. Audit density: product surface must match the user/device context.
6. Audit states: components must include hover/focus/pressed/disabled/loading/error where relevant.
7. Audit showcase form: if the user dislikes the current form, offer alternate showcase formats before rebuilding.
