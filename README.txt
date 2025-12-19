# # lotto-game

A client-side Lotto game built with **HTML + CSS (Grid/Flex + Media Queries) + JavaScript (DOM)**.  
The player starts with a fixed amount of money, selects **1 strong number (1–7)** and **6 unique numbers (1–37)**, pays for a ticket, and checks the round against the system draw.

> UI note: Bootstrap is used **only** for UI components (Alerts + Modals). Game logic is plain JavaScript.

---

## Features
- Dynamic boards generated in JavaScript:
  - Strong numbers: **1–7**
  - Regular numbers: **1–37**
- Instant visual selection (stable `is-selected` state)
- Valid round flow:
  - Validations (must pick 1 strong + exactly 6 numbers)
  - Ticket payment per round
  - Prize calculation + results rendering
  - **Valid plays** counter increases only after a completed valid check
- Blocking modal when:
  - Player finishes the game
  - Player runs out of money (shows remaining money + restart instructions)
- Responsive layout (Phone / Tablet / Above tablet)
  - Phone layout uses fewer grid columns and bigger buttons for comfortable tapping

---

## Tech Stack
- HTML5
- CSS3 (Grid, Flexbox, Media Queries)
- JavaScript (DOM, Events)
- Bootstrap 5 (UI only: Modals & Alerts)

---

## Project Structure
```text
/
├─ index.html
├─ css/
│  └─ styles.css
├─ js/
│  └─ app.js
└─ Web.config



How to Run
Option A — Quick

Download/clone the repo.

Open index.html in a browser.

Option B — Recommended (Live Reload)

Use VS Code “Live Server” or Visual Studio run options for a smoother workflow.

How to Play

On page load, read the rules in the Welcome modal.

Click Start Game.

Select:

1 strong number (1–7)

Exactly 6 unique numbers (1–37)

Click Check lottery to play a round.

Review results (winning vs your picks) and continue until:

You finish the game, or

You run out of money (the game locks).

Game Rules

Ticket cost is fixed per round.

A valid play requires:

1 strong number

6 numbers

Prize rules:

6 matches + strong → 1000

6 matches without strong → 600

4 matches + strong → 400

Anything else → 0

UI & Responsive Design

The page uses a clean centered container and panels for clarity.

Boards are CSS Grid-based:

Phone: fewer columns + larger buttons (easier selection)

Tablet: more columns + more compact layout

Above tablet: more columns and larger typography

Button styling is stable:

Selected state remains visible even under :focus / :active states.

Debugging Notes

The project includes a debug helper controlled by a DEBUG flag.

A dedicated debug function can print only the system winning values when needed.

Recommended DevTools workflow:

Elements: verify is-selected classes

Console: inspect game.state / game.player

Sources: add breakpoints inside click handlers (onNumberClicked, onCheckLotteryClicked)

Function Reference (Short)

Ordered by the app flow.

Boot / Setup

cacheElements() — cache DOM nodes

initBootstrapModals() — init welcome/block modals

wireEvents() — connect UI events

Alerts / Modals

showAlert() — show Bootstrap alert

escapeHtml() — HTML escaping for safe rendering

openWelcomeModal() / closeWelcomeModal() — welcome modal control

openBlockModal() — lock the game + show modal

updateBlockModalContent() — update modal text/money

Board Creation

buildBoards() — generate strong + number boards

createCellButton() — create a single board button

readCellValue() — parse button data-value

clearElement() — clear a DOM container

Rendering

renderStatus() — update stats (money, ticket cost, valid plays)

renderPicked() — show current user picks

renderSelectionStyles() — apply is-selected classes

setControlsEnabled() — enable/disable UI controls

Round Lifecycle

startNewRound() — generate winning values + reset picks

User Actions

onStrongClicked() — toggle strong selection

onNumberClicked() — toggle number selection (max 6)

onCheckLotteryClicked() — validate + charge + evaluate + render result

onFinishClicked() — finish and lock

onDepositClicked() — optional money deposit + unlock (if enabled)

Results / Rules

renderResult() — show round results + summary

chipsHtml() — build badge HTML output

calculatePrize() — compute prize from matches

Utilities

generateUniqueNumbers() — unique random numbers

randomInt() — random integer in range

countMatches() — count matching numbers

buildHitArray() — hit flags for rendering

indexOfNumber() — loop-based indexOf

removeAt() — loop-based remove without splice

copyArray() — loop-based array copy

arrayToString() — loop-based array string (no join)

Screenshots

Add your screenshots to: assets/screenshots/ and update paths below.

Welcome Modal

Number Selection (Phone Layout)

Round Result

Blocked Game (Out of Money / Finished)

Notes (Course / Constraints)

The project is fully client-side.

The UI avoids permanent on-page messages and uses alerts/modals for user feedback.

Array handling utilities are implemented conservatively (loop-based helpers where needed).