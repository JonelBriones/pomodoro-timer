# Study Quest — design

A study timer that tags each focus block by subject, tracks weekly hours and plans topics from your syllabus.

This file is how the app looks. It comes from the clickable prototype designed in Altitude, which stays there as the visual target. Follow it whenever a screen is built or changed: use these colours, fonts and spacing, and give each screen the parts listed for it. The prototype is a picture, not code — build every screen in this project's own code. The app shell comes first: every screen as its own page, the navigation between them and this look, with a clearly labelled placeholder for each part a screen holds. Later tasks replace the placeholders with the real parts, one task at a time.

## Device

A website in a desktop browser window. Design for a 1280px-wide window first; narrower windows may stack the same parts.

## Look

- Name: Loaded Bar — Calm, dark, and quietly competitive, like a solo training session logged one plate at a time.
- Mode: dark
- Direction: A home gym at night: dark slate, chalk-white type, and coloured plates that load up as the study week builds.
- Signature element: The week bar: each day is a barbell and every finished pomodoro slides on as a plate in its subject's colour, so the week reads like a loaded training block.
- Who and where: Late evening after a guard shift, he sits at a home desk in a dim room, a lamp on the math workbook and the laptop screen as the brightest thing nearby, so the screen goes dark.

## Colours

Full palette: a midnight slate base, with competition plate colours (red, blue, yellow, green) each owning one subject, and plate red as the action colour.

| Name | Value | Used for |
|---|---|---|
| Night slate | `#171C27` | Page background, the dim desk at night |
| Raised slate | `#222A3C` | Timer field and grouped surfaces |
| Raised slate 2 | `#2A3349` | Backgrounds and selected states (a lighter Raised slate) |
| Chalk | `#EEF0F4` | Primary text and timer digits |
| Mist | `#A3ACC0` | Text |
| Mist 2 | `#6F7891` | Text and backgrounds (a deeper Mist) |
| Line | `rgba(163,172,192,.14)` | Borders |
| Plate red | `#F0524A` | Primary action, focus ring, first subject |
| Plate red press | `#D9443D` | Hover states (a deeper Plate red) |
| Plate blue | `#4C8DF6` | Second subject plates and tags |
| Yellow | `#F4C542` | Text and backgrounds |
| Plate green | `#3FBF7F` | Done states, streak kept, checked topics |

As CSS custom properties:

```css
:root {
  --night: #171C27; /* Night slate */
  --raised: #222A3C; /* Raised slate */
  --raised-2: #2A3349; /* Raised slate 2 */
  --chalk: #EEF0F4;
  --mist: #A3ACC0;
  --mist-2: #6F7891;
  --line: rgba(163,172,192,.14);
  --red: #F0524A; /* Plate red */
  --red-press: #D9443D; /* Plate red press */
  --blue: #4C8DF6; /* Plate blue */
  --yellow: #F4C542;
  --green: #3FBF7F; /* Plate green */
}
```

## Fonts

Free Google Fonts families under the SIL Open Font License: use them in the app, self-host them, or load them from Google Fonts.

- **Unbounded** — Timer digits and the app wordmark only. Weights 500, 700. Get it: https://fonts.google.com/specimen/Unbounded
- **Hanken Grotesk** — All UI text, headings, labels, numbers. Weights 400, 600, 800. Get it: https://fonts.google.com/specimen/Hanken+Grotesk

To load them from Google Fonts:

```html
<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Unbounded:wght@500;700&family=Hanken+Grotesk:wght@400;600;800&display=swap">
```

## Spacing, corners and shadows

- Spacing: 4 / 8 / 12 / 16 / 24 / 32 / 48 px; tight inside groups, 32 between regions
- Corners: 6px chips and plates, 12px buttons and inputs, 20px large fields
- Shadows: `0 12px 32px rgba(6,9,16,.45)`

## Icons

