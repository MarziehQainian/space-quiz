# Copilot instructions

## Project structure

The quiz is a single, self-contained `index.html`: semantic markup, inline CSS, question data, and plain JavaScript live together. There is no package manifest, framework, or build step. The `questions` array is the content source; `renderQuestion()` updates the active question, `selectAnswer()` handles scoring and feedback, `showResults()` displays the final state, and the restart handler resets the quiz.

## Build, test, and lint

- **Build:** No build command; open `index.html` directly in a browser.
- **Tests:** No automated test runner or single-test command. For a browser smoke test, check a correct and incorrect answer, score and progress updates, all 10 questions, the results screen, and restart.
- **Lint:** No lint command is configured.

When editing question data, keep each `answer` as the zero-based index of its correct `options` entry. The result score and caption currently assume 10 questions, so update them if the quiz length changes.

## UI and interaction conventions

- Keep the quiz dependency-free and self-contained in `index.html`.
- Use the CSS custom properties for colors and surfaces. The `prefers-color-scheme: light` override and the default dark palette should remain visually supported.
- Preserve native buttons for answers and actions, the progress bar's ARIA value attributes, and the feedback status region. The question heading is programmatically focusable so advancing moves focus to the new question; answer selection and results also move focus to the next action.
- Respect `prefers-reduced-motion`; feedback animations and transitions must not be required to understand an answer.
