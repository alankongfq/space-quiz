# Copilot Instructions for Space Quiz

## Architecture & Project Overview
- **Single-File Architecture**: The application is a self-contained vanilla web application residing entirely inside `index.html` (embedded CSS, semantic HTML, and vanilla JavaScript).
- **Core State Machine**:
  - `questions`: In-memory array containing objects with `category`, `question`, `options`, `answer` (0-indexed integer), and educational `fact`.
  - State tracked via `currentQuestionIdx`, `score`, and `answered`.
  - Views toggled via display properties on `#quizView` and `#resultsView`.
- **UI & Theming**:
  - CSS custom properties (`:root`) govern both light and dark themes via `@media (prefers-color-scheme: dark)`.
  - Designed with an aerospace/mission-control aesthetic, featuring responsive layouts and a subtle background star field.

## Development, Testing & Verification
- **Running Locally**:
  - No build step or package manager dependencies (`package.json`) required.
  - Open `index.html` directly in any web browser (`file:///.../index.html`) or serve via a static web server (e.g., `python3 -m http.server 8000` or `npx serve .`).
- **Syntax Verification**:
  - Verify embedded JavaScript syntax without running a browser using Node:
    ```bash
    node -e 'const fs=require("fs");const s=fs.readFileSync("index.html","utf8");const js=s.match(/<script>([\s\S]*?)<\/script>/)[1];new Function(js);console.log("Syntax OK")'
    ```
- **Browser Testing**:
  - Test interactively or via browser automation/canvases.
  - Verify keyboard accessibility (Tab, Enter) through all options, Next button, and the restart button.

## Key Conventions & Constraints
- **Zero Build Dependencies**: Keep the application entirely static and dependency-free unless explicitly instructed to migrate to a framework or bundler.
- **Accessibility & Motion Compliance**:
  - Maintain WCAG compliance with proper ARIA roles (`role="progressbar"`, `role="status"`, `aria-live="polite"`).
  - Manage programmatic focus when transitioning questions and reaching results (`#questionText.focus()`, `#nextBtn.focus()`, `#resultsHeadline.focus()`).
  - Honor `@media (prefers-reduced-motion: reduce)` by disabling transitions/animations and halting the background star drift.
- **Question Schema**:
  - Any added question must follow the exact structure:
    ```javascript
    {
      category: "Category Name",
      question: "Question prompt text?",
      options: ["Option A", "Option B", "Option C", "Option D"],
      answer: 0, // 0-based index of the correct option
      fact: "Contextual explanation displayed after an answer is submitted."
    }
    ```
