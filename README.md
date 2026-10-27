# Family meal planner

A Claude Code skill that plans your family's meals around your cooking preferences, fills your online grocery cart and/or gives you a list for the physical store, and ends with a parallel cooking plan.

## What you need

- The Claude desktop app (Code tab).
- Optional: an online grocery store connected to Claude, e.g. through an MCP server. Currently only tested with Picnic. Without one, you get a shopping list for the physical store and no price estimates.

## Setup

1. Clone or download this repo.
2. Copy both templates from `.claude/skills/family-meal-planner/templates/` to the repo root:
   - `cooking-rules.md`: your household and cooking preferences.
   - `staples.md`: items you always keep on hand.
3. Fill them in with your preferences.
4. Open the repo folder in the Code tab and ask Claude what to cook, for a meal plan, for a shopping list, or to fill your grocery cart.
