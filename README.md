# MealCraft

A free personal meal planner that runs entirely in your browser. Add what's in your pantry, build meals from it, and drop them into a weekly plan you can print or download as an image.

**Live site:** https://crypticot.github.io/meal-craft/

## Features

- **Pantry:** add ingredients one at a time or several at once, separated by commas. Duplicates are skipped.
- **My Meals:** build a meal once from your pantry items, then reuse it anywhere. A meal without its own photo shows its first ingredient's picture.
- **Weekly planner:** plan Breakfast, Lunch and Dinner for every day of the week, with a "today" highlight, week-by-week navigation, and a one-click "Copy to next week".
- **Custom meal slots:** rename, remove or add slots such as Snack.
- **Output grid:** pick a date range and print it, save it as a PDF, or download it as a PNG image.
- **Picture picker:** search TheMealDB and Wikipedia for pictures (plus Pexels if you add a free API key), upload your own photo, or paste an image link.
- **Starter foods:** load ready-made ingredients and meals by country from `starter-foods.json`, and untick anything you don't want.
- **Save and import:** export your whole plan as a `.json` file and import it on another device.
- **Mobile friendly:** the planner switches to a day-by-day layout on small screens.

## Privacy

There is no account, server or database. Everything is stored in your browser's `localStorage`. Clearing your browser data erases your plan, so use **Save plan** on the home page to keep a backup file.

The only network requests are the optional picture searches (TheMealDB, Wikipedia, Pexels) and the fonts, icons and image-export library loaded from public CDNs.

## Running it locally

It's a single static page with no build step.

1. Download or clone the repository.
2. Serve the folder with any static server, for example:

   ```bash
   python3 -m http.server 8000
   ```

3. Open http://localhost:8000.

You can also open `index.html` directly. In that case the browser may block loading `starter-foods.json` automatically, and the Starter foods dialog will let you choose the file by hand.

## Project structure

```
index.html            App markup, styles and logic (single file)
plate.png             Hero image on the home page
starter-foods.json    Starter ingredients and meals by country
og-image.jpg          Social sharing preview (1200x630)
favicon.ico           Browser tab icon
favicon.svg
favicon-32x32.png
apple-touch-icon.png  iOS home screen icon
icon-192.png          Web app manifest icons
icon-512.png
site.webmanifest      Web app manifest
```

## Starter foods format

`starter-foods.json` maps a country name to its ingredients and meals:

```json
{
  "Nigeria": {
    "ingredients": [
      { "name": "Garri", "wiki": "Garri" }
    ],
    "meals": [
      { "title": "Jollof rice", "items": ["Rice", "Tomato", "Onion"], "wiki": "Jollof rice" }
    ]
  }
}
```

- `items` lists ingredient names. Any that aren't in the pantry yet are added automatically.
- `wiki` (a Wikipedia page title) or `img` (an image URL) is optional. When present, the picture is fetched if the user leaves "Add pictures" ticked.

## Built with

- HTML, CSS and vanilla JavaScript, with no framework
- [Plus Jakarta Sans](https://fonts.google.com/specimen/Plus+Jakarta+Sans) via Google Fonts
- [Font Awesome](https://fontawesome.com/) icons
- [html2canvas](https://html2canvas.hertzen.com/) for image export

## Deploying to GitHub Pages

1. Push the files to a repository named `meal-craft`.
2. Go to **Settings → Pages**, choose the `main` branch and the root folder, then save.
3. The site will be live at `https://<your-username>.github.io/meal-craft/`.

If you use a different username or repository name, update the URLs in the `<head>` of `index.html` (`canonical`, `og:url`, `og:image`, `twitter:image` and the JSON-LD block).
