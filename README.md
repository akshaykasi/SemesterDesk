# Semester Desk

A study hub for engineering (CSE) students. It runs entirely in the browser: no build step, no server, no dependencies.

## What it does

| Tab | What you get |
| --- | --- |
| Overview | A "needs attention" list (low attendance, overdue deadlines) and a summary of every tool |
| CGPA | Credit-weighted SGPA per semester and overall CGPA on a 10-point or 4.0 scale, a CGPA-to-percentage factor, and a target planner that tells you the SGPA you need next semester |
| Attendance | Present/Absent buttons per subject against a minimum you set (75% by default), how many classes you can still skip, or how many you must attend in a row to recover |
| Tasks | Deadlines with priority, overdue and due-soon flags, open/done filters |
| DSA | Easy/medium/hard counts across 12 topics (add your own) against a target |
| Focus timer | Pomodoro timer with adjustable lengths, session log and a 7-day chart |
| Library | Search and filter 17 learning resources (courses, practice sites, tools) |

## Run it

Open `index.html` in a browser, or serve the folder:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

## Publish on GitHub Pages

1. Push this folder to a GitHub repository.
2. Open the repository's **Settings > Pages**.
3. Under **Build and deployment**, choose **Deploy from a branch**, pick `main` and `/ (root)`, then save.
4. Your site appears at `https://<your-username>.github.io/<repository-name>/` after a minute or two.

## Sign-in and your data

The login screen uses **device profiles**: type a name and you get your own profile in that browser.

- There is no password. Anyone who opens the page in the same browser can open any profile there.
- Data is stored in the browser's `localStorage`, one entry per profile. It never leaves the device. Clearing site data deletes it, and it does not follow you to another browser or device.
- The code also contains a "Continue with your Claude account" path. It only activates when the page is published as an artifact inside Claude, where it saves each person's data privately to their account. On GitHub Pages that option is hidden automatically.

Real passwords, or accounts that sync across devices, need a backend (for example Firebase or Supabase). This project does not include one.

## Customize

Everything lives in `js/app.js`:

- `SCALES` holds the grading scales (letter grades and their points). Edit it to match your university.
- `LIB` is the resource library. Add or remove entries.
- `DSA_DEFAULT` is the starting list of DSA topics.
- `sampleState()` is the example data new profiles start with.

The look is controlled by the color and font tokens at the top of `css/styles.css`. Light and dark themes follow the system setting.

## Tests

The tests run the real page in a simulated browser ([jsdom](https://github.com/jsdom/jsdom)) and cover the calculators, attendance maths, tasks, DSA counters, the timer, the library, and the sign-in and saving flows.

```bash
npm install
npm test
```

## Project layout

```
index.html          page markup (login screen and the app)
css/styles.css      styles and design tokens
js/app.js           all behaviour
tests/              jsdom tests (npm test)
```

## License

MIT. See `LICENSE`. Replace the copyright line with your own name if you like.
