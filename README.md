# Space Exploration Quiz

A responsive, mission-control-inspired quiz about space exploration. Answer ten
multiple-choice questions, learn a fact after each answer, and see your final
score, accuracy, and rank.

Features include automatic light and dark themes, an optional 15- or 20-second
countdown per question, personal-best statistics saved in your browser, keyboard
navigation, and reduced-motion support.

**Live app:** https://alankongfq.github.io/space-quiz/

## Run locally

The app is entirely contained in `index.html`, with embedded CSS and vanilla
JavaScript. No dependencies, installation, or build step are required.

Open `index.html` directly in a browser, or serve the repository with Python 3:

```sh
python3 -m http.server 8000
```

Then visit http://localhost:8000. Stop the server with `Ctrl+C`.

## Deployment

GitHub Pages uses GitHub Actions as its source. The workflow in
`.github/workflows/pages.yml` validates the embedded JavaScript and packages only
`index.html` as the website artifact. Pull requests targeting `main` run validation
without deploying. Pushes to `main` deploy automatically; the workflow can also be
run manually from the Actions tab on `main`.

Deployment uses the `github-pages` environment with `pages: write` and
`id-token: write` permissions. No deployment secrets are needed.
