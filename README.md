# Raider Pass Builder

Find any student's 1st-block room for tomorrow in seconds, and print counseling passes in walking order. Built for the Regis Jesuit counseling office.

**Live site:** https://rjedtech.github.io/Raider-Pass-Builder/

## What it does

1. **Download tomorrow's schedule from myRJ:** the *Student Schedule For The Day* report, exported to Excel. Blackbaud has already applied Red/White day and the six-week rotation for that date, so each student's earliest class is their 1st block.
2. **Send the counselors' calendars from Outlook:** with every counselor's calendar ticked in Outlook on the web (Day view, tomorrow), one click on the **Send to Pass Builder** favorites-bar button (a bookmarklet) reads the visible appointments and opens the builder with them already loaded (`postMessage`, origin-checked). It also copies them, so pasting is the fallback.
3. **Add the schedule file:** every student gets their 1st-block room, building, floor, teacher and Red/White day. If another Pass Builder tab already has the schedule open, the new tab takes it from there (`BroadcastChannel`, nothing stored).
4. **Check and print:** Check-Ins and entries titled with just a student's name become passes; uncertain names wait for a click; staff and personal events are skipped. The counselor comes from “By …” on the entry, or from the student's division and last name (the ranges on the School Counseling resource board). Passes print four to a letter page on the BD/GD layout in walking order from the BD Counseling Office (BD, then SIC and Steele, ending in GD), with a route sheet on page 1.

A one-student lookup box handles walk-ins. Matching handles preferred names, nicknames, hyphenated last names and small misspellings.
- Runs entirely in the browser. The schedule file and calendar entries never leave the computer and are gone when the page closes. Only the counselor list is remembered, in the browser.

## How it's built

One self-contained `index.html`, plus screenshots in `img/`. Libraries load from cdnjs:

| Library | Use |
|---|---|
| SheetJS 0.18.5 | read the myRJ `.xls` export |
| jsPDF 2.5.1 + AutoTable 3.8.2 | build the route sheet and passes |

## Things to keep up to date

- **Counselor list** (`DEFAULT_COUNSELORS`): names, pass names, BD/GD division and last-name ranges from the School Counseling resource board in myRJ. All editable on the page.
- **Walking order** (`BUILDING_ORDER`, `WALK`): from the 2022 floor plans. Rooms not in the list fall in after their building's list.
- **Screenshots:** myRJ and Outlook pictures are real, taken in October 2026 at full resolution; the Outlook ones show only the calendar list and toolbar (no counselor appointments). Builder pictures are 2× captures with made-up example students. Retake them if myRJ or Outlook moves the buttons.
