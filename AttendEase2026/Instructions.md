# Attend Ease 2026 - Copilot App Builder(Frontier) Prompt

## App Name

Attend Ease 2026v2

## Objective

Create an employee attendance tracking app that allows users to check in
and check out daily, with simple tracking and visibility of their
attendance records.

## Authentication & User Context

-   Use Microsoft Entra ID for authentication
-   Automatically identify the logged-in user
-   Map the logged-in user to the Employee (Person or Group field) in the SharePoint List

## Data Source Configuration

-   Use SharePoint List as the backend data store
-   List Name: AttendanceLog
-   No seed data required

### AttendanceLog SharePoint List Columns

1.  Employee (Person or Group, Required, Single selection)
2.  CheckInTime (Date and Time, Required)
3.  CheckOutTime (Date and Time, Optional)
4.  Remarks (Multiple lines of text, Optional)
5.  Created (System-generated Date and Time)
6.  Created By (System-generated Person or Group)

## Core Features & Logic

### Check-In

-   Allow user to check in once per day
-   On check-in:
    -   Set Employee = Logged-in user
    -   Set CheckInTime = Current date & time
    -   Prevent duplicate check-ins for the same day

### Check-Out

-   Allow check-out only if a check-in exists for the day
-   Update the same record:
    -   Set CheckOutTime = Current date & time

### Remarks

-   Allow user to add remarks during check-in or check-out

### Daily Validation

-   Ensure only one attendance record per user per day
-   Handle edge cases:
    -   Missing check-out from previous day
    -   Multiple attempts to check in

## User Experience

-   Show current status:
    -   Not Checked In
    -   Checked In at \[time\]
    -   Checked Out at \[time\]
-   Provide buttons:
    -   Check In\
    -   Check Out\
-   Display recent attendance history (last 7--30 days)
