# Visual gap checklist

Fill this in before editing a screen. One line per difference is enough.

## Screen

- Source screen:
- Design reference:
- Rendered evidence: screenshot, prototype, or file and line range.

## Composition

- What does the user see first?
- What should the user see first in the design?
- Which large regions must shrink, grow, move, or disappear visually?
- Which source regions are cards, and which should become open layout?
- Which design regions are cards, tiles, borders, or quiet groups?

## Controls

- List every source action.
- Mark where that same action appears in the design.
- If the design omits it, keep it and assign the closest matching visual treatment.
- Do not remove an action to make the screen cleaner.

## Style

- Surfaces and emphasis colors.
- Radius and elevation differences.
- Spacing and density differences.
- Text scale and weight differences.
- States that need a separate treatment: selected, pressed, disabled, empty, loading, error.

## Acceptance

The screen is not done when:

- Only hex values changed.
- A user can still describe it as the old layout with new colors.
- A major region in the reference has no corresponding layout change.
- White or dark text remains on the wrong surface.

The screen is done when the same actions are present and a side-by-side comparison shows the same visual hierarchy as the reference.
