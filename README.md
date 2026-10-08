# Review Showdown

A classroom review game with a teacher board and student Chromebook buzzers. You don't need any accounts or a database.

- `index.html`: the teacher board. Project it.
- `buzzer.html`: the student buzzer. Students open it on Chromebooks.
- `sets/`: review sets saved as CSV files.

## Put it online (GitHub Pages)

1. Create a new public repository, for example `review-game`.
2. Upload everything in this folder (`index.html`, `buzzer.html`, `sets/`) to the repository root.
3. Go to **Settings → Pages**. Under Source, pick **Deploy from a branch**, then choose `main` and `/ (root)`. Save.
4. After a minute the board is live at `https://YOURNAME.github.io/review-game/`.
   Students go to `https://YOURNAME.github.io/review-game/buzzer.html`, or scan the QR code on the board.

## Running a game

1. Open the board. Pick a review set, name the teams and choose the buzzer mode.
2. **Student Chromebooks:** students type the 4-letter room code and pick a team. Several Chromebooks can join the same team, and the first buzz counts.
3. **One keyboard:** teams buzz with number keys 1–6 on the teacher computer. This mode works offline.
4. Teacher shortcuts: **Space** opens the buzzers. **Enter** goes back to the board or moves to the next step.
5. Typed answers are checked automatically. Small typos are allowed, and "What is…" is ignored. Use **Override** to change any call, or hover over a team's score and click **Edit** to change it by hand.

If you refresh the board mid-game, the game state is saved, and the board tries to reopen the same room code.

## Making a new review set

Make a spreadsheet with these columns (download `sets/blank-template.csv` or use **Download blank template** on the setup screen):

| category | points | clue | answer | also_accept | wrong_1 | wrong_2 | wrong_3 |
|---|---|---|---|---|---|---|---|
| Reformers | 200 | The reformer who exposed how prisoners and people with mental illness were treated | Dorothea Dix | Dix | Horace Mann | Lucretia Mott | Elizabeth Cady Stanton |
| Turning Points | FINAL | Historians call this election a revolution… | Election of 1800 | 1800 | Election of 1796 | Election of 1824 | Election of 1828 |

- **clue** is the definition or description. **answer** is the term, in a few words.
- **also_accept** lists other answers that count, separated by `|` (used for typed answers).
- **wrong_1, wrong_2, wrong_3** are the wrong options in 4-choice mode. Make them the same kind of thing as the answer (court case vs. court case, reformer vs. reformer) so the right one doesn't stand out. Any you leave blank are filled from other answers in the set. The choice order is shuffled every game.
- Put `FINAL` in the points column for the final round clue (optional).
- Up to 6 categories and 6 clues per category. Rows don't need to be in order.
- An optional first row `#title: Unit 4 Review` sets the game title. Any other row starting with `#` is ignored.

To load a set, you can:
- Use **Load CSV file** on the setup screen, drag the file onto the page, or paste cells straight from Google Sheets or Excel.
- Upload the CSV to `sets/` in the repository and open `index.html?set=sets/unit4-review.csv`. Bookmark that link.

## How the buzzers connect

The board and Chromebooks connect peer-to-peer. A free public matchmaking server (PeerJS) introduces them for a moment, with no sign-up. After that, buzzes go device to device. Some school networks block peer-to-peer traffic, so test it once on your school Wi-Fi. If it's blocked, use **One keyboard** mode.
