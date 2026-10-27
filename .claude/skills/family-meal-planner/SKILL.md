---
name: family-meal-planner
description: Plan my family's meals following my cooking rules, then fill my online grocery cart and/or give me a list for shopping in a physical store. Use when I ask what to cook, for a meal plan or menu, for a shopping list, or to fill my grocery cart.
---

# My meal planning and grocery workflow

Read the cooking-rules.md - it contains personal information about my household and cooking preferences. Take it into account when executing the workflow.

## The workflow

1. In preparation of planning, ask me (unless I already told you in my request): 
    1. How many meals or days I want to cook for, and whether that includes any special occasion days mentioned in cooking rules (Freeform)
    2. How I'm shopping this time: online store only, physical store only, or a mix (AskUserQuestion)
    3. Do I have any ingredients that I need to use up (Freeform)
    4. Any cuisine I'm in the mood for (AskUserQuestion)
    5. Any particular recipes or ingredient I'm in the mood for (Freeform)
2. Work out how many distinct dishes are needed from the cooking rules (e.g. cook once, eat twice), then offer me up to 3 recipes per dish to choose from that fit my rules (AskUserQuestion - repeat for each dish). Each meal should contain protein, carbs and veggies. These are nutritional components, not separate dishes: one dish can cover all three (like one pot dinner), or a meal can combine a main with sides. 
3. You give me the final menu with ingredients listed, price estimation per meal and total price as if I have none of the ingredients at home (before adding staples). Ask me if I want to adjust anything. (Freeform)
4. For pantry staples (oil, salt, spices, condiments) ask me if I'm missing anything. For the rest of the items, ask me if I already have it, or, if I already stated that I have - whether I have enough for your plan. (ChecklistPanel, pantry check mode) After I answer, give me the adjusted total price without the items I already have.
5. Ask me if we need to replenish anything from staples.md. (ChecklistPanel, staples restock mode, one section per group in staples.md) After I answer, give me the price of the checked staples and the new total including them.
6. If I'm shopping in a mix, ask me which items I'll buy in the physical store (ChoicePanel, no `max`). Offer one combined list: the meal plan ingredients I still need plus the staples I checked. The rest goes to the online store.
7. For checked staples marked with * that go to the online store, ask me which flavors/variety I want out of those offered there (Freeform, give the numbered list and I type the number that I want). Don't ask for the ones going to the physical store; I'll pick there.
8. After I confirm, fill the online store cart with the online items, see Ordering from the online store section. Skip if I'm shopping only in the physical store.
9. Give me the list for the physical store with the physical store items, see Shopping in the physical store section. Skip if I'm shopping only online.
10. Give me a parallel cooking plan, see Cooking plan section.

## Prices

- All prices come from the online store, as estimates for items I'll buy in the physical store too.
- If no online store is connected, skip every price estimate in the workflow.

## Finding products in the online store

- Product names don't always state the property I need (frozen, pre-cut, unsalted, vegan, etc.). Don't judge a search result by its name alone: open the details of every plausible result before saying a product isn't available.
- If a search that includes the property comes back empty, search again for just the ingredient and check the results' details.

## Asking me questions

Ask the workflow questions strictly in the order listed, one question per turn, skipping only the ones I already answered. Don't reorder, batch or regroup questions.

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

- Only add the items I didn't assign to the physical store. I should be able to get all of them from the online store, both base and condiments.
- Before adding anything, check the cart for items already in it and ask me whether to keep or remove them.
- After filling the cart, check it again for unavailable items and swap in a reasonable substitute, telling me what changed.
- If any ingredients are not available and there are no reasonable substitutes, let me know.
- Tell me the cart total for the items you added, as shown in the online store after substitutions.
- I do the last step with scheduling the delivery and paying myself through browser.

## Shopping in the physical store

- Give me the list in chat as a checklist I can tick off on my phone, grouped by store section (produce, meat and fish, dairy, bakery, dry goods, frozen, household), in the order I'd walk through a typical supermarket.
- Each item gets the total quantity to buy across all meals (e.g. "Onions — 4", not one line per recipe) and the package size to look for when it matters.
- Add a short note next to items whose label you couldn't check in the online store, saying what to check according to cooking rules (allergens etc), and a fallback if it's sold out (e.g. "or frozen spinach").
- End with the estimated total for the physical store part.
