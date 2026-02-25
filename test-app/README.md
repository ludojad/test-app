# 📚 Quiz CLI

An interactive command-line quiz game for testing and improving your programming knowledge — built entirely with **Node.js built-ins**, no external dependencies required.

---

## 📖 Overview

Quiz CLI is a terminal-based multiple-choice quiz application written in modern JavaScript (ES Modules). It presents questions across multiple programming categories, tracks your score, provides instant feedback with explanations, and shows a summary of results at the end of each round.

**Intended users:** Developers learning JavaScript/Node.js fundamentals, or anyone looking for a lightweight, educational CLI quiz tool.

---

## ✨ Features

- 🗂️ **Multiple quiz categories** — JavaScript Basics, Node.js Fundamentals, General Programming
- 🔀 **Randomized question order** — questions are shuffled on every run using the Fisher-Yates algorithm
- 🔢 **Configurable question count** — choose to answer 3, 5, or all available questions per session
- 💡 **Instant feedback** — each answer shows whether you were correct, the right answer (if wrong), and a short explanation
- 📊 **Results summary** — final score with percentage, performance message, and a review of all incorrectly answered questions
- 📈 **Progress bar** — visual indicator of how far through the quiz you are
- 🎨 **Colorized output** — ANSI terminal colors using zero external packages
- 🔁 **Play again loop** — keep playing different categories without restarting the app

---

## 🛠️ Prerequisites

| Requirement | Version  |
|-------------|----------|
| Node.js     | >= 18.0.0 |
| npm         | >= 8.x (bundled with Node 18) |

> No third-party packages are required. The project relies solely on Node.js built-in modules (`readline`, `fs/promises`, `path`, `url`).

---

## 🚀 Installation

1. **Clone the repository:**

```bash
git clone https://github.com/ludojad/test-app.git
cd test-app/test-app
```

2. **Verify your Node.js version:**

```bash
node --version
# Expected: v18.x.x or higher
```

3. **No dependencies to install** — the project has no external `npm` packages.

---

## ▶️ Running the Application

Start the quiz from the project root:

```bash
npm start
```

Or run it directly with Node:

```bash
node index.js
```

---

## 🎮 Usage

Once started, the application guides you through the following steps interactively:

### 1. Choose a Category

```
Choose a category:

  1. JavaScript Basics
  2. Node.js Fundamentals
  3. General Programming

Your choice (enter number):
```

### 2. Select Number of Questions

```
How many questions?

  1. All questions
  2. 3 questions
  3. 5 questions

Your choice (enter number):
```

### 3. Answer Questions

Each question displays a progress bar and multiple-choice options:

```
[████████████░░░░░░░░░░░░░░░░░░] 40%
Question 2 of 5

What does '===' check for?

  1. Value only
  2. Type only
  3. Value and type
  4. Reference

Your choice (enter number): 3

✓ Correct!
💡 The strict equality operator (===) checks both value and type without coercion.
```

### 4. View Results

At the end of the quiz, a full summary is displayed:

```
══════════════════════════════════════════════════
  📊 QUIZ RESULTS
══════════════════════════════════════════════════

  Category: JavaScript Basics
  Score: 4/5 (80%)

  🌟 Great job! Well done!

══════════════════════════════════════════════════

📝 Review these questions:

1. What is the output of: typeof null?
   Your answer: 'null'
   Correct: 'object'
```

### 5. Play Again

```
Would you like to play again? (y/n):
```

---

## 🧪 Running Tests

The project includes a basic test script using Node.js's built-in test runner (available from Node.js v18+):

```bash
npm test
```

> **Note:** No test files are currently present in the repository. The `test` script is pre-configured and ready for test files to be added under the project directory.

---

## 📁 Project Structure

```
test-app/
├── index.js               # Application entry point — main loop, banner, orchestration
├── package.json           # Project manifest, scripts, and engine requirements
├── data/
│   └── questions.json     # Quiz question bank (categories, options, answers, explanations)
└── src/
    ├── colors.js          # ANSI terminal color/style utilities (no dependencies)
    ├── input.js           # User input helpers: prompt, select, confirm, pressEnter
    └── quiz.js            # Quiz class — game logic, scoring, progress, result display
```

### Key File Descriptions

| File | Purpose |
|------|---------|
| `index.js` | Entry point. Loads questions, renders the welcome banner, and manages the main play loop. |
| `data/questions.json` | JSON question bank with categories. Each question has options, a correct answer index, and an explanation. |
| `src/quiz.js` | `Quiz` class encapsulating all game logic: shuffling, tracking progress, evaluating answers, rendering results. |
| `src/input.js` | Async wrappers around Node.js `readline` for structured user interaction (menus, yes/no, press-enter prompts). |
| `src/colors.js` | Lightweight color utility using raw ANSI escape codes. Exports helpers like `success`, `error`, `info`, `highlight`, etc. |

---

## 📝 Question Bank

Questions are stored in `data/questions.json` and organized by category:

| Category ID   | Display Name             | Questions |
|---------------|--------------------------|-----------|
| `javascript`  | JavaScript Basics        | 5         |
| `nodejs`      | Node.js Fundamentals     | 5         |
| `general`     | General Programming      | 5         |

### Adding New Questions

To extend the quiz, edit `data/questions.json` and follow this structure:

```json
{
  "question": "Your question text here?",
  "options": ["Option A", "Option B", "Option C", "Option D"],
  "answer": 0,
  "explanation": "Brief explanation of why the correct answer is correct."
}
```

> `answer` is a **zero-based index** pointing to the correct entry in the `options` array.

### Adding New Categories

Add a new top-level key under `categories`:

```json
"python": {
  "name": "Python Basics",
  "questions": [ ... ]
}
```

No code changes are needed — the app dynamically reads all categories from the JSON file.

---

## ⚙️ Environment Variables

This project does **not** require any environment variables. All configuration is handled through the `data/questions.json` file and command-line interaction.

---

## 🏗️ Technical Notes

- **ES Modules** — The project uses `"type": "module"` in `package.json`, so all files use `import`/`export` syntax.
- **No `__dirname`** — Since ES Modules don't expose `__dirname`, the entry point uses `fileURLToPath` + `dirname` from `node:url` and `node:path` to resolve the data file path correctly.
- **Zero dependencies** — All functionality (colors, readline, file I/O, path resolution) relies entirely on Node.js built-in modules.
- **Fisher-Yates shuffle** — Questions are randomized each session using an unbiased in-place shuffle algorithm.

---

## 📄 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.

---

## 🤝 Contributing

Contributions are welcome! Here's how to get started:

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/my-feature`
3. Make your changes
4. Run tests: `npm test`
5. Submit a Pull Request

Some ideas for contributions:
- Add more question categories (e.g., Python, HTML/CSS, Git)
- Implement a high-score/leaderboard system
- Add timed questions
- Support loading custom question files via a CLI argument
