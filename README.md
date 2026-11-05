# IELTS ZONE Student Enrolment System - High-fidelity prototype

This is the high-fidelity prototype for **Systems Analysis and Design (6BUIS026C), Coursework 2**, Westminster International University in Tashkent.

It is a working prototype of an Enrolment System for IELTS ZONE, the case I analysed in Coursework 1. It helps the staff of a branch to register students, check their level, put them in groups, take payments and follow up with students.

> This is a prototype. All names, phone numbers and payments in it are made-up demo data.

## How to run

1. Download `index.html` (or clone this repository).
2. Open `index.html` in Chrome or Edge by double-clicking it.

No installation, no server and no internet connection are needed. The program is one file with HTML, CSS and JavaScript.

Data is saved in your browser (localStorage). To go back to the start data, click **Reset demo data** at the top right.

## Roles

Use the **Role** drop-down at the top to see the system as different staff members. Each role sees different menus.

| Role | Can do |
|---|---|
| Administrator | Register students, placement test, assign groups, activate and archive students, mark absences |
| Cashier | Record payments, reverse a payment, send receipts and payment reminders |
| Coordinator | See the daily task list, the monthly report and the activity log |
| Branch Manager | Same as Coordinator, plus approve or reject refund requests |

## Main functions

- **Today:** KPI cards and a daily task list (placement tests to do, absent students to call, overdue payments, students ready for activation).
- **Register student:** contact channel, course, phone, Telegram, backup contact and parent phone.
- **Placement test:** written and speaking scores, level is suggested automatically.
- **Assign to group:** shows seats left, blocks full groups and schedule conflicts, waiting list.
- **Payments:** cash, card, Click and Payme, partial payments, receipt, reversal with a reason.
- **Archive student:** reason is required, optional refund request.
- **Monthly report:** new students, active at start and now, archived by reason, income by method.
- **Activity log:** every important action with time and role.

## Business rules in the program

These rules come from the use cases in Coursework 1.

- A student without Telegram needs SMS or call as a backup contact.
- A student under 18 needs a parent phone. An adult can skip it with a reason.
- A phone number must look like `+998901234567`. A duplicate phone or Telegram account asks if it is the same family.
- If the staff changes the suggested level, or the score is near a level border, a comment is required.
- A full group cannot be chosen. A group at the same time as the student's mock test booking is blocked.
- A payment is blocked if the student has no group yet.
- Click and Payme payments go through a simulated gateway check. Tick "Simulate gateway failure" to see the error path.
- An amount bigger than the balance asks if it is an advance payment.
- A payment reversal needs a reason.
- A payment that is late but inside the 3-day grace period is not marked as overdue. After that a reminder can be sent (Telegram first, SMS or call if there is no Telegram).
- A refund request must be approved by the Branch Manager.

## Quick demo (about 1 minute)

1. As **Administrator**, open **Register student** and save a new student (use a phone like `+998901112233`).
2. Enter written score `31` and speaking score `6`, then save the placement result.
3. Assign a group. Try the full group `Tue-Thu-Sat 14:00` for another student to see the message.
4. Switch the role to **Cashier**, open **Payments**, choose the student and record `600000` by **Click**.
5. Switch to **Coordinator** and open **Monthly report**.

## Demo data

- 1001 Aziz Karimov: payment overdue after the grace period (use Cashier, Today, "Send reminder").
- 1003 Jasur Tursunov: late, but still inside the grace period. No Telegram, so SMS is used.
- 1004 Dilnoza Aliyeva: waiting for the placement test.
- 1005 Bekzod Yusupov: waiting for a group. He has a mock test on `Mon-Wed-Fri 18:00`, so that group gives a schedule conflict.
- A group is already full, to test the full-group message.
- A refund request is waiting for the Branch Manager.

## Limits

- It does not connect to the real Click, Payme, Telegram or SMS services. These calls are simulated with messages.
- Data is saved only in one browser, there is no real database and no real login.
- The schedule check compares a group time only with a mock test booking.
- It is not tested with large data (more than 1,000 students per branch).
- It is not connected to the existing LMS or to the "stars and box" system.

## Built with

- HTML, CSS and plain JavaScript, no libraries.
- Built with the help of an AI assistant (Claude), as allowed in the coursework brief. I checked it against my use cases and the low-fidelity prototype.



## Author

Student ID: 00019125
