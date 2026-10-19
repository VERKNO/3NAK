# Chut

**Batak home cooking and baking, adapted for ingredients you can buy in Prague.**

Chut is a free recipe app. It works in any browser, can be installed on your phone like a normal app, and keeps working offline once you've opened it. No account, no sign-in, nothing to set up.

👉 **Open the app: [endrudaud.github.io/chut](https://endrudaud.github.io/chut/)**

*Chuť* is Czech for "taste".

## What's inside

- **Batak dishes**: arsik, saksang, BPK (babi panggang Karo), babi panggang Toba with crispy skin, babi goreng, mie gomak, daun ubi tumbuk, ayam panggang andaliman, sambal andaliman.
- **Baking**: simple cakes, with tips for glass tins and ovens without guesswork.
- **Kitchen notes**: substitutes and shopping tips at the bottom of the page.

Every recipe is simplified for a normal home kitchen and uses ingredients from Czech supermarkets or Prague's Asian shops. Each recipe lists where to buy the less common items.

Common substitutes used in the recipes:

| Indonesian ingredient | Use in Prague | Where |
|---|---|---|
| Andaliman | Sichuan pepper, toasted 1 minute in a dry pan | Sapa market or Asian shops |
| Kemiri (candlenut) | Macadamia nuts, same amount | Supermarkets |
| Asam cikala | Lime juice | Supermarkets |
| Daun salam | Bay leaves (bobkový list) | Supermarkets |
| Mie lidi | Thick spaghetti | Supermarkets |
| Pork blood (in sauces) | Left out; roasting juices or coconut milk instead | — |

## How to use

- **Search** by dish name or ingredient, for example "coconut" or "pork".
- **Change the servings** with the − and + buttons; ingredient amounts adjust automatically.
- Each recipe shows the **oven setting**, time, equipment and **where to shop**.

## Install it on your phone

**Android (Chrome)**
1. Open [endrudaud.github.io/chut](https://endrudaud.github.io/chut/) in Chrome.
2. Tap the **⋮** menu → **Install app** (or **Add to Home screen**).
3. Chut appears on your home screen with its own icon and opens full-screen.

**iPhone (Safari)**
1. Open [endrudaud.github.io/chut](https://endrudaud.github.io/chut/) in Safari.
2. Tap the **Share** button (square with an arrow) → **Add to Home Screen** → **Add**.

The app updates itself: new recipes appear the next time you open it with an internet connection. Recipes you've opened before also work offline.

## Run it on your computer

Opening `index.html` by double-clicking won't work, because the browser blocks loading the recipe file that way. Use a small local server instead:

- **VS Code**: install the **Live Server** extension, then click **Go Live** in the bottom status bar.
- **Python**: in this folder run `python -m http.server 8000` and open `http://localhost:8000`.

## For contributors

All recipes live in one file, `recipes.json`. To add a recipe, add one object to the `recipes` list:

```json
{
  "id": "kebab-case-id",
  "title": "Name",
  "category": "Cake | Fish | Meat | Chicken | Noodles | Vegetables | Sambal",
  "cuisine": "Batak | Batak (Karo) | European | ...",
  "description": "One or two sentences",
  "servings": 4,
  "time": "20 min prep + 40 min cooking",
  "oven": "160°C top & bottom heat, no fan",
  "equipment": ["chopper", "gas stove"],
  "ingredients": [{"amount": 200, "unit": "g", "name": "plain flour"}],
  "steps": [{"title": "Short title", "text": "What to do"}],
  "notes": ["Tips and variations"],
  "shopping": {"ingredient(s)": "where to find them in Prague"},
  "tags": ["batak", "oven"],
  "added": "YYYY-MM-DD"
}
```

- `oven` is `null` for stovetop dishes.
- `unit` is `null` for countable items (eggs, shallots); the name then carries the noun ("garlic cloves").
- Amounts are for the given `servings`; the app scales them.

Kitchen tips at the bottom of the page come from `kitchen.json` (`tips`: a list of `{title, text}`).

### Files

| File | What it is |
|---|---|
| `index.html` | The whole app (one page, no build step) |
| `recipes.json` | All recipes |
| `kitchen.json` | Kitchen tips shown at the bottom |
| `manifest.webmanifest` | App name, colors and icons for installing on a phone |
| `sw.js` | Offline support; bump `CACHE` (e.g. `chut-v2`) when you change `index.html` |
| `icons/` | App icons |
