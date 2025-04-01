### Authorization Testing Table

| Page / Feature           | Guest | Reserver | Administrator |
|--------------------------|:-----:|:--------:|:--------------:|
| / (index)                |  ✅   |   ✅     |      ✅        |
| └─ View resource form    |  ❌   |   ✅     | ✅ *Note added |
| └─ Create new resource   | ❌ *1 | ❌ *2    | ✅ *3          |
| /login                   |  ✅   |   ✅     |      ✅        |
| /register                |  ✅   |   ✅     |      ✅        |
| /profile                 |  ❌   |   ✅     |      ✅        |
| /admin/users             |  ❌   |   ❌     |      ✅        |
| /admin/settings          |  ❌   |   ❌     |      ✅        |

Symbols used:
✅ Pass (a note can be added)
❌ Fail (a note can be added)
⚠️ Attention (a note can be added)