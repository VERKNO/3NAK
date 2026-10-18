# Chut

Andrew's recipe book: Batak home cooking and baking, adapted to ingredients available in Prague and to the equipment at home.

## Files

- `recipes.json`: all recipes, one object per recipe.
- `kitchen.json`: kitchen equipment and general cooking tips.
- `index.html`: a simple viewer app. Turn on GitHub Pages (Settings → Pages → deploy from `main`, root) to open it on your phone.

## Recipe format

```json
{
  "id": "kebab-case-id",
  "title": "Name",
  "category": "Cake | Fish | Meat | Chicken | Noodles | Vegetables | Sambal | ...",
  "cuisine": "Batak | European | ...",
  "description": "One or two sentences",
  "servings": 4,
  "time": "20 min prep + 40 min cooking",
  "oven": "160°C top & bottom heat, no fan" ,
  "equipment": ["chopper", "gas stove"],
  "ingredients": [{"amount": 200, "unit": "g", "name": "plain flour"}],
  "steps": [{"title": "Short title", "text": "What to do"}],
  "notes": ["Tips and variations"],
  "shopping": {"ingredient(s)": "where to find them in Prague"},
  "tags": ["batak", "oven"],
  "added": "YYYY-MM-DD"
}
```

`oven` is `null` for stovetop dishes. `unit` is `null` for countable items (eggs, shallots). The viewer scales ingredient amounts by servings.
