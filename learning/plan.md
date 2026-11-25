<!-- altitude:generated from your journey — local edits don't sync; park ideas in a lesson or edit on the web -->

# Study Quest: a pomodoro timer built around your study week

You add your subjects once, like math review. You start a focused pomodoro tagged with a subject, and each finished session earns points toward a weekly streak. You paste a course syllabus, and a language model turns it into a list of topics with suggested weeks, which you can edit and check off as you study. The home page shows your hours per subject this week and your next planned topic.

## Locked decisions

## Build brief
### Stack
- React
- Express.js
- Node.js
- SQL database
- Tailwind
### Features
- Run a tagged focus timer
- Earn points and a weekly streak
- See weekly hours and your next topic
- Turn a syllabus into an editable topic plan
### Design
- Build every screen to `DESIGN.md` at the project root: the colours, fonts, spacing and screens of your Altitude prototype, the visual target. The app shell section sets up every screen as its own page, with the navigation, the look and a clearly labelled placeholder for each part; later tasks fill the placeholders. Each task that builds or changes a screen brings the file and writes it if it is missing or out of date.

## 00 · Click through every Study Quest screen
The React app runs in your browser with the Focus, This week, Topic plan, Subjects and Paste syllabus pages, the prototype's colours and fonts, a labelled placeholder for each part, and a top navigation that marks the page you are on.

- [x] Create the project and install React
  A Study Quest folder exists on your machine with React installed, and you can say what each installed package is for.
- [ ] Open the app and apply the design colours ← you are here
  The dev server shows your app in the browser on the dark slate background with the prototype's chalk text, fonts and spacing, and a change you save appears without restarting.
- [ ] Lay out the Focus page with placeholders
  The Focus page shows labelled boxes for the subject picker, the big clock, today's sessions and the week bar, and clicking the Start focus placeholder logs a message you can see in the console.
- [ ] Give every screen its own page component and address
  Focus, This week, Topic plan, Subjects and Paste syllabus each exist as their own component at their own address, laid out in the prototype's columns with a labelled placeholder for every part.
- [ ] Add the navigation that marks the current page
  You click between Focus, This week, Topic plan and Subjects from a top bar that highlights the page you are on, and Paste syllabus opens from the Topic plan with a back control while the navigation keeps the plan marked.

## 01 · Your subjects live in a SQL database behind your own API
An Express server you wrote reads your real subjects, like math review, from a SQL table and returns them as JSON at /api/subjects.

- [ ] Start a Node server process
  Running one command starts your server, it prints the port it listens on, and a browser request to it gets a plain reply.
- [ ] Route requests with Express
  Express answers a health route, logs every incoming request through a small middleware, and returns a clear 'not found' for unknown addresses.
- [ ] Design the subjects table
  You choose a SQL database for the project and create a subjects table with a name, a plate colour and the date added, and you can explain each column.
- [ ] Connect the server and insert your real subjects
  The server connects using a connection string kept in an environment variable, and math review plus your other real subjects are inserted and read back with SELECT.
- [ ] Serve your subjects as JSON
  Visiting /api/subjects in the browser shows your real subjects as a JSON list straight from the database.

## 02 · Add your subjects once from the app
The Subjects page lists your subjects from the API, and adding one with a name and plate colour saves it to the database and shows it immediately.

- [ ] Save your working app with Git
  Your shell and your subjects API are saved in a first commit, and you stage only the files you mean to keep.
- [ ] Call your API from the browser
  The app fetches /api/subjects, logs the subjects it got, and logs a readable message instead of crashing when the server is stopped.
- [ ] Show your subjects on the Subjects page
  The page title with subject count, the subject list panel and each subject row with plate colour, name and date added show your real data, with a loading and an error message when needed.
- [ ] Accept new subjects on the server
  A POST to /api/subjects saves a new subject, and a request with no name gets a 400 with a clear message instead of an empty row.
- [ ] Submit the Add a subject form
  The Add a subject panel with its subject name field, plate colour swatches and Add subject button saves a subject, the new row appears in the list, and the subject added confirmation shows.

## 03 · Run a tagged focus timer that logs real sessions
You pick math review on the Focus page, run a real countdown, and each finished block is saved as a session linked to that subject and listed under today.

- [ ] Pick a subject on the Focus page
  The top navigation with Focus active, the subject picker chips and the Edit subjects link work, and the chosen subject is shared with the clock area.
- [ ] Make the countdown clock tick
  The big countdown clock counts down in mm:ss, the Start focus / Pause button starts and pauses it, and the focus, break and long break lengths switch the starting time.
- [ ] Add a sessions table linked to subjects
  A sessions table stores start and end times and points, each row points at its subject, and inserts use placeholders rather than pasted-in values.
