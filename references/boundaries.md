# Restyle boundary checklist

Use this before editing and again before delivery.

## Keep unchanged

- Navigation destinations, route arguments, back stack behavior, and deep links.
- Click handlers, enabled and disabled conditions, validation, and error states.
- Data loading, pagination, refresh, caching, and empty-state triggers.
- Permissions, privacy flows, analytics, ads, and feature flags.
- Animation durations, easing, repeats, and the conditions that start them.
- Existing drawable, font, Lottie, audio, and video assets.
- User-facing copy, except where the design reference provides text and the user explicitly asks for that text.

## Required visual changes

- Rebuild screen composition when the reference changes hierarchy, grouping, size, or reading order.
- Change containers between filled blocks, bordered cards, tinted tiles, and open layout.
- Move an existing control to the reference position without changing its action.

## Safe visual changes

- Semantic colors, component colors, borders, opacity, and contrast.
- Spacing, sizing, radius, alignment, and elevation.
- Replacing a dark filled treatment with a light surface treatment when the same control remains.
- System-bar icon brightness for the new background.
- Temporary previews or screenshots outside the source tree.

## Stop and ask

- The design removes a source action with no obvious visual equivalent.
- Matching the layout requires changing a public component signature or state model.
- A contrast fix appears to require a new image asset.
- The source has platform-specific dark and light resources, and it is unclear whether both should converge.
- The requested git destination is not clean or the requested revision cannot be checked out.

## Review test

For each diff hunk, answer:

1. Does this change a user action or only its presentation?
2. Does the same asset and animation still run under the same condition?
3. Will text remain readable on the new surface?
4. Can this be reverted without changing behavior?

If any answer is uncertain, narrow the edit before continuing.
