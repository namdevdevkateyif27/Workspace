# YIF Schedule Companion

A browser-local demo that helps a fellow compare YIF schedule updates with a sample timetable. It includes a weekly view, sample messages, source-linked change review, confirm/dismiss/undo actions, CSV timetable import, catch-up history, and `.ics` export.

## Run the demo

Open `public/index.html` in a modern browser. Schedule data and review actions stay in that browser's local storage. The app starts with fictional/sample data for the week of 5 October 2026.

The app uses a local demo parser unless the Worker endpoint has an OpenAI API key. To enable AI extraction on Sites, configure `OPENAI_API_KEY` as a secret in the Site's runtime environment. The key is read only by the Worker and never sent to the browser. The Worker endpoint sends the submitted message text to OpenAI for extraction; use synthetic or consented examples for demos.

## Sites Worker source

- `worker/index.js` is the deployed Worker and embeds the matching HTML page.
- `public/index.html` is the readable UI source.
- `.openai/hosting.json` contains the Site project configuration.
- `scripts/build.sh` builds the deployment artifact in `dist/`.
- `scripts/validate-artifact.mjs` checks the built Worker artifact.

The demo is not connected to a YIF mailbox or a live programme calendar. It does not implement email forwarding, user accounts, shared storage, or automatic calendar writes. Each browser has its own data.