- [ ] Log a finished session exactly once
  When the clock hits zero the session is saved once even if the request repeats, the Session logged, +20 pts confirmation appears, and the Block logged confirmation shows on This week.
- [ ] List today's finished sessions
  Today's finished sessions under the clock show each real block with subject and time, counted by your local day rather than the server's.

## 04 · See your week: hours per subject, points and a streak
This week and the Focus page show hours per subject, the session log, points and a streak, all computed in SQL from your real sessions and checked by tests.

- [ ] Add up this week's hours per subject in SQL
  One query returns hours per subject from Monday to Sunday of the current week, and the result matches your own hand count of a few sessions.
- [ ] Show hours per subject and the week bar
  The page title with week range and total, the hours per subject panel and subject hours rows on This week, plus the Focus week total, hours per subject legend and the week bar of barbells loaded with subject plates, show real numbers in a stable order.
- [ ] Show the session log grouped by day
  The session log panel groups sessions into day groups with date and day total, each session row shows subject colour, time, subject and points, and the empty rest-of-week line offers a Start focus button.
- [ ] Award points and count the weekly streak
  Points and the streak are worked out from the sessions themselves, so the streak and points pills, points preview, streak lines, streak panel, points earned this week and last 3 weeks list always agree with the log.
- [ ] Test the week maths you rely on
  Tests confirm weekly hours, week boundaries and streak counting on sample sessions, and you can read a failing test's message to find the broken line.

## 05 · Plan topics you can edit and check off
Each subject has a topic plan grouped by suggested week that you can check off, rename and move, and the Focus page shows your next topic.

- [ ] Add a topics table with suggested weeks
  A topics table belongs to subjects, and a seed script loads a few real math review topics with weeks so the plan has data to show.
- [ ] Show the Topic plan grouped by week
  The page title, subject switcher chips, topic plan panel, week groups and week labels with this-week marker show real topics, the switch is kept in the URL, each subject row's Plan link opens its plan, and the No plan yet empty state shows for a subject without topics.
- [ ] Check off topics
  Each topic row with done and next states has a topic checkbox, the server only allows valid status changes, the Next up tag moves on, the confirmation shows, and the progress bar and weeks done summary update.
- [ ] Show your next topic on the Focus page
  The current topic heading and the next topic card with Mark done show the earliest unchecked topic for the chosen subject, the marked done state appears after clicking, the plan links work, and the Up next panel on the plan matches.
- [ ] Rename topics and move them between weeks
  The Rename button opens an inline rename field with Save, the Move to week select moves a topic, and both work with the keyboard and a screen reader label.

## 06 · Turn a pasted syllabus into a topic plan
You paste a real course syllabus, the server asks a language model for topics with weeks, checks the answer, and you review the draft before saving it to your plan.

- [ ] Choose a model provider and call it from the server
  You pick a model provider, keep your API key in an environment variable, and a server route returns a real model reply without the key ever reaching the browser.
- [ ] Paste a syllabus and see draft topics
  The Paste a syllabus button opens the page with back to topic plan, page title, subject select and syllabus text area; Make my topic plan shows the Reading your syllabus notice, then the draft plan panel fills with draft topic rows of title, week and remove, or the draft empty state.
- [ ] Check the model's plan on the server
  Malformed JSON, missing weeks, empty titles or a slow model each produce a clear error response the page can show, and only a checked plan is returned.
- [ ] Judge plans against real syllabi
  You run three real syllabi through the endpoint several times, write down what a good plan looks like for each, and tests with a stand-in model prove the checker rejects bad answers.
- [ ] Review the draft and save it to your plan
  The topics and weeks check notice summarises the draft, Save to topic plan writes all topics in one go or none, the empty syllabus error and the Subjects missing name error explain themselves, and saved topics appear on the Topic plan.

## 07 · Ship Study Quest live and graduate
Study Quest runs at its own URL with a tested critical path, and you log a real math study session on it and walk through how it works.

- [ ] Push the project to GitHub through a pull request
  Your work lives on GitHub, and a branch with a small change is merged through a pull request whose diff you read line by line.
- [ ] Test the critical path against a fresh database
  An integration test builds the tables from migrations, adds a subject, logs a session and checks weekly hours, running against its own clean database every time.
- [ ] Deploy the API and database
  The Express API and its SQL database run on a host, configured by environment variables, and the health route answers at a public address.
- [ ] Put the React app online and connect it to the API
  The React app is live at its own URL and talks to the deployed API, which accepts requests only from your app's address.
- [ ] Run a real study session on the live app
  You log a real math review session and paste a real syllabus on the live URL, an end-to-end test repeats that path, the server logs each step, and the syllabus route limits how often it can be called on your API key.
