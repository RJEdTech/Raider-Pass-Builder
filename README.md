# Raider Pass Builder

Find any student's 1st-block room for tomorrow in seconds, and print counseling passes in walking order. Built for the Regis Jesuit counseling office.

**Live site:** https://rjedtech.github.io/Raider-Pass-Builder/

## What it does

- **Step 1:** reads myRJ's *Student Schedule For The Day* report (Excel export) for tomorrow's date. Blackbaud has already applied Red/White day and the six-week rotation for that date, so the earliest class each student has is their 1st block.
- **Step 2 (the main job):** type part of any student's name, or paste a calendar line like `Check-In: First Last`, and see their 1st-block room, building and floor, teacher, course and Red or White day. Matching handles preferred names, nicknames, hyphenated last names and small misspellings.
- **Step 3 (optional):** paste a counselor's whole Outlook calendar (copied with the *Copy calendar* favorites-bar button). Check-Ins and entries titled with just a student's name become passes; anything uncertain waits for a click; staff and personal events are skipped. Passes print four to a letter page on the BD/GD pass layout, sorted in walking order from the BD Counseling Office (BD, then SIC and Steele, ending in GD), with a route sheet on page 1.
- Runs entirely in the browser. The schedule file and calendar entries never leave the computer and are gone when the page closes. Only the counselor list is remembered, in the browser.

## How it's built

One self-contained `index.html`, plus screenshots in `img/`. Libraries load from cdnjs:

| Library | Use |
|---|---|
| SheetJS 0.18.5 | read the myRJ `.xls` export |
| jsPDF 2.5.1 + AutoTable 3.8.2 | build the route sheet and passes |

## Things to keep up to date

- **Counselor list** (`DEFAULT_COUNSELORS`): from the School Counseling resource board in myRJ. Each person's name on the pass and BD/GD division can also be edited on the page.
- **Walking order** (`BUILDING_ORDER`, `WALK`): from the 2022 floor plans. Rooms not in the list fall in after their building's list.
- **Screenshots:** taken from myRJ and Outlook on the web in October 2026. Builder screenshots use made-up example students. Retake them if myRJ or Outlook moves the buttons.
