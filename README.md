## Getting Started, Licensing & Access

**What is Veridate?**
Veridate is a cloud-based (Microsoft Azure) quality inspection and compliance tracking system for food production, replacing paper-based QA checks. It has a web portal (for setup, admin, and reporting) and a native mobile app for iOS and Android (for running checks on the factory floor), which look and work identically on both platforms.

**How do I get set up as a new client?**
A nominated person becomes your internal admin. Veridate sets your organisation up as a client, and that nominated person receives an invite email to create a password. From there they log in at the portal login page.

**What's the difference between an "app user" and a "portal user"?**
- **App users** use the mobile app on the factory floor to run checks. App user licences are limited (often starts around 10, adjustable based on your needs).
- **Portal users** access the web interface for admin, setup, and reporting. Portal user accounts are unlimited.
- The same email address can be both an app user and a portal user — it's a single underlying user account with access to both, rather than two separate accounts. You'd still send an app-user invite and a portal-user invite to get each type of access set up (PIN for the app, password for the portal), but they land on the same account.

**How do app users log in, versus portal users?**
- **App users** get an invite email, follow the link, and set a 4-digit PIN. After that, they log into the app with their email address and PIN.
- **Portal users** get an invite email and set a full password (with confirmation). They log into the portal with email and password — the login page also has a "Forgot password?" link for resets.

**What can a portal user do — is access all-or-nothing?**
No — portal access is granular, built from individual roles you assign when inviting someone:
- **Super Admin** — full access.
- **Product management** — add, edit, delete products and production lines.
- **Check schemes management** — add, edit, delete check schemes and check scheme templates.
- **View reports** — access and view the report page, and apply filters.
- **Download reports** — can export reports.
- **User management** — add, edit, and delete users.
- **Alerts** — can respond to alerts with corrective actions.

The account owner (the first Super Admin on the account) is a special case — that user's access can't be edited or deleted by anyone.

**Can operators share a single phone or tablet?**
Yes. A phone or tablet doesn't need to belong to one person — several operators can share the same device on a line, or even across multiple lines. Each operator still logs in individually with their own PIN before doing anything; the app times sessions out rather than staying logged in as one generic user, so every check is always tied to the specific person who performed it.

**What if an operator doesn't have their own email address?**
You can still get them a PIN. Email is used for sending the initial invite (which can go via a distribution group or shared alias rather than a personal inbox), but each operator ends up with their own individual 4-digit PIN, which is what ties every check they perform back to them personally. Using a single generic/shared login for multiple people isn't supported — the system is built around individual accountability for every check.

**Is there a limit on how many products, images, or checks I can have?**
No practical limit on any of these — products, images per product, or checks within a check scheme. App user seats are managed on a "Seats used / Seats available" basis (e.g. 2/10) via a "Manage seats" option, and can be increased if you need more. Portal users are unlimited — the "Add portal user" screen currently shows text implying it allocates a spare seat, but that's a known copy error slated to be corrected; portal users don't actually draw from a seat pool.

**What devices and OS versions are supported?**
The app runs natively on both iOS and Android, on phones and tablets, with the same look and functionality across platforms. Performance is optimised for the current version of iOS/Android plus the previous two versions — older devices aren't blocked, but performance is tuned around that recent range.

## Data Security, Privacy & Retention

