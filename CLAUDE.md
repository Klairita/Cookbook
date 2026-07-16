# Repository instructions

## Merging pull requests

Never merge a pull request as part of the same request that opened it or
asked for other changes. Merging requires a separate, explicit confirmation
message from the user after the PR is open (e.g. "yes, merge it") — a
request like "make this change and merge it" is not sufficient on its own.
Always open/update the PR, then stop and wait for that separate confirmation
before calling the merge tool.

## Recipe tags

Every recipe in `recipes.json` must include at least one meal-type tag from
this fixed set: `Breakfast`, `Lunch`, `Dinner`, `Snack`, `Dessert`,
`Ice Cream`. A recipe may have more than one if it fits multiple (e.g. a
snack that's also a dessert). Beyond these meal-type tags, feel free to add
other descriptive tags (ingredients, cuisine, diet, prep time, etc.) as
appropriate — there are no fixed rules for those.

## Recipe language

The cookbook is English-only. If a source recipe (text, screenshot, etc.) is
in another language, translate the name, description, ingredients and steps
to English before adding it to `recipes.json` — don't leave any part in the
original language.
