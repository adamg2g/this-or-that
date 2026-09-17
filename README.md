# This or That

A 4-player party game in a single HTML file. Players open the same URL, enter their names, and once 4 have joined the game runs 5 rounds of "this or that" questions. After each round, a reveal screen shows a token with each player's initials under the option they chose.

**Architecture:** one static `index.html`, no database, no server code. Real-time sync uses Supabase Realtime channels — Presence for the lobby, Broadcast for answers. Nothing is ever persisted.

## Changing the questions

Edit the `QUESTIONS` array at the top of the `<script>` block in `index.html` — one `{ a, b }` pair per round (the round count follows the array length), where `a` is the coral card and `b` is the teal card.

## Running locally

```sh
python3 -m http.server 8080
```

Then open `http://localhost:8080` in 4 tabs (mix normal and private windows). Everyone on the page shares one fixed room, so only one group can play at a time; the **Play again** button (or a refresh all round) resets everyone to the lobby.
