Ahh got it! You want to **split the number and the unit into two separate columns** — like:

| A (Original) | B (Number) | C (Unit) |
|--------------|------------|----------|
| 101.2gb      | 101.2      | gb       |
| 500b         | 500        | b        |
| 965kb        | 965        | kb       |
| 314.2mb      | 314.2      | mb       |

### ✅ Do this in Google Sheets:

Assume your original data is in column **A**, starting at A1.

**In column B** (Number):
```excel
=REGEXEXTRACT(A1, "^[0-9.]+")
```

**In column C** (Unit):
```excel
=REGEXEXTRACT(A1, "[a-zA-Z]+$")
```

This will neatly split the number and the unit into two columns.

Let me know if you'd like to convert those units to a standard form (like all to MB or GB)!
