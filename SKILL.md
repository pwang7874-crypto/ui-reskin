---
name: ui-reskin
description: Rebuilds the visible layout of an existing app from a git URL or local source so it matches a supplied design, while preserving routes, behavior, animations, assets, and interactions. Use when a redesign looks too small or a token-only recolor would not reproduce the reference.
compatibility: Windows, macOS, and Linux. Works with Pi, Codex, Claude Code, Grok, DeepSeek, and other Agent Skills clients. Requires git and a browser only when cloning or rendering an HTML prototype.
---

# Visual Restyle

Rebuild the visible screens so they clearly match the reference. Do not change what the product does.

A token swap is not a completed restyle. If a screenshot of the result still has the source layout, hierarchy, or emphasis, the work is incomplete.

The user may provide either a git URL or a local source directory, plus screenshots, an HTML prototype, or another design reference. Read this file completely before editing.

Use the current operating system's normal shell and path syntax. Do not hard-code a user profile, drive letter, or agent-specific tool name. Use the host agent's file, shell, and editing tools.

## Outcome

- A separate working copy contains the restyle. Never edit the original checkout in place.
- Routes, click handlers, state transitions, data flow, permissions, analytics, ads, and business rules stay intact.
- Existing images, icons, fonts, Lottie files, and motion timings stay unless the design reference explicitly replaces a visual asset.
- The result is committed only when the user asks. Push only after a separate confirmation.

## 1. Collect the two inputs

Identify:

- Source: git URL plus branch, tag, or commit; otherwise a local project path.
- Design: local prototype, screenshots, or a written visual spec.
- Destination: a new sibling directory. Never reuse `build`, `.gradle`, `.git`, or cache directories from the source when copying.

If the design reference is missing, inspect the source first but do not invent a new visual system. Ask for the reference.

Resolve `git` from `PATH`. If it is unavailable, look for an existing user-specific Git installation and use its absolute path only for this run. Do not install Git or change global Git configuration unless the user asks.

```bash
git clone --branch <ref> --single-branch <url> <destination>
```

On Windows, if checkout reports `Filename too long`, enable `core.longpaths` for that repository and check out the required paths. On macOS or Linux, preserve executable permissions and symlink behavior. Confirm the requested branch and commit before editing.

## 2. Lock the behavior

Before changing visuals, record the existing behavior from source:

- App entry, navigation graph, back behavior, and tab structure.
- Screen list and the action available on each screen.
- Existing animations and the state that triggers them.
- Asset directories and which screens use them.
- Theme, color, type, and system-bar files.

Use [references/source-map.md](references/source-map.md) for the Android/Compose layout used by Vela Browser. For another technology, map the equivalent files first; do not assume this repository layout.

The lock is a short working note, not a new product spec. It exists to prevent later edits from drifting into behavior changes.

## 3. Read the design

Extract a visual contract before editing code:

- Page background, card surface, text, border, brand, pressed, and status colors.
- Radius, spacing, elevation, and control heights.
- What the design emphasizes first on each screen.
- Which source elements are only restyled and which are intentionally omitted.

Treat the design as the visual target, not as permission to remove source functionality. If the design omits a source feature, keep the feature and give it the new visual treatment.

Open an HTML prototype in a browser when possible. A headless screenshot is useful, but the implementation still comes from the prototype's actual layout and tokens.

## 4. Compare the rendered screens

Open or render the design and inspect the source screen. For every major screen, write a gap list before editing:

- First focal point and reading order.
- Elements present, hidden, combined, or resized.
- Container treatment: open page, card, tinted tile, divider, or border.
- Density, alignment, radius, and spacing.
- Color role: brand action, selection, information, or decoration.

Use [references/visual-gap.md](references/visual-gap.md). A gap such as "large hero title becomes one quiet brand line" requires a layout change, not a recolor.

## 5. Rebuild the presentation

Change shared tokens first, then rebuild the visible composition of each major screen. Layout, hierarchy, and component structure are in scope when they do not change behavior.

Work in this order:

1. Set the new theme, surfaces, type scale, and system-bar contrast.
2. Restyle shared controls so the new language is consistent.
3. Rebuild each major screen's composition: order, grouping, sizes, containers, and emphasis.
4. Preserve every source action, but move or restyle it to the reference treatment.
5. Fix contrast and states such as pressed, selected, disabled, empty, loading, and error.

Do not stop after step 1 or 2. The result must be visibly different in structure where the reference differs, while every original action remains reachable.

## 6. Edit within the behavior boundary

Allowed:

- Color, typography, spacing, radius, borders, elevation, alignment, and visual hierarchy.
- System-bar appearance when the new background requires it.
- Layout changes that make the same controls follow the design.

Not allowed without an explicit user request:

- Adding, removing, reordering, or renaming user-facing actions.
- Changing navigation destinations or arguments.
- Changing animation duration, easing, or trigger conditions.
- Replacing or regenerating image, icon, font, or Lottie assets.
- Editing ViewModels, repositories, network code, storage, permissions, analytics, or ads for a visual task.

When a contrast problem comes from an asset rather than code, keep the asset and adapt its container. Do not redraw it.

Use [references/boundaries.md](references/boundaries.md) while reviewing every changed file.

## 7. Verify visually

Compare the working copy against the untouched source:

- Every changed file must be visual, plus the temporary working note if one was intentionally kept.
- Search changed UI code for navigation calls, state mutations, and business conditions. They should match the source except for purely visual arguments.
- Check light backgrounds for white or low-contrast text left over from the old theme.
- Check branded buttons and dark overlays for text that must remain light.
- Run the project's normal compile command when it is practical. If it cannot run, say exactly what was not verified.

## 8. Deliver

Report:

- Working copy path and source revision.
- Design reference used.
- Visual changes by screen or shared component.
- Behavior and assets intentionally preserved.
- Verification performed and anything not run.

Commit or push only when the user asks. Before committing, inspect the repository identity and recent authors. Never borrow another author's name or email. If the user's identity is not configured, ask before creating the commit.

