# Cookbook

## Nutrition

Nutrition values shown in the app are **calculated, not hard-coded**. They're
computed live from each recipe's ingredients, so editing an ingredient's
`amount` in `recipes.json` automatically recalculates the nutrition shown —
no number needs to be updated by hand.

Two files work together:

- **`products.json`** — a flat catalog of foods. Each entry has an `id`, a
  `name`, nutrition `per100` (calories/protein/carbs/fat per 100 g or 100 ml —
  matching whichever unit the ingredient uses), and a `brand` (`null` for a
  generic/typical estimate, or a brand name once real packaging values are
  known for that product).
- **`recipes.json`** — ingredients reference a catalog entry via `foodId`.
  Ingredients with no meaningful calories (salt, herbs, water) simply omit
  `foodId`.

For each recipe, per-serving nutrition = sum of every ingredient's
`amount × (per100 / 100)`, divided by `baseServings`. `pcs`-unit ingredients
convert through `piece.grams` first. The app shows a line under the
nutrition box saying whether the numbers are fully generic, fully from real
products, or a mix (e.g. "3/9 ingredients ... + generic estimates for the
rest") — so partial real-product data (req. 1) is always visible.

**To plug in a real product's numbers:** give the per-100g/ml calories,
protein, carbs and fat from the packaging for a specific ingredient. That
entry in `products.json` gets `brand` set and `per100` updated (or a new
entry is added and the ingredient's `foodId` is pointed at it).

**When a product changes** (e.g. switching cottage cheese brands): just
edit that catalog entry's `per100`/`brand` in place. Every recipe using it
recalculates automatically — no history is tracked, since only the
currently-used product matters for the numbers shown.
