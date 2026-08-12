# Repository Instructions

## Firebase deployment

- The production Firebase project and Hosting site are both `khatm-dua`. The live URL is <https://khatm-dua.web.app>.
- `khatm_dua.html` is the Firebase deployment source of truth. No build or copy step is required.
- Firebase Hosting publishes from the repository root, but `firebase.json` ignores repository-only files. In particular, `index.html` is the GitHub Pages redirect and must remain excluded from Firebase Hosting.
- The Hosting rewrite serves `khatm_dua.html` directly at `/` while keeping `/khatm_dua.html` available.
- Before deploying, run `git diff --check` and `xmllint --html --noout khatm_dua.html`.
- Deploy the live site only when explicitly requested, using:

  ```bash
  npx --yes firebase-tools@latest deploy --only hosting
  ```

- After deploying, verify that <https://khatm-dua.web.app> returns the expected page. When exact verification is useful, compare the SHA-256 digest of the live response with `khatm_dua.html`.
- Do not commit Firebase authentication tokens, CLI caches, or generated deployment artifacts.
