# countdown-timer

A single-page countdown to January 1, 2027 with a 30-day build-sprint tracker underneath. The top half is a live days/hours/minutes/seconds countdown; the bottom half is a "30 Days · 30 Builds" checklist — thirty small projects grouped into four themed weeks, each day with two checkboxes (**Project** shipped, **Brag** posted) — plus stat tiles for days fully done, current streak, projects shipped, and brags posted.

Live at https://vaibhavgit9210.github.io/countdown-timer/

## How it works

Everything is in one `index.html` — no framework, no build step.

- The countdown is a 1-second `setInterval` against a fixed target date (`Jan 1, 2027`); when it passes, the cells are replaced with a done message.
- The sprint is a hardcoded list of 30 builds (7+7+7+9 across four weeks). Day 1 is the day you first open the page; the start date and checkbox state live in localStorage.
- Cross-device sync is a plain-`fetch` PUT/GET of the state blob to a Firebase Realtime Database URL — no SDK, no auth, last write wins. If the network call fails, the page falls back to device-local state and shows an offline badge.
- A footer button resets all checkboxes and restarts the 30 days from today.

## Running locally

Open `index.html` in any browser. State persists in localStorage; the Firebase sync only matters if you want the same checklist on multiple devices (point `DB` in the script at your own Realtime Database URL).
