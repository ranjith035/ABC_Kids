# ABC Adventure 🔤

A light, offline alphabet game for a 4-year-old. One HTML file — no install, no internet, no ads, no accounts.

**File:** `abc-adventure.html` (~45 KB)

## Play it

1. Double-click `abc-adventure.html` (opens in Chrome or Edge).
2. Press **F** or tap **⛶** for fullscreen.
3. On a TV: connect HDMI, open the file on the big screen, press **F**.

Progress (stars) is saved in the browser automatically.

## Three ways to play

| Mode | What happens |
|---|---|
| **Learn** | Tap any letter, see a giant letter + picture + word. Tap the picture, the letter, or **Say it** to hear it. Swipe or use ◀ ▶ to move through the words. Tap any picture in the bottom strip to jump straight to it. |
| **Word Match** | The game shows a big letter and three pictures. Pick the picture that starts with that letter. |
| **Letter Hunt** | The game says a word and shows its picture. Pick the letter it starts with. |
| **Surprise Me** | Jumps to a random letter. |

## Controls

- **Tap / click** — everything works by touch or mouse.
- **← →** — previous / next word (Learn mode).
- **1 2 3** — pick an answer (Word Match / Letter Hunt).
- **Space** — repeat the word or question.
- **Esc** — back to the letter grid.
- **F** — fullscreen.
- **Type any letter** on the home screen to jump to it.

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

Open `abc-adventure.html` in Notepad/VS Code and find:

```js
const LETTERS = [
  { l:'A', words:[['Apple','🍎'],['Ant','🐜'], ... ] },
  ...
];
```

Each word is `['Word', 'emoji']`. Add as many as you like — the word strip and counter update automatically. Use a single emoji per word.

## Ideas for v2

- Letter-sound (phonics) mode: “A says ah”.
- “Find the letter” around the room / memory match pairs.
- Record a parent's voice for each word.
- Install as a PWA so it opens like an app on a tablet.
- Weekly “words learned” summary for parents.
- Themed packs (animals, food, vehicles) and a second language.
