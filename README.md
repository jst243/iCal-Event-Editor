Bulk iCal Generator
Create and manage multiple calendar events rapidly, then export them in one .ics file compatible with Outlook, Apple Calendar, Google Calendar, and others. Includes three views—Cards, List, and an interactive Calendar—plus an accessible modal editor and bulk actions.
Why this exists
Accelerate curriculum and schedule building (meetings, labs, clinicals, workshops) and share as a single calendar import.
Table of Contents
Features
Live Usage (no build)
File & Dependencies
How to Use
  • Add / Edit / Delete
  • Views: Cards / List / Calendar
  • Bulk Export to ICS
  • Selection & Bulk Delete
ICS Details & Parity With Original
Accessibility & Responsiveness
Troubleshooting
Customization
Roadmap Ideas
License
Features
Three views: Cards (tiles with quick edit/delete), List (dense table-like rows with Title, Date, Time/All‑day, Location, Show As, Reminder, Priority), and Calendar (month/week/day grid with click-to-add and click-to-edit).
Modal editor with All‑day toggle, 12/24‑hour conversions behind the scenes, and end‑date/time fallbacks.
Bulk export to a single .ics (iCalendar) file, including VALARM reminders, Microsoft BusyStatus / TRANSP, and priority mapping.
Selection & bulk delete (Select All / Deselect All).
Mobile‑first, responsive UI with accessible labels and keyboard support.
No build step needed—just open the HTML file.
Live Usage (no build)
Save the provided file as bulk-ical-generator.html.
Double‑click to open it in your browser (or serve locally using any static server).
You’re ready to add events and export a .ics.
Tip: If your organization restricts CDNs, see File & Dependencies for how to switch to local assets.
File & Dependencies
This project is intentionally single‑file and client‑only:
bulk-ical-generator.html
It references the following CDN dependencies:
Tailwind CSS (utility-first styling)
Lucide Icons (SVG icon set)
FullCalendar (interactive calendar view)
If you need to go offline or pin versions, download those assets locally and change the <link> / <script src> tags accordingly.
How to Use
Add / Edit / Delete
Add Event: Click Add Event (or click a date in Calendar view). A modal opens.
Required: Title and Start Date. If not an all‑day event, also set a Start Time.
All‑day: Check “All day event” to hide time fields.
End date/time: If left blank, it mirrors the start date/time for convenience.
Save to store the event; Cancel (or clicking the backdrop) discards a brand‑new untitled draft automatically.
Delete: Use the Delete button on a card/list row or bulk delete.
Views: Cards / List / Calendar
Cards: best for quick scanning with visuals.
List: compact rows showing key fields; less‑critical columns hide on small screens.
Calendar: Month/Week/Day grid. Click a date to add a draft event; click an event to edit. Use Prev/Next/Today to navigate.
Bulk Export to ICS
The Download (N) button is enabled when at least one event is valid: Title + Start Date (+ Start Time unless all‑day).
Clicking Download saves bulk-events.ics containing all valid events.
Selection & Bulk Delete
Use Select All / Deselect All in the header.
When one or more items are selected, a red Delete (N) button appears to bulk-remove.
ICS Details & Parity With Original
All‑day events use DTSTART;VALUE=DATE / DTEND;VALUE=DATE. Timed events use DTSTART/DTEND.
VALARM reminders are emitted using TRIGGER:-PT{minutes}M when a reminder is set.
Microsoft Busy Status (X-MICROSOFT-CDO-BUSYSTATUS) and TRANSP mapping for Free vs. Busy are included.
Priority mapping: HIGH→1, NORMAL→5, LOW→9.
End date/time defaults to start when omitted; title defaults to “Untitled Event” for display (Download enables on real title).
Times are exported as local times (no trailing Z); most calendar apps import as local time.
Accessibility & Responsiveness
Keyboard & Screen Reader: Labeled form elements, aria-modal on the dialog, focus placed in Title on open.
Mobile-first: Buttons stack, modal becomes a full-height sheet on small screens, list columns hide progressively.
Cards grid uses auto-fill with minmax() so tiles adapt fluidly to viewport changes.
Troubleshooting
Buttons don’t work / UI unstyled: Ensure the environment can reach the CDNs (Tailwind, Lucide, FullCalendar). If blocked, vendor assets locally and update tags.
Can’t download .ics: Ensure at least one valid event (Title + Start Date + Start Time unless all‑day).
Calendar visible but clicks do nothing: Verify FullCalendar script loaded (check console for network errors).
Customization
Branding: Swap Tailwind utility colors to match your palette.
Icons: Replace Lucide with any SVG or another set.
Fields: Add columns (Instructor, Room, Cohort) to List view and extend the editor.
Offline: Vendor JS/CSS locally and remove CDN tags.
Persistence: Add localStorage/indexedDB to persist events across refreshes.
Import/Export: Add CSV to bulk‑load sessions for academic schedules.
Drag & Drop: Enable moving/resizing in the Calendar and auto‑update the store.
Roadmap Ideas
Inline quick‑edit in List view (title/date/time without opening the modal).
Tagging/color‑coding by Show As or Priority across views.
Timezone selector and optional UTC (Z) exports.
Multi‑file export: one .ics per cohort/track.
Packaging as a React component or Web Component.
License
MIT (or your preferred license). Replace this section as needed.
Attribution & Parity Notes
This implementation preserves core behavior from the original bulk-ical-generator.tsx component: event schema and defaults, time conversion helpers, all‑day vs. timed formatting, reminder VALARM, Busy/Free/Tentative/OOF handling, and the “discard untitled new event on close” rule.
