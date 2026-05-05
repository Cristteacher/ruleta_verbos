# Ruleta de Verbos

Spanish verb conjugation game built as a single-file React/Tailwind app in `index.html`.

## What this project contains

- `index.html` — complete app source with React components, game logic, UI, and persistence
- `.github/copilot-instructions.md` — internal project guidance for contributors and AI assistants

## Run locally

1. Open `index.html` in your web browser.
2. The app loads directly without build tools.
3. For a simple local server, you can run from the project folder:
   - Python 3: `python -m http.server 8000`
   - Then open `http://localhost:8000`

## Deployment

### GitHub Pages

1. Create a new GitHub repository for this project.
2. Add `index.html` and `README.md` to the repository root.
3. Commit and push to GitHub.
4. In the repository on GitHub, go to `Settings` → `Pages`.
5. Set the source to `main` branch (or the branch you use) and root `/`.
6. Save and wait a few moments for GitHub Pages to publish.
7. Your live site will be available at `https://<your-username>.github.io/<repo-name>/`.

### Netlify

1. Sign up at [netlify.com](https://www.netlify.com/) if you do not already have an account.
2. Choose "New site from Git".
3. Connect your GitHub repository.
4. Select the repository for this project.
5. For build settings, leave the build command blank and set the publish directory to `/`.
6. Deploy the site.
7. Netlify will provide a live URL immediately.

## Recommended workflow

1. Create a Git repository in this folder if you want version control.
2. Commit `index.html` and `README.md`.
3. Push to GitHub.
4. Deploy via GitHub Pages or Netlify.

## Notes

- The app does not require a build step.
- All dependencies are loaded from CDNs.
- `localStorage` is used to save progress, badges, and the feedback toggle setting.

## If you want help with publishing

I can also provide the exact Git commands to:

- initialize a git repository
- make the first commit
- push the code to GitHub
- connect the repository to GitHub Pages or Netlify
