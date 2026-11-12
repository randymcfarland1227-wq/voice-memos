# Voice Memos

A phone voice-memo recorder that syncs every saved recording into **Randy's Life Hub → Self inbox**.

- Live: https://randymcfarland1227-wq.github.io/voice-memos/ — add it to the home screen.
- Optional subject, type (Thought / Idea / To-do / Journal / Meeting / Reminder), "Logged for" date & time, notes/transcript; pause/resume; typed-only memos (no audio) work too.
- Plain HTML/JS (`index.html`), no build step. Push to `main` = live (GitHub Pages).
- Sync: recording → IndexedDB queue (works offline) → Life Hub Worker `PUT /api/files` → `PUT /api/state` with one capture `{ kind: 'voice', focusAreaId: 'self', loggedAt, memoType, audio?: { fileId, type, seconds, size } }`.
- Auth: the Life Hub backup key. Same github.io origin as Life Hub, so in the same browser it's picked up automatically; a home-screen app asks once for Life Hub's "Link another device" link.
- Life Hub shows them in a foldable Voice memos section in Self (frontier-next `app/components/VoiceMemoList.tsx`).
