# Taskify

A single-file task board: columns you can rename and recolour, drag & drop, project tags, deadline warnings, subtasks with checkboxes on the card, and sync to a secret GitHub Gist.

## Put it online with GitHub Pages

1. Create a repository, e.g. `taskify`.
2. Upload `index.html`, `icon.svg` and this README to the repository root.
3. Go to **Settings → Pages**, set *Source* to `Deploy from a branch`, branch `main`, folder `/ (root)`, and save.
4. After a minute the board is live at `https://<your-user>.github.io/taskify/`.

Nothing is built or bundled — it's one HTML file with no dependencies, so a plain upload is enough. Opening the file directly from disk works too, except that gist sync needs `http(s)`.

## Gist sync

1. Create a token at **github.com/settings/tokens**. A classic token needs only the `gist` scope; a fine-grained token needs the *Gists* permission set to *Read and write*.
2. In Taskify, open **Gist sync**, paste the token, then click **Create new gist**. That makes a secret gist called `taskify-board.json` and saves the current board into it.
3. On another machine, paste the same token and gist ID (a full gist URL works too) and click **Load from gist**.
4. Tick **Save automatically after changes** to push edits every few seconds.

The dot on the sync button shows the state: grey not connected, amber unsaved changes, green saved, red an error worth reading in the dialog.

### About the token

The token stays in your browser's local storage and goes only to `api.github.com`. Anyone with the token can read and write all your gists, so treat it like a password: prefer a fine-grained token limited to gists, give it an expiry date, and use **Forget token** on shared machines. A secret gist is not encrypted — it's unlisted, not private — so don't put confidential project data on the board.

## Local data

Without gist sync the board lives in memory for the session only. **Export** writes a JSON file, **Import** reads one back, and the same format is what the gist stores, so the two are interchangeable.
