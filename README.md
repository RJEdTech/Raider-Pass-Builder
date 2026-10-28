# Raider Pass Builder

Find any student's 1st-block room for tomorrow in seconds. Built for the Regis Jesuit counseling office, so counseling passes can be delivered at the start of 1st block.

**Live site:** https://rjedtech.github.io/Raider-Pass-Builder/

## What it does

1. **Download tomorrow's schedule from myRJ:** the *Student Schedule For The Day* report, exported to Excel. Blackbaud has already applied Red/White day and the six-week rotation for that date, so each student's earliest class is their 1st block.
2. **Add the file, then look up each student:** type any part of a name from a counselor's calendar and the 1st-block room shows in big letters, with the building, floor, teacher and Red/White day. Clicking back into the box highlights the last name, so the next one types right over it. Matching handles preferred names, nicknames, hyphenated last names and small misspellings.

Runs entirely in the browser. The schedule file never leaves the computer and is gone when the page closes.

## Parts still being built

These are in the code but switched off (`CALENDAR_PARTS = false` in the script, and the hidden `#laterParts` block on the page). The Outlook import didn't work in the counseling office's Outlook, so the page is just the two steps above for now.

- **Outlook calendar import:** a *Send to Pass Builder* favorites-bar button (bookmarklet) that read the visible appointments in Outlook on the web and sent them to the page (`postMessage`, origin-checked), with paste as a fallback.
- **Appointment list:** Check-Ins and name-only entries became passes; staff and personal events were skipped; the counselor came from “By …” on the entry or from the student's division and last name.
- **Room list and passes:** a sortable *Rooms for tomorrow* list (walking order from the BD Counseling Office, counselor, or last name), a one-page room list, and passes printed four to a letter page on the BD/GD layout.

To bring them back, set `CALENDAR_PARTS = true`. A likely next route for the calendars is Power Automate rather than the bookmarklet.

## How it's built

One self-contained `index.html`, plus screenshots in `img/`. Libraries load from cdnjs:

| Library | Use |
|---|---|
| SheetJS 0.18.5 | read the myRJ `.xls` export |
| jsPDF 2.5.1 + AutoTable 3.8.2 | route sheet and passes (parts still being built) |

## Things to keep up to date

- **Screenshots:** the myRJ pictures are real, taken in October 2026 at full resolution. Builder pictures are 2× captures with made-up example students. Retake them if myRJ moves the buttons.
- **Counselor list** (`DEFAULT_COUNSELORS`) and **walking order** (`BUILDING_ORDER`, `WALK`): only used by the parts still being built.