Simple line icons drawn in the text colour (2px stroke, 1em square), never emoji. The prototype uses: zap, star, pencil, play, target, check, plus, info, file-text, arrow-left, sparkles, refresh-cw, check-circle, x. Any open-source line icon set with these icons works.

## Navigation

- The persistent navigation reaches: Focus, This week, Topic plan, Subjects. It shows on every screen, those that open from another screen included.
- The item for the screen you are on is marked as current (`aria-current="page"`): a Raised slate (`#222A3C`) background, its text in Chalk (`#EEF0F4`). On a screen it doesn't lead to, the item you came from stays marked.
- Paste syllabus opens from another screen and has a back control; the navigation doesn't lead to it.

## Screens

Main screen first: the one people look at most. Locally the app runs at localhost:3000.

### Focus (main screen)

Start a tagged focus block and see the week loading up

Holds:
- Top navigation with Focus active
- Streak and points pills in the top bar
- Subject picker chips
- Edit subjects link
- Current topic heading for the chosen subject
- Big countdown clock
- Start focus / Pause button
- Focus, break and long break lengths
- Points to earn for this block
- Session logged, +20 pts confirmation
- Today's finished sessions
- Next topic card with Mark done
- Marked done state
- Open topic plan and Paste a syllabus links
- Week total studied
- Week bar of barbells loaded with subject plates
- Streak line with session meter
- Hours per subject legend

Opens: Subjects, Topic plan, Paste syllabus

Features it shows:
- Run a tagged focus timer
- Earn points and a weekly streak
- See weekly hours and your next topic

### This week

Review hours per subject and streak progress for the week

Holds:
- Page title with week range and total studied
- Session log panel
- Day group with date and day total
- Session row with subject colour, time, subject and points
- Empty rest-of-week line with Start focus button
- Hours per subject panel
- Subject hours row
- Streak panel
- Points earned this week
- Sessions toward streak line with meter
- Last 3 weeks list with kept tags
- Block logged confirmation

Later (parked for after your first version — don't build these yet):
- Weekly goal bar and goal text
- Change goals link

Opens: Focus, Subjects

Features it shows:
- See weekly hours and your next topic
- Earn points and a weekly streak
- Set a weekly hours goal per subject (not in your first version: parked for later)

### Topic plan

Edit and check off topics by suggested week

Holds:
- Page title and plan progress line
- Weeks done summary under the title
- Paste a syllabus button
- Subject switcher chips
- Topic plan panel
- Week group
- Week label with this-week marker
- Topic row with done and next states
- Topic checkbox
- Next up tag
- Move to week select
- Rename button
- Inline rename field with Save
- No plan yet empty state
- Checked off, moved or plan saved confirmation
- Up next panel
- Up next Mark done button
- Topics checked off progress bar

Opens: Paste syllabus

Features it shows:
- Turn a syllabus into an editable topic plan
- Check off topics as you study

### Paste syllabus

Turn a pasted syllabus into a draft topic plan

Holds:
- Back to topic plan
- Page title and explainer
- Subject select
- Syllabus text area
- Empty syllabus error
- Make my topic plan button
- Draft plan panel
- Draft empty state
- Reading your syllabus notice
- Draft topic row with title, week and remove
- Topics and weeks check notice
- Save to topic plan button

Opens: Topic plan

Features it shows:
- Turn a syllabus into an editable topic plan

### Subjects

Add subjects once and give each a plate colour

Holds:
- Page title with subject count and total hours
- Subject list panel
- Subject row with plate colour, name, date added and hours to date
- Plan link on each subject row
- Add a subject panel
- Subject name field
- Plate colour swatches
- Add subject button
- Subject added confirmation
- Missing name error

Later (parked for after your first version — don't build these yet):
- Weekly goal picker on each subject row
- Weekly goal field for the new subject

Opens: Topic plan

Features it shows:
- Add your subjects once
- Set a weekly hours goal per subject (not in your first version: parked for later)
