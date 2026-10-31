# Chut

**Recipes for Indonesian taste, adapted for ingredients you can buy in Prague.**

Chut is a free recipe app in **English and Bahasa Indonesia**. It works in any browser, can be installed on your phone like a normal app, and keeps working offline once you've opened it. No account, no sign-in, nothing to set up.

👉 **Open the app: [endrudaud.github.io/chut](https://endrudaud.github.io/chut/)**

*Chuť* is Czech for "taste".

> **Bahasa Indonesia:** Chut adalah aplikasi resep gratis untuk cita rasa Indonesia, disesuaikan dengan bahan yang bisa dibeli di Praha. Tekan **ID** di bagian atas untuk Bahasa Indonesia. Bisa dipasang di HP: di Android buka di Chrome → menu **⋮** → **Instal aplikasi**; di iPhone buka di Safari → **Bagikan** → **Tambahkan ke Layar Utama**. Tidak perlu akun.

## What's inside

The app has three sections, as tabs above the recipe list:

- **Food**: Batak dishes (arsik, saksang, BPK, babi panggang Toba, babi goreng, mie gomak, daun ubi tumbuk, ayam panggang andaliman, sambal andaliman), simple cakes and baking, and a versatile peanut sauce (bumbu kacang) for salads, fried tofu/tempeh or satay. Filterable by **Savoury / Sweet**.
- **Beverage**: coffee and non-coffee drinks, filterable by **Coffee / Non-coffee** and **Hot / Cold** — including Indonesian drinks (kopi tubruk, es kopi susu, es teh manis, wedang jahe, bandrek, es cendol). The **Coffee types & differences** link shows how common coffee drinks compare (espresso, latte, cappuccino, cold brew, kopi tubruk and more), with a simple diagram of each one's proportions.
- **Make your own**: how to ferment your own tempeh and grow your own bean sprouts (tauge) at home, from soybeans or mung beans.
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

- **Switch language** with **EN | ID** at the top. The app remembers your choice, and starts in Indonesian if your phone is set to Indonesian.
- **Pick a section** (Food / Beverage / Make your own) and narrow it further with the filter chips underneath.
- **Search** by dish name or ingredient, in either language, for example "coconut" or "santan".
- **Change the servings** with the − and + buttons; ingredient amounts adjust automatically.
- Each recipe shows the **oven setting**, time, equipment and **where to buy** the ingredients in Prague.
- **Add all ingredients to your shopping list** with one tap on a recipe page, or add them one at a time; open the list with the **Shopping list** button at the top.

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

All recipes live in one file, `recipes.json`. Text is written in both languages as a pair `["English", "Indonesian"]`; a plain string is used for text that is the same in both (numbers, Czech words). To add a recipe, add one object to the `recipes` list:

```json
{
  "id": "kebab-case-id",
  "title": ["Name in English", "Nama dalam Bahasa Indonesia"],
  "category": ["Meat", "Daging"],
  "cuisine": "Batak",
  "section": "food",
  "type": "savoury",
  "description": ["One or two sentences", "Satu atau dua kalimat"],
  "servings": 4,
  "time": ["20 min prep + 40 min cooking", "20 menit persiapan + 40 menit masak"],
  "oven": ["160°C top & bottom heat, no fan", "160°C api atas & bawah, tanpa kipas"],
  "equipment": [["chopper", "chopper"], ["gas stove", "kompor gas"]],
  "ingredients": [{"amount": 200, "unit": "g", "name": ["plain flour", "tepung terigu"]}],
  "steps": [{"title": ["Short title", "Judul singkat"], "text": ["What to do", "Apa yang dilakukan"]}],
  "notes": [["Tip", "Tips"]],
  "shopping": [{"items": ["galangal, lemongrass", "lengkuas, serai"], "where": ["Sapa or Asian shops", "Sapa atau toko Asia"]}],
  "tags": ["batak", "oven"],
  "added": "YYYY-MM-DD"
}
```

- `section` is `"food"`, `"beverage"` or `"ferment"` — picks which tab the recipe shows under. Defaults to `"food"` if left out.
  - For `"food"`: add `type`, `"savoury"` or `"sweet"` (defaults to `"savoury"`).
  - For `"beverage"`: instead of `type`, add `drink` (`"coffee"` or `"noncoffee"`) and `temp`, an array such as `["hot"]`, `["cold"]` or `["hot", "cold"]` for a drink served either way.
  - `"ferment"` (things you make yourself, like tempeh or bean sprouts) needs neither.
- `oven` is `null` for stovetop dishes.
- `unit` is `null` for countable items (eggs, shallots); the name then carries the noun ("garlic cloves"). Units `tsp`, `tbsp` and `cup` are shown as `sdt`, `sdm` and `cangkir` in Indonesian.
- Amounts are for the given `servings`; the app scales them.

Kitchen tips at the bottom of the page come from `kitchen.json` (`tips`: a list of `{title, text}`, both as language pairs). Button and label texts are in the `UI` object at the top of the script in `index.html`. The coffee-types guide (12 entries, each with a title, description and a ratio for its diagram) is the `COFFEE_GUIDE` constant near the top of the script, not a separate file.

You don't need to edit `recipes.json` by hand: in the app, tap **Add recipe** to paste or upload one recipe's JSON
(this same shape, or `{"recipes": [...]}` for several at once) — the **Show recipe JSON structure** link in that
sheet shows and copies the template above. Recipes added this way stay in your own browser only (not shared with
other people or synced back to this repo).

### Files

| File | What it is |
|---|---|
| `index.html` | The whole app (one page, no build step) |
| `recipes.json` | All recipes |
| `kitchen.json` | Kitchen tips shown at the bottom |
| `manifest.webmanifest` | App name, colors and icons for installing on a phone |
| `sw.js` | Offline support; bump `CACHE` (e.g. `chut-v6`) when you change `index.html` |
| `icons/` | App icons |
