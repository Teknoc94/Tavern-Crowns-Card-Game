# Tavern Crowns

A tavern card game of crowns, castles and folk-tale monsters, set in a fantasy Carpathian Basin of the 12th–14th centuries.

Three rounds, two victories, ten cards in your hand. Raise the red-and-silver Árpád banners, bribe the Golden Basileia, call the fairies of the Bakony, the Night Brood of the marshes or the river clans of the Danube, and outlast an opponent who knows exactly when to pass.

**[Play it in your browser](https://teknoc94.github.io/Tavern-Crowns-Card-Game/)** (after you enable GitHub Pages, see below)

## Features

- Five factions, 22 leaders and 162 cards across three sets (Core, Mirror & Smoke, River Crowns)
- A computer opponent with three difficulty levels: Easy, Medium and Hard
- Deck builder: at least 22 units, at most 10 specials, saved in your browser
- A full rulebook in the game, with notes on the real history and folklore behind the cards
- An original tavern tune, synthesised live in the browser
- Works on desktop and phone, with no build step and no dependencies

## The factions

| Faction | Edge | Flavour |
|---|---|---|
| Holy Crown of Hungaria | Draws a card after every round it wins | Árpád stripes, Béla IV's stone castles, Cuman horse archers, Teutonic Knights of Barcaság |
| Golden Basileia | Wins every drawn round | 12th-century Byzantium: Manuel I Komnenos, Anna Komnene, Irene Piroska, the Varangian Guard, Greek fire |
| Free Folk of the Bakony | Decides who goes first | Tündér Ilona's fairies, dwarves of the Bükk and Mátra, outlaws and herb-wives |
| Night Brood | Keeps one unit on the battlefield after each round | Lidérc, boszorkány, garabonciás, the iron-nosed hag, the seven-headed dragon |
| River Clans of the Danube | Brings back two units at the start of round 3 | Lehel's horn, Botond's mace, Réka's shieldmaidens, táltos brew and the Turul |

## Run it locally

Open `index.html` in a browser. To load painted card art from the `art/` folder, serve the folder over HTTP, because browsers block `fetch` on `file://` pages:

```sh
python3 -m http.server 8000
# then open http://localhost:8000
```

## Publish with GitHub Pages

1. Push this repository to GitHub.
2. Open **Settings → Pages**, choose **Deploy from a branch**, select `main` and `/ (root)`, and save.
3. After a minute the game is live at `https://teknoc94.github.io/Tavern-Crowns-Card-Game/`.

## Card art

Every card already has generated fallback art. To replace it with painted art:

1. Open `art/PROMPTS.md`. It has a ready-made image prompt for every card and leader. The Deck Builder can also copy a single card's prompt, or all of them.
2. Generate an image with the image tool of your choice, and save it in `art/` named after the card id, for example `art/miklos_toldi.webp`.
3. Add it to `art/manifest.json`:

```json
{
  "cards": {
    "miklos_toldi": "miklos_toldi.webp",
    "saint_margaret_the_healer": { "file": "saint_margaret_the_healer.png", "full": true }
  }
}
```

Use `"full": true` when the image is a complete card with its own frame, number and name panel; the game then hides its own frame.

To try art before committing it, use **Deck Builder → Card art → Upload images**. Files are matched by name (`miklos_toldi.png` or `Miklós Toldi.png`) and stay in your browser only.

Check the license of the image tool you use before you publish its output.

## Project layout

```
index.html        entry point
src/db.js         card, leader and faction data
src/engine.js     rules engine and computer opponent
src/art.js        generated fallback card art
src/music.js      the tavern tune (WebAudio)
src/ui.js         screens, deck builder, card art loading
src/rules.js      in-game rulebook
src/style.css     styles
art/              painted card art, manifest.json, PROMPTS.md
```

## History and folklore

Names and stories come from Hungarian and Central European history of the 11th–14th centuries and from Hungarian folk tales. Abilities and events in the game are fiction. The in-game rulebook has a short note on each source.

## License

Code: MIT, see `LICENSE`. Art you add to the `art/` folder is covered by its own terms.
