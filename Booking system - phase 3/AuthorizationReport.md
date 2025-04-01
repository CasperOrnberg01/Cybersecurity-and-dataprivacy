### Authorization Testing Table

| Page / Feature             | Guest | Reserver | Administrator |
|----------------------------|:-----:|:--------:|:--------------:|
| / (index)                  |  ✅     |    ✅      |      ✅         |
| /resources                 |   ✅ only see resources form empty    |     ✅ only see resources form empty    |       ✅  only see resources form empty       |
| /resources?id=XXX          |   ❌ can only see empty form, not the particular resource with entered ID   |  ✅⚠️ Reservers can modify reservations made by others, critical.       |     ✅´can modify  reserver made reservations, maybe acceptable as admin?           |
| /reservation               |   ❌"Unauthorized"    |     ✅     |       ✅         |
| /reservation?id=XXX        |   ❌ "Unauthorized"    |     ✅     |                |
| /logout                    |   ✅    |    ✅      |       ✅         |
| /login                     |   ✅    |     ✅     |     ✅           |
| /register                  |    ✅   |     ✅     |       ✅         |
| /api/resources             |  ❌cant see resources, just empty form     |    ✅  can see resource information json format    |        ✅ can see resource information json format       |
| /api/resources/XXX         |   ❌ cannot see resources "Unauthorized"    |    ✅ can see resources/1 and so on     |        ✅   can see resources/1 and so on      |
| /api/reservations/XXX      |   ✅⚠️ Guests can see reservations just like reservers and admins, and none of them shouldnt be able to do so.    |     ✅⚠️ reservers can see others reservations and reserver_tokens at /api/reservations/1, /api/reservations/2 etc...     | ✅⚠️admin can also see others reservations and reserver_tokens               |
| /api/users                 |  ✅⚠️ accessible as guest, which is critical vulnerability. Email/"username" + role + user_token is revealed to guests.     |    ✅⚠️shouldn't be accessible      |     ✅⚠️           |
| /api/session               |  ❌     |    ✅ can see own session     |       ✅  can see own session       |


Symbols used:
✅ Pass (a note can be added)
❌ Fail (a note can be added)
⚠️ Attention (a note can be added)

