### Authorization Testing Table

| Page / Feature             | Function | Guest | Reserver | Administrator |
|----------------------------|----------------------------------------|:-----:|:--------:|:--------------:|
| / (index)                  |x | ✅     |    ✅      |      ✅         |
| /resources                 | x |  ✅ only see resources form empty    |     ✅ only see resources form empty    |       ✅  only see resources form empty       |
| /resources?id=XXX          |x |  ❌ can only see empty form, not the particular resource with entered ID   |  ✅⚠️ Reservers can modify reservations made by others, critical.       |     ✅´can modify  reserver made reservations, maybe acceptable as admin?           |
| /reservation               | x | ❌"Unauthorized"    |     ✅     |       ✅         |
| /reservation?id=XXX        | x |  ❌ "Unauthorized"    |     ✅     |                |
| /logout                    | x | ✅    |    ✅      |       ✅         |
| /login                     | x | ✅    |     ✅     |     ✅           |
| /register                  | x |  ✅   |     ✅     |       ✅         |
| /api/resources             | x | ❌cant see resources, just empty form     |    ✅  can see resource information json format    |        ✅ can see resource information json format       |
| /api/resources/XXX         | x | ❌ cannot see resources "Unauthorized"    |    ✅ can see resources/1 and so on     |        ✅   can see resources/1 and so on      |
| /api/reservations/XXX      | x | ✅⚠️ Guests can see reservations just like reservers and admins, and none of them shouldnt be able to do so. Discoverable via ID fuzzing, Guests and Reservers can access any reservation   |     ✅⚠️ reservers can see others reservations and reserver_tokens at /api/reservations/1, /api/reservations/2 etc...     | ✅⚠️admin can also see others reservations and reserver_tokens               |
| /api/users                 | x | ✅⚠️ accessible as guest, which is critical vulnerability. Email/"username" + role + user_token is revealed to guests.     |    ✅⚠️shouldn't be accessible      |     ✅⚠️           |
| /api/session               | x | ❌     |    ✅ can see own session     |       ✅  can see own session       |


Symbols used:
✅ Pass (a note can be added)
❌ Fail (a note can be added)
⚠️ Attention (a note can be added)

#⚠Critical notes:
-guests, reservers and admins can all access /api/reservations/XXX.
-Everyone can access  /api/users.

## ZAP REPORT:
[View full ZAP Scan Report](./ZapReport_phase3.md)
Zap found other types of issues, related to: Input validation, info disclosure and frontend hints.

## Wfuzz Summary

- `/api/reservations/1`, `/2`, `/7` returned `200 OK`, reservation data is discoverable with numeric fuzzing
- Confirms a **horizontal privilege escalation** + **insecure direct object reference**
- `/api/users` was found again and responds with user info as guest, confirming discovered data leak in table
- No new hidden pages discovered

##Final step
Also in addition to the table:
-Reservers can book resources if they are > 15 years old.
-Booking system displays booked resources without login, however vulnerabilities were discovered in the table.
-Delete option seems to be missing, or not yet implemented.
