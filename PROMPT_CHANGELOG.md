# Prompt Changelog

This document tracks all changes made to the codebase in response to user prompts. Each entry documents the date, the original prompt, and an overview of the changes implemented.

## Instructions for AI Assistants

When adding a new entry to this changelog:
1. Add entries in reverse chronological order (newest first)
2. Use the exact format shown in the template below
3. Include the date in YYYY-MM-DD format
4. Copy the exact prompt text from the user
5. Provide a clear, concise overview of all changes made
6. List all files that were modified, created, or deleted (optional but recommended)
7. Maintain consistency with existing entries

## Entry Template

```markdown
---

## [YYYY-MM-DD] - Brief Description

**Prompt:**
```
[Exact prompt text from the user]
```

**Overview:**
[Clear summary of what was changed, why, and how. Include any important implementation details, patterns used, or architectural decisions. Write it in a format where the text can be copy and pasted into a git commit. For example specifically in this section when wanting to type the character ' or " add a \ beforehand so I can add it to the commited changes comment.]

**Files Changed:**
- `path/to/file1.tsx` - Description of changes
- `path/to/file2.ts` - Description of changes
- `path/to/newfile.tsx` - Created new file for [purpose]

**Additional Notes:**
[Any relevant notes, considerations, or follow-up items]
```

---

## Changelog Entries

---

## [2026-04-25] - Firebase init, session identity, and Firestore wiring

**Prompt:**
```
Plan: Cursor Prompt 01 — Firebase Init + Session Identity

Implement the plan as specified, it is attached for your reference. Do NOT edit the plan file itself.

To-do's from the plan have already been created. Do not create them again. Mark them as in_progress as you work, starting with the first one. Don't stop until you have completed all the to-dos.
```

**Overview:**
Wire `index.html` to Firebase v10 (ESM CDN imports in a single `<script type="module">`), add `gstatic` preconnect in `<head>`, and use `sessionStorage` for `impostor_session_id` and `impostor_player_name` with `window.prompt` on first name entry (abort create/join on cancel). Remove dev nav, screens 4/6/7 preview demo markup, and local-only mock state; add `mergeLobbyFromServer`, `onSnapshot` on `lobbies/{code}` with `onLobbyUpdate` for spec auto-navigation, host-only impostor-disconnect reveal, and `setConnected` on `beforeunload`/`visibilitychange`. Implement Screen 1 create (randCode collision retry, `setDoc`) and join (`getDoc`, `updateDoc` for new player), then wire lobbies, word pot, start/reveal, back-to-lobby, and new round through Firestore. Role cards use `state.sessionId === state.lobby.impostorId`; result screen uses host vs player from `state.sessionId === state.lobby.hostId` (no `postView` toggles). Expose `goto`, `newRound`, and `backToLobby` on `window` for existing inline `onclick` handlers. No CSS or panel-layout edits beyond the listed HTML removals.

**Files Changed:**
- `index.html` - Firebase ESM, Firestore CRUD and listeners, session identity, HTML removals (dev nav, demo controls)
- `PROMPT_CHANGELOG.md` - This entry

**Additional Notes:**
Orphaned `.devnav` / `.demo-controls` CSS left in place per no-CSS-changes rule.

---

