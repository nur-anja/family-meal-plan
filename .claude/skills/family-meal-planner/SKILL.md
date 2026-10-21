---
name: family-meal-planner
description: Plan my family's meals and build my online grocery cart following my cooking rules. Use when I ask what to cook, for a meal plan or menu, or to fill my grocery cart.
---

# My meal planning and grocery workflow

Read the cooking-rules.md - it contains personal information about my household and cooking preferences. Take it into account when executing the workflow.

## The workflow

1. In preparation of planning, ask me (unless I already told you in my request): 
    1. How many meals or days I want to cook for, and whether that includes any special occasion days mentioned in cooking rules (Freeform)
    2. Do I have any ingredients that I need to use up (Freeform)
    3. Any cuisine I'm in the mood for (AskUserQuestion)
    4. Any particular recipes or ingredient I'm in the mood for (Freeform)
2. Each meal should contain protein, carbs and veggies. These are nutritional components, not separate dishes: one dish can cover all three (e.g. a stew with chicken, potatoes and carrots, or a pasta bake with lentils and spinach), or a meal can combine a main with sides. For each component, ask me what I want (aside from what I already have and what I've mentioned I'm in the mood for) (ChoicePanel). Make sure we have variety of all three components to cover all meals without too much repetition. 
3. When we're set on components, offer me up to 3 recipes per meal to choose from that fit my rules. (AskUserQuestion - repeat for each meal)
4. You give me the final menu with ingredients listed, price estimation per meal and total cart price as if I have none of the ingredients at home (before adding staples). Ask me if I want to adjust anything. (Freeform)
5. Give me a parallel cooking plan, see Cooking plan section.
6. For pantry staples (oil, salt, spices, condiments) ask me if I'm missing anything. For the rest of the items, ask me if I already have it, or, if I already stated that I have - whether I have enough for your plan. (ChecklistPanel, pantry check mode) After I answer, give me the adjusted total cart price without the items I already have.
7. Ask me if I plan to get any ingredients in brick and mortar store, or order everything from the online store. (AskUserQuestion. If I want to shop in brick and mortar, follow up with a ChoicePanel of the shopping list items, no `max`: which will I buy in store?)
8. Ask me if we need to replenish anything from staples.md. (ChecklistPanel, staples restock mode, one section per group in staples.md)
    1. For checked items marked with *, ask me which flavors/variety I want out of those offered in the online store.
9. After I confirm, you can fill the online store cart, see Ordering from the online store section.
10. If I said I plan to partly shop in brick and mortar store, give me the grocery list to take with me to the store.

## Asking me questions

When the workflow specifies a question, it needs to be asked in correct format. Some questions already specify what format to use, for other use the guidelines below. 
- Freeform: just plain text in chat
- AskUserQuestion: the standard widget. Each card has short options to pick from, with your recommendation first when you have one. Use it for suggestions with up to 4 options. Only add an "Other" option to open-ended questions (e.g. cuisine, cravings).
- ChoicePanel: an interactive panel from choice-panel.html template. Used for picking from more than 4 options as a multiselect or single select. If applicable, set `max` to what the plan needs (3 dishes, one carb each → 3) and state it in the question.
- ChecklistPanel: an interactive panel from checklist-panel.html template. Use the mode the workflow step names; each mode's config is described in the comment at the top of the template's script.

Other notes:
- Interactive panels are shown with show_widget. Copy the matching template and change only the question text and the config at the top of its script.
- If nothing fits, use Freeform. 
- Never trim options or merge items to fit 4.

## Cooking plan

- Check the cooking rules for cooking plan constraints (how the cooking is split between days, time spent cooking, etc).
- Parallelize the cooking across available kitchen equipment and give a timeline.
- The countertop work (prepping the sauces, chopping, etc) should also be included in the cooking plan.

## Ordering from the online store

- Except for the ingredients I said I want to get in brick and mortar store, I should be able to get all ingredients for the dishes from the online store, both base and condiments. 
- Before adding anything, check the cart for items already in it and ask me whether to keep or remove them.
- After filling the cart, check it again for unavailable items and swap in a reasonable substitute, telling me what changed.
- If any ingredients are not available and there are no reasonable substitutes, let me know. 
- I do the last step with scheduling the delivery and paying myself through browser.
