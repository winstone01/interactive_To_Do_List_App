# Interactive To-Do List Dashboard

A personal task dashboard built by **Winstone Anderson** using HTML, CSS and vanilla JavaScript. It combines task management with colour-coded status badges, priority indicators, a results summary and subtle hover effects.

This project explores how layout, visual feedback and JavaScript state work together to create an interactive interface without a front-end framework.

## Features

- **Create and edit tasks** through an Add / Update modal.
- **Set task status:** Pending, In Progress or Completed.
- **Set task priority:** Minor, Normal or Critical, shown with labels and coloured dots.
- **Complete or reopen tasks** using the circular task control.
- **Delete tasks** after confirming the action.
- **Separate active and completed tasks** into their own sections.
- **Save tasks locally** so changes survive a page refresh in the same browser and site.
- **View summary statistics:** total tasks, completed tasks, remaining tasks and completion percentage.
- **See a personalised greeting** based on the time when the page loads.
- **Enjoy hover feedback:** task cards slide slightly, buttons lift, and header buttons change colour.
- **Adapt the main layout** from two columns to one at viewport widths of 1024px or below.

## Built With

| Technology | Purpose |
| --- | --- |
| HTML5 | Dashboard structure, form and controls |
| CSS3 | Grid and Flexbox layouts, colour palette, badges, modal and transitions |
| JavaScript | Task data, rendering, form handling and statistics |
| Web Storage API | Browser-local persistence through `localStorage` |
| Font Awesome | Search, notification, profile, add, edit and delete icons |
| Google Fonts | Source Sans 3 typography |

No package installation, build step or backend is required. Fonts and icons are loaded from external services and need an internet connection to load normally.

## Project Files

| File | Contents |
| --- | --- |
| `index.html` | Dashboard, summary cards and task form |
| `style.css` | Layout, styling, hover effects and breakpoint |
| `script.js` | Task operations, persistence and summary calculations |
| `README.md` | Project documentation |

## Run Locally

1. Download or clone the project.
2. Keep the HTML, CSS and JavaScript files together in the same directory.
3. If using the timestamped export files, rename them to `index.html`, `style.css` and `script.js`. These are the filenames referenced by the HTML.
4. Open the folder in VS Code and serve `index.html` with Live Server, or use another local static web server.
5. Open the local address in your browser.

Use the same local address when returning to the app: browser storage belongs to a particular origin. Opening the HTML directly may display the app, but serving it locally gives more predictable storage behaviour.

## How to Use

1. Select **Add New Task**.
2. Enter a task title, choose a status and select a priority.
3. Select **Save Task**, or **Cancel** to close the form without saving.
4. Use the pencil button to update an existing task.
5. Use the circular control to mark a task complete or return it to Pending.
6. Use the bin button to delete a task and confirm the prompt.

The **On Hold** section contains all unfinished tasks, including tasks marked In Progress. The heading count and the summary's **Pending** figure both count all unfinished tasks. The heading's “today” wording does not represent a date filter; this version does not store due dates.

## Data and Statistics

Each task stores an `id`, `title`, `status`, `priority` and `completed` flag. New tasks receive an ID from `Date.now()`.

Tasks are saved as JSON under the local storage key **`flowTaskToDo`**. The first visit loads four sample tasks when no saved data exists. Clearing browser storage removes saved tasks; they are not synced between devices or browsers.

Completion rate is calculated as:

```text
round((completed tasks / total tasks) × 100)
```

An empty list displays 0%. Both progress bars currently display this completion percentage, including the bar beneath Total Tasks.

To restore the sample data, remove only this app's storage key in the browser developer console and reload the page. This deletes the currently saved task list:

```js
localStorage.removeItem("flowTaskToDo");
location.reload();
```

## Current Scope and Development Notes

- The search field, notification button and profile button are styled interface elements. Search filtering, notifications and account management are not implemented.
- The greeting uses the name Winstone, and task avatars display fixed `CF` initials. These can be customised in `script.js`.
- The uploaded completed-task template has a missing closing quote in its title element. Its intended markup is `<div class="task-title completed">${t.title}</div>`. The completed-task `.map()` result also needs `.join("")`, as used by the active-task renderer, to avoid commas between multiple completed cards.
- Further polish could include improved text contrast, accessible names for icon buttons, keyboard-operable completion controls, modal focus handling and additional layout adjustments for narrow screens.
- Task titles are currently inserted into HTML template strings. Rendering titles as plain text would make arbitrary user-entered content safer and more reliable.

## What This Project Demonstrates

- Managing a task collection with arrays, objects, `find()`, `filter()` and `map()`.
- Implementing create, read, update and delete operations in the browser.
- Keeping the displayed task list and summary statistics in sync.
- Handling form submissions and rejecting empty titles.
- Persisting application state with JSON and `localStorage`.
- Combining Grid, Flexbox, transitions and status colours in a dashboard interface.

## Author

**Winstone Anderson** — UI-focused front-end developer in London.

- GitHub: [winstone01](https://github.com/winstone01)
- Portfolio: [winstoneanderson.com](https://winstoneanderson.com)

