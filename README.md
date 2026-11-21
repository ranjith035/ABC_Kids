# ABC Adventure 🔤

A light, offline alphabet game for a 4-year-old. One HTML file — no install, no internet, no ads, no accounts.

**Play locally:** open `public/index.html` (or double-click it).
**Live site:** deploy the `public/` folder (see [Deploy](#deploy)).

## Play it

1. Open `public/index.html` in Chrome or Edge.
2. Press **F** or tap **⛶** for fullscreen.
3. On a TV: open the deployed URL in the TV browser, or connect HDMI from a laptop and press **F**.

Progress (stars) is saved in the browser automatically.

## Three ways to play

| Mode | What happens |
|---|---|
| **Learn** | Tap any letter, see a giant letter + picture + word. Words automatically advance every 5 seconds with a visual countdown timer so toddlers can learn hands-free. Tap the picture, the letter, or **Say it** to hear it. Tap **5s Auto** (or press **P**) to pause or resume anytime. Swipe or use ◀ ▶ to move manually. |
| **Word Match** | The game shows a big letter and three pictures. Pick the picture that starts with that letter. |
| **Letter Hunt** | The game says a word and shows its picture. Pick the letter it starts with. |
| **Surprise Me** | Jumps to a random letter. |

## Controls

### Touch / mouse
Tap anything.

### Keyboard

| Key | Action |
|---|---|
| Arrows | Move the yellow focus ring (home / quizzes) |
| Enter | Select the focused item |
| ← → | Previous / next word (Learn) |
| ↑ ↓ | Previous / next letter (Learn) |
| P / A | Pause or resume 5s auto-advance (Learn) |
| 1 2 3 | Pick an answer |
| Space | Repeat the word or question |
| Esc / Backspace | Back to the letter grid |
| F | Fullscreen |
| Any letter | Jump to that letter from the home screen |

### TV remote (Sony Bravia, Android TV, Fire TV, etc.)

The game listens for the standard D-pad key codes that TV browsers send:

| Remote button | Action |
|---|---|
| ◀ ▲ ▶ ▼ | Move the yellow focus ring |
| OK / Enter | Select the focused letter, mode or answer |
| Back | Return to the letter grid |
| Play/Pause (if it sends Space) | Repeat the word |

In **Learn**, ◀ ▶ changes the word, ▲ ▼ changes the letter, and **OK** says the word again. In the quizzes, the D-pad moves between the three answers and **OK** picks one.

> Note: the exact buttons depend on the TV browser. Sony's Android TV browser (or Chrome/Puffin installed on the TV) sends normal arrow/Enter key events, so it works. Very old Opera-based TV browsers may not support speech or modern CSS — in that case, cast/mirror from a laptop or use a Fire Stick/Chromecast with a browser.

## Learning design

- **No losing.** Wrong answers gently shake, say “Try again”, and after two tries the right answer glows as a hint.
- **Rewards, not pressure.** Every correct answer gives a star, confetti and a happy sound. Stars are counted per letter and shown on the home grid.
- **Spoken words.** Uses the device's built-in voice (slow, kid-friendly rate), so no audio files to download.
- **Big type.** Letters scale with the screen: roughly 350 px on a 1080p TV, with a giant letter card on every screen.
- **Color-coded letters.** Each letter has its own color to help memory.

## Word bank

- **432 words**, 15–18 per letter, chosen to be words a preschooler is likely to meet (animals, food, vehicles, everyday objects).
- **X is special:** only 4 words start with X (X-Ray, Xylophone, Xmas Tree, X-Ray Fish). The other 11 (Box, Fox, Six, Ox, Axe, Taxi, Exit, Mix, Fix, Wax, Sax) contain the X sound, which is how children's alphabet books usually teach X. Quizzes only ask about the 4 words that really start with X, and the game highlights the X inside the word.

### Add or change words

Open `public/index.html` and find:

```js
const LETTERS = [
  { l:'A', words:[['Apple','🍎'],['Ant','🐜'], ... ] },
  ...
];
```

Each word is `['Word', 'emoji']`. Add as many as you like — the word strip and counter update automatically. Use a single emoji per word.

## Deploy

The site is plain static files in `public/`, so there is no build step.

### Cloudflare Pages (Git integration)

In the Pages project settings use:

- **Framework preset:** None
- **Build command:** *(leave empty)*
- **Build output directory:** `public`

That is what fixes `Could not detect a directory containing static files`.

### Cloudflare Workers (Wrangler)

`wrangler.toml` is already configured with `[assets] directory = "./public"`:

```bash
npx wrangler deploy
```

If your Worker has a different name, change `name = "abc-kids"` in `wrangler.toml` first.

### Any other host

Upload the contents of `public/` (GitHub Pages, Netlify, Vercel, S3, a USB stick — all work).

## Ideas for v2

- Letter-sound (phonics) mode: “A says ah”.
- “Find the letter” around the room / memory match pairs.
- Record a parent's voice for each word.
- Install as a PWA so it opens like an app on a tablet.
- Weekly “words learned” summary for parents.
- Themed packs (animals, food, vehicles) and a second language.