**Who can see our data?**
Only your own portal users can view and access your organisation's data — it's held in your own secured area of the Microsoft Azure environment. Neither InspectionWorx staff (Veridate's makers) nor any retailer partner (e.g. M&S) has visibility into your records; InspectionWorx only steps in for backend technical support if something goes wrong with the underlying infrastructure.

**How long is data retained, and can it be archived?**
This is configurable to your own retention requirements (e.g. common industry benchmarks like 3 years for BRC-related records were discussed, though your specific requirement may differ). An archiving feature is available so older records can be moved out of the live, actively-used dataset into secure archive storage rather than being deleted.

---

## Products

**What does the "Active" / "Inactive" status on a product mean?**
A product must be made **Active** before it can be used in the app to start a production run. You can create and fully configure a product — details, fields, images, date rules, check schemes — while it's still Inactive, then activate it once everything's confirmed. If required information is missing, you'll see a tooltip explaining what's needed and won't be able to activate it.

**What are the two ways to create a new product?**
- **From blank** — starts with just the product name and Product ID; every other field is created by you from scratch.
- **Duplicate an existing product** — copies over all field names (and optionally the check schemes, via a checkbox at duplication time) from the source product. This is the faster route once you have at least one product set up, and it's worth creating a few "template" blank products per category so duplicating gives you a ready-made starting point.

**Why does the Product ID matter?**
If you use other systems (ERP, warehousing, planning), using the same Product ID in Veridate makes it easier to match up exported production run reports with records in those other systems.

**What are the custom fields on a product for?**
They store any product-specific information you want to reference later — e.g. a 1D retail barcode, 2D artwork barcode, printed date code, pack presentation image, etc. Importantly, a field must exist on the product before it can be referenced in that product's check schemes — so it's worth adding a field for anything you'll want to check. When you duplicate a product, all its field names (and any images, if named/used consistently) come across for free.

**Can I add images to a product?**
Yes — images can be uploaded and then referenced within check schemes (e.g. showing what a correctly sealed pack should look like), which is useful for guiding staff running checks in the app.

**How does the use-by / best-before date get calculated?**
Date configuration on a product includes:
- The **date format** to print.
- An **offset** (a number of days/weeks) from the production start time.
- **Rounding rules** — e.g. round up/down to the end of a month, or up/down to a specific day of the week (useful for products where retailers destock on set days).
- **Concessions** — temporary date-calculation exceptions valid between a start and end date; can be set to single-use so they auto-deactivate after one production run.
- **Date avoidance** — rules to avoid coding specific dates (e.g. Christmas Day), with a chosen effect on shelf life when that date would otherwise apply.

**What if my product is made up of several other products, each with their own date code (a "component" product)?**
There's a separate mode for this. Instead of an offset/rounding calculation, you flag the product as a component product and, during the production run, scan each individual component's own date code until all required components have been scanned. The system then calculates the final date automatically based on the shortest remaining life among the components you scanned.

**Is Veridate only for M&S products, or can I use it for other customers too?**
You can use it for any of your products, not just ones going to a particular retailer — there's no restriction preventing you running non-M&S products through the same system. This is intentional: having operators use one consistent digital process for all products, rather than switching between digital checks for one customer and paper for others, avoids confusion on the line.

**Where does a corrective action alert get sent?**
Each product has a field for the alert email address used when a check fails and that check is configured to require a corrective action. You can list multiple addresses, though a distribution list/alias is usually easier to maintain if the responsible people change over time.

**What are the tabs within a product?**
Once you open a product, there are three tabs:
- **Dashboard** — shows which production line(s) the product currently has runs active on (or "None"), and a count of alerts requiring action for that product.
- **Product Details** — the Active toggle, general info (name, ID, custom fields), product/packaging images, date configuration, concessions, date avoidance, and email alerts.
- **Check Schemes** — the product's assigned Start, Mid, and End check schemes.

**How do product fields work — is it just a name and a value?**
Yes — each custom field is a simple Field Name / Field Value pair (e.g. "1D Retail Barcode" → "29249862", "Min Temp" → "5"). You add more via "+ Add new fields," and each has its own delete icon.

**How do product images work?**
Each image is uploaded with a name (e.g. "Front Of Pack," "Back Of Pack," "Pack Presentation") so it can be referenced consistently in check schemes. Each image can be individually replaced or deleted, and there's an "+ Add image" tile for adding more.

---

## Check Schemes & Check Types

**What is a "Check Scheme"?**
A check scheme is a named set of one or more individual checks, applied at a specific stage of a production run (Start, Mid, or End). Each individual check has a title, a question/prompt, an expected response, and — once run — an actual response.

**How many check schemes does a product need?**
Every product requires exactly **one** Start-of-run check scheme and exactly **one** End-of-run check scheme. It can also have **zero, one, or many** Mid-run check schemes — these are entirely optional.

**How do I build a check scheme?**
From within a product, for each stage (Start/Mid/End) you can either **add from an existing check scheme template** (a predefined, reusable structure) or **build a new check scheme directly on the product**. If you're duplicating a product, there's a checkbox to bring across its check schemes automatically. Checks within a scheme can be reordered at any time using the arrows next to each entry, and each check can be edited later via its Edit button — nothing is locked in once saved.

**When is a check scheme assigned to a product?**
When the product itself is created — that's when its Start, Mid, and End check schemes get assigned from the available templates (or built fresh).

**Can I change a product's check schemes after it's been created?**
Yes, they can be edited at any point. Note that once a product's check scheme has been edited, it becomes independent of the template it was originally assigned from — if you later update the source template, that product's check scheme won't automatically pick up the change. Each product's check scheme is its own copy from the point of assignment onward.

**What types of checks are available?**
When adding a check to a scheme, the check "Type" dropdown offers ten options:
- **Barcode scan** — scans and matches against a value, typically linked to a product field.
- **Data matrix scan** — scans a 2D data matrix code, distinct from a standard barcode scan.
- **OCR text check** — reads printed text (e.g. a date code) via the camera; can optionally allow manual typing if print quality is expected to be poor.
- **OCR time check** — reads a printed real-time clock value and checks it's within a set +/- window of minutes, useful for confirming a sample pack is current rather than saved from earlier in the run.
- **Yes/No question** — a straightforward yes/no with an expected answer you set.
- **Yes/No question with image** — the same, but with a reference image shown alongside (e.g. "does the pack look like this?").
- **Multiple choice** — offers several options with one marked correct.
- **Number entry** — enter a numeric value, checked against a range you set — either a fixed min/max you type in directly, or one sourced from product fields (e.g. Min Temp / Max Temp fields). If there's no real range, you put the same number in both boxes.
- **Text entry** — a manually typed value, as an alternative to OCR.
- **Photo capture** — simply captures an image with no pass/fail logic, for keeping a permanent visual record.

**What does "corrective action" mean on a check?**
It's a toggle on an individual check when you create it. Turning it on means that if the check fails (actual response doesn't match expected), a supervisor will be required to document what corrective action was taken, and that failure plus the corrective action will show up in the product's alerts section — along with triggering the alert email to the product's corrective-action address. Not every check needs this (e.g. data-capture-only checks like "how many people are on the line" typically don't).

**Can barcode/OCR checks handle variable data like QR codes with changing pallet numbers?**
Not yet as a fixed feature at time of the walkthroughs — full free-text matching only. Wildcard/partial matching (matching a fixed portion of a code while allowing the rest to vary) was in active development and not yet available to demo — worth confirming current availability before publishing this answer live.

**What happens if the OCR can't read a poorly printed date code?**
You can either reject the check outright (forcing a re-print/re-check) or allow the operator to manually type in the date code they can read from the pack instead — but whatever's typed in still has to match the calculated expected date for the check to pass, so it isn't a way to bypass the check.

**Why would I use an OCR time check rather than just trusting the printed time?**
It's specifically there to prevent falsifying records — for example, using a sample pack from earlier in the run for every check rather than a genuinely current one. The check reads the real-time clock printed on the pack via OCR and confirms it's within your configured tolerance of the actual current time, so you know the sample being checked is current, not reused.

**Can I set a grace period for interval-based Mid-run checks, or do they have to be exact?**
Yes — when you set a Mid-run check to run on an interval (e.g. every 15 minutes), you can also configure a tolerance/grace window beyond the target time (e.g. an extra 5 minutes) before the check is considered overdue.

**What's the difference between Mid-run checks and Start/End checks in how they're triggered?**
- **Start** and **End** checks are triggered manually by the operator, and are compulsory gatekeepers — Start must be completed before any other check scheme can run, and End must be completed to close the run.
- **Mid-run checks** are optional and can be either **manual** (operator opens the list of available mid-run check schemes in the app and picks one) or run **on a set interval** (a timed schedule configured when the check was created). Mid-run schemes are often grouped by event — e.g. a film/board change, a raw material batch change, or a staff/shift change.

**What does "Time due" mean in a report, and why is it sometimes "N/A"?**
It relates to interval-based (timed) Mid-run checks — the app shows a countdown to when the check is due, and its colour changes once the check becomes overdue. Manual mid-run checks and Start/End checks aren't on a timer, so "Time due" shows N/A for those.

---

## Production Lines

**What is a production line, and why do I need to set them up?**
A production line is simply a named entry in a list so it can be selected in the app when starting a production run. Each line also has its own **start-of-day time** — the point at which the "day" rolls over for date calculation purposes (commonly midnight, but can be set per line, e.g. to match shift changes or CIP schedules).

**How do I add or manage production lines?**
On the Production Lines page, each line is just a name plus a start-of-day time (HH:MM). You can add a new one via "+ Add new production line," delete any line, and there's a "Save changes" button to confirm edits.

---

## Running Checks in the App (Mobile)

**What happens when I start a production run in the app?**
You select the product and the production line to run it on. The Start check scheme for that product must be completed before any other checks (Mid or End) become available.

**What happens if I select the wrong production line or make a mistake mid-run?**
You can either continue and correct the specific check result, or restart the run's checks from the beginning if something more fundamental was wrong (e.g. the wrong packaging was in place for the whole run).

**How do timed Mid-run checks behave in the app?**
If a Mid-run check is interval-based, the app shows a countdown to when it's due; the display changes colour once you're inside the "overdue" window if you haven't run it yet.

---

## Production Runs, Reports & Corrective Actions

**What do the different statuses in the reports list mean?**
There are three: **Completed** (every check in the scheme passed), **Failed** (at least one check that failed had corrective action enabled on it), and **Completed with errors** (at least one check failed, but none of the failed checks had corrective action enabled). In other words, whether a scheme shows as Failed or Completed with errors depends on whether the specific check that failed was configured to require a corrective action, not on how many checks failed.

**How do I see the details behind a check result?**
Click into any row in Product Reports to open the **View report** panel. It shows the product, person, check scheme type and name, date/timing, and a breakdown of each individual check with its question, expected response, actual response, and a Success/Fail indicator. Where a check involved a photo capture, a thumbnail is shown and can be clicked to view the full-size image.

**What does a failed check's corrective action entry actually contain?**
When a check with corrective action enabled fails, the report shows: the expected vs. actual response, a "Corrective action" field confirming one was required, and a timestamped entry recording who logged it and what they wrote (e.g. "Wrong packaging on the line. Staff training planned.").

**Can I add notes to a report after the fact?**
Yes — this is separate from the corrective action entry. Below the corrective action, there's an "Additional notes" field with an "+ Add note" button, so further context can be added later if useful, and it's recorded permanently against that check.

**Can a check result be edited or deleted after it's been submitted, to "fix" a mistake?**
No — the audit log is designed to be tamper-proof: results can't be edited or removed after the fact, and checks can't be backdated or pre-completed ahead of time. This is intentional, since the whole point of moving from paper to digital is producing a record that can't be falsified. You can add notes for extra context, and you can always run further checks (e.g. restart a run), but the original entries stand as recorded.

**What are the alerts shown on the Products page / product card?**
When a check fails, it raises an alert against that product. A status indicator (green when clear) shows whether a product currently has outstanding alerts; failed checks turn this red until the corrective action is acknowledged/addressed.

**How do I filter or search production run reports?**
Use the filter bar at the top of Product Reports — you can filter by Product, Type (Start/Mid/End), Scheme, Status, Production line, Date range, and Person, then click the checkmark to apply or the reset icon to clear filters.

**Can I export the audit log?**
Yes — click **"Export audit log as CSV"** in the top-right of the Product Reports page. The CSV can be opened in Excel or imported into other systems (e.g. to combine with ERP or warehousing data).

---

## Change History

**What does Change History track?**
Every change made in the portal, split across four tabs: **Products**, **Production lines**, **Users**, and **Check Schemes**. Each tab has the same style of filters as Production Runs (by Product/Person/Action and date range) and its own "Export audit log as CSV" button. In short: Production Runs shows what's happened *in the app* (on the factory floor); Change History shows what's happened *in the portal* (admin/config changes). Note: the page itself is titled "System Change" even though the sidebar link says "Change History" — same page.

**What does each Change History tab show?**
- **Products** — field-level changes to a product (e.g. a rounding rule changing from one setting to another, an image being added/edited/replaced/deleted, a product's Active status changing, a field value being edited), each row showing the old and new value.
- **Production lines** — lines added or deleted, with who did it and when.
- **Users** — users added or deleted, plus edits to their type or roles (e.g. a user's access changing from App-only to both App and Portal, or a role like Super Admin being added or removed).
- **Check Schemes** — changes to check schemes and individual checks on a product (e.g. a check's expected response changing, a whole check scheme being added), again showing old vs. new values.

---

## User Management (Portal Pages)

**What does the User Management page look like day to day?**
It has three tabs: **App users**, **Portal users**, and **Access log**. App users shows your seat usage (e.g. "2/10") with a "Manage seats" option, and a simple list of Name / Email / Status per app user (with delete only — no edit, since their access is all-or-nothing). Portal users shows Name / Email, a green checkmark per role they hold (Super Admin, Check schemes management, View reports, Download reports, User management, Alerts), and Status (Pending until they accept the invite, then Active) — each portal user other than the account owner can be edited or deleted.

**What's in the Access log?**
It's a login/logout history for the portal — separate from Change History. Each row shows a Timestamp, Action (Login successful, Login failed, or Logout), Email, Username, and IP address. It's filterable by User, Action, and date range, and has its own "Export access log as CSV" button.

## Help Centre & Support

**What's in the Help Centre?**
Links to external tutorial videos, plus FAQs that grow over time as users ask questions — the intent is that common questions get turned into FAQ entries so everyone benefits. There's also a Contact section for anything not covered there.

---

Copyright InspectionWorx Ltd 2026 Veridate is a registered trademark of InspectionWorx Ltd
